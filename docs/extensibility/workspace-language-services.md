---
title: Visual Studio 中的工作區和語言服務 |Microsoft Docs
description: 瞭解語言服務如何提供開啟資料夾使用者與使用方案和專案時所使用的相同豐富語言功能。
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 815cfb9e17fed38b519719010acd997f7fdc5242
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877035"
---
# <a name="workspaces-and-language-services"></a>工作區和語言服務

語言服務可以提供 [開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 使用者與使用方案和專案時所使用的相同豐富語言功能。 語言服務可能會根據副檔名或已開啟檔的內容自行啟用，不過這個「鬆散式檔案」語言服務僅限於語法醒目提示。 需要額外的資訊，才能在編輯/查看原始程式碼時提供更豐富的體驗。 每個語言服務都有自己的 API，可使用此檔的額外內容資料進行初始化。 這通常是由專案系統所管理，它會與語言服務和組建系統緊密地結合。

## <a name="initialization"></a>初始化

在 [工作區](workspaces.md)中，語言服務是由 <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> 僅專門在該語言服務中的擴充點初始化，並不知道任何組建撰寫。 如此一來，不論在組建 (（例如 MSBuild、makefile 等 ) ）中有多少模式存在，語言服務擁有者都可以維護單一的開啟資料夾擴充功能。 當檔案內容建立所在的檔案在磁片上變更，而檔案內容已重新整理時，語言服務提供者就會收到一組更新過的檔案內容通知。 然後，語言服務提供者可以更新其模型。

在編輯器中開啟檔時，Visual Studio 只會考慮需要可找到相符檔案內容提供者之檔案內容類型的語言服務提供者。 然後，它會將檔案內容 (s) 從相符的提供者 (s) 傳遞給選取的語言服務提供者 `ILanguageServiceProvider.InitializeAsync` 。 語言服務提供者如何使用該檔案內容資料，是語言服務提供者的執行詳細資料，但預期的使用者體驗是該開啟檔的更豐富語言服務。

## <a name="using-ilanguageserviceprovider"></a>使用 ILanguageServiceProvider

使用與 `ContextType` `SupportedContextTypes` 語言伺服器匯出屬性的其中一個值相符的來建立檔案內容時，將會通知語言服務。

為了支援語言服務，延伸模組將需要：

- 唯一的 `Guid` 。 這將用於 `SupportedContextTypes` 屬性引數和 `FileContext` 物件中。
- 語言檔案內容
  - 提供者 factory
    - `ExportFileContextProviderAttribute`具有上述唯一產生的屬性 `Guid``SupportedContextTypes`
    - 實作 `IWorkspaceProviderFactory<IFileContextProvider>`
  - 的提供者實作為 `IFileContextProvider.GetContextsForFileAsync`
    - 使用函式 `FileContext` `contextType` 引數作為唯一產生的來建立新的 `Guid`
    - 使用的 `Context` 屬性，將 `FileContext` 其他資料提供給 `ILanguageServiceProvider`
- 語言服務
  - 提供者 factory
    - `ExportLanguageServiceProvider`具有上述唯一產生的屬性 `Guid``SupportedContextTypes`
    - 實作 `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - 提供者
    - 實作 `ILanguageServiceProvider`
    - 在檔案 `ILanguageServiceProvider.InitializeAsync` 開啟時，用來為提供的引數啟用語言服務
    - 在檔案 `ILanguageServiceProvider.UninitializeAsync` 關閉時，用來停用所提供引數的語言服務

>[!WARNING]
>`ILanguageServiceProvider`主要執行緒上的工作區可能會叫用方法。 請考慮在不同的執行緒上排程工作，以避免 UI 延遲的引入。

## <a name="language-server-protocol"></a>語言伺服器通訊協定

`Microsoft.VisualStudio.Workspace.*`Api 不是在開啟資料夾中啟用語言服務的唯一方法。 另一個選項是使用語言伺服器。 如需詳細資訊，請參閱 [語言伺服器通訊協定](language-server-protocol.md)。

## <a name="related-interfaces"></a>相關介面

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> 當已開啟或關閉相符檔案類型的檔案以進行編輯時，會叫用。

## <a name="next-steps"></a>後續步驟

* [工作區組建](workspace-build.md) -開啟資料夾支援 MSBuild 和 makefile 等組建系統。