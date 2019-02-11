---
title: 工作區和 Visual Studio 中的語言服務 |Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2893ae2bcd70ff317ba799fea6cfd2751c685731
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929774"
---
# <a name="workspaces-and-language-services"></a>工作區和語言服務

語言服務可以提供[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)使用者相同的豐富的語言功能它們是用來使用方案和專案時。 語言服務可能會自行啟動這個 「 鬆散檔案 」 語言服務是限制為語法反白顯示，根據副檔名或開啟的文件的內容。 其他資訊，才能編輯/檢閱原始碼時提供更豐富的體驗。 每個語言服務會有它自己的初始化與此文件的額外內容資料的 API。 這通常被管理專案系統使用，這緊密結合的語言服務，建置系統。

## <a name="initialization"></a>初始化

在 [工作區](workspaces.md)，語言服務會初始化所<xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider>延伸點，只有該語言服務中專門和一無所知建置撰寫。 如此一來，語言服務擁有者可以維護單一開啟資料夾存在於資料夾和檔案 （例如 MSBuild、 makefile 等） 在建置期間執行其編譯器的延伸不限數目的模式。 當建立的檔案內容來源的檔案會在磁碟上變更並重新整理的檔案內容時，語言服務提供者會收到通知的已更新的檔案內容集。 然後，語言服務提供者可以更新其模型。

在編輯器中開啟文件時，Visual Studio 只會考慮語言需要找相符的檔案內容提供者的檔案內容類型的服務提供者。 然後將傳遞檔案內容從相符的提供者至選取的語言服務提供者，透過`ILanguageServiceProvider.InitializeAsync`。 語言服務提供者的功能與檔案的內容資料是語言服務提供者的實作詳細資料，但預期的使用者體驗是更豐富的語言服務，如開啟文件。

## <a name="using-ilanguageserviceprovider"></a>使用 ILanguageServiceProvider

將通知語言服務，以建立的檔案內容`ContextType`符合其中一個`SupportedContextTypes`值的語言伺服器匯出的屬性。

若要支援的語言服務，將需要擴充功能：

- 唯一`Guid`。 這將用於`SupportedContextTypes`屬性的引數和`FileContext`物件。
- 語言檔案內容
  - 提供者 factory
    - `ExportFileContextProviderAttribute` 使用上述的屬性產生的唯一專屬`Guid`中 `SupportedContextTypes`
    - 實作 `IWorkspaceProviderFactory<IFileContextProvider>`
  - 提供者實作 `IFileContextProvider.GetContextsForFileAsync`
    - 建構新`FileContext`與`contextType`作為唯一產生建構函式引數 `Guid`
    - 使用`Context`屬性`FileContext`提供的額外資料 `ILanguageServiceProvider`
- 語言服務
  - 提供者 factory
    - `ExportLanguageServiceProvider` 使用上述的屬性產生的唯一專屬`Guid`中 `SupportedContextTypes`
    - 實作 `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - 提供者
    - 實作 `ILanguageServiceProvider`
    - 使用`ILanguageServiceProvider.InitializeAsync`開啟檔案時，啟用提供的引數的語言服務
    - 使用`ILanguageServiceProvider.UninitializeAsync`關閉檔案時，停用提供的引數的語言服務

>[!WARNING]
>`ILanguageServiceProvider`主執行緒上的工作區可能會叫用方法。 請考慮將排程工作在不同的執行緒，以避免產生 UI 延遲。

## <a name="language-server-protocol"></a>語言伺服器通訊協定

`Microsoft.VisualStudio.Workspace.*`開發介面不會啟用您的語言服務中開啟資料夾的唯一方式。 另一個選項是使用語言伺服器。 如需詳細資訊，了解[語言伺服器通訊協定](language-server-protocol.md)。

## <a name="related-interfaces"></a>相關的介面

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> 比對的檔案類型的檔案是開啟或關閉進行編輯時，會叫用。

## <a name="next-steps"></a>後續步驟

* [工作區建置](workspace-build.md)-開啟資料夾支援建置系統，例如 MSBuild 和 makefile。