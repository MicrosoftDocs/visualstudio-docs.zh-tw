---
title: 工作區和 Visual Studio 中的語言服務 |Microsoft 文件
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8631ffea-83c8-4fd4-a01e-c59772e89c84
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 59cf2936311bb94c2db1ada6a7a3d5ccf994f027
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="workspaces-and-language-services"></a>工作區和語言服務

語言服務可以提供[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)使用者相同的豐富的語言功能它們是用來使用方案和專案。 語言服務可能會自行啟動雖然這項 「 鬆散檔案 」 語言服務僅限於語法反白顯示，根據副檔名或開啟的文件的內容。 編輯/檢閱原始碼時提供更豐富的經驗被需要其他資訊。 每個語言服務有它自己 API 進行初始化這項額外內容資料的文件。 這通常被受管理專案系統，語言服務和建置系統緊密結合。

## <a name="initialization"></a>初始化

在[工作區](workspaces.md)，語言服務由初始化<xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider>延伸點，該語言服務只能在特製化，而且知道組建撰寫的任何內容。 如此一來，語言服務擁有者可以維護單一開啟資料夾存在於資料夾和檔案 （例如 MSBuild、 makefile 等），在建置期間執行其編譯器的擴充功能，不論多少的模式。 當從中建立的檔案內容的檔案會在磁碟上變更並重新整理的檔案內容時，更新的檔案內容集語言服務提供者會收到通知。 語言服務提供者則可以更新其模型。

在編輯器中開啟文件時，Visual Studio 只會考慮語言需要可以找到相符的檔案內容提供者檔案內容類型的服務提供者。 接著，將檔案內容比對的提供者從選取的語言服務提供者透過`ILangaugeServiceProvider.InitializeAsync`。 語言服務提供者的用途與檔案內容資料是語言服務提供者實作細節，但預期的使用者經驗會更豐富的語言服務的開啟文件。

## <a name="using-ilanguageserviceprovider"></a>使用 ILanguageServiceProvider

建立的檔案內容時，將會通知語言服務`ContextType`符合其中一個`SupportedContextTypes`值語言伺服器匯出的屬性。

若要支援語言服務，將需要擴充功能：

- 唯一`Guid`。 這會用於`SupportedContextTypes`屬性引數和`FileContext`物件。
- 語言檔案內容
  - 提供者處理站
    - `ExportFileContextProviderAttribute` 具有上述屬性唯一產生`Guid`中 `SupportedContextTypes`
    - 實作 `IWorkspaceProviderFactory<IFileContextProvider>`
  - 提供者實作 `IFileContextProvider.GetContextsForFileAsync`
    - 建構新`FileContext`與`contextType`做為唯一產生的建構函式引數 `Guid`
    - 使用`Context`屬性`FileContext`來提供深度的額外資料 `ILanguageServiceProvider`
- 語言服務
  - 提供者處理站
    - `ExportLanguageServiceProvider` 具有上述屬性唯一產生`Guid`中 `SupportedContextTypes`
    - 實作 `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - 提供者
    - 實作 `ILanguageServiceProvider`
    - 使用`ILanguageServiceProvider.InitializeAsync`開啟檔案時啟用提供的引數的語言服務
    - 使用`ILanguageServiceProvider.UninitializeAsync`檔案關閉時，停用提供的引數的語言服務

>[!WARNING]
>`ILanguageServiceProvider`主執行緒上的工作區可能會叫用的方法。 請考慮將排程工作在不同的執行緒，若要避免引進 UI 延遲。

## <a name="language-server-protocol"></a>語言伺服器通訊協定

`Microsoft.VisualStudio.Workspace.*`應用程式開發介面不允許您開啟的資料夾中的語言服務的唯一方式。 另一個選項是使用語言伺服器。 如需詳細資訊，請閱讀有關[語言伺服器通訊協定](language-server-protocol.md)。

## <a name="related-interfaces"></a>相關的介面

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> 開啟或關閉編輯對應的檔案類型的檔案時，會叫用。

## <a name="next-steps"></a>後續步驟

* [工作區組建](workspace-build.md)-開啟資料夾支援建置 MSBuild 等 makefile 的系統。 