---
title: 從編輯器延伸模組存取 DTE 物件
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d023359412b423c9c12d7c7d8a37e79571cbc11a
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269081"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>逐步解說：從編輯器延伸模組存取 DTE 物件

在 Vspackage 中，您可以使用 DTE 物件的型別來呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 方法，以取得 DTE 物件。 在 Managed Extensibility Framework （MEF）延伸模組中，您可以匯入 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>，然後使用 <xref:EnvDTE.DTE>的類型來呼叫 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 方法。

## <a name="prerequisites"></a>必要條件：

若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

## <a name="get-the-dte-object"></a>取得 DTE 物件

1. 建立C# VSIX 專案，並將其命名為**DTETest**。 新增**編輯器分類器**專案範本，並將其命名為**DTETest**。

   如需詳細資訊，請參閱[使用編輯器專案範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)功能。

::: moniker range=">=vs-2019"

2. 將下列元件參考加入至專案：

    - VisualStudio 架構
    - VisualStudio：不變的10。0

3. 在*DTETestProvider.cs*檔案中，新增下列 `using` 指示詞：

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. 在 `DTETestProvider` 類別中，匯入 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>。

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. 在 `GetClassifier()` 方法中，將下列程式碼加入 `return` 語句之前：

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. 將下列元件參考加入至專案：

   - EnvDTE
   - VisualStudio 架構

3. 在*DTETestProvider.cs*檔案中，新增下列 `using` 指示詞：

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. 在 `DTETestProvider` 類別中，匯入 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>。

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. 在 `GetClassifier()` 方法中，將下列程式碼加入 `return` 語句之前：

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>請參閱

- [語言服務和編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
- [使用 DTE 啟動 Visual Studio](launch-visual-studio-dte.md)
