---
title: 從編輯器擴充功能存取 DTE 物件
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3e21ea3d05350a59d62fc9da9e0387f072ec16
ms.sourcegitcommit: 62f42113ae4dae1ddfff1c4e02445acc09913445
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64878205"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>逐步解說：從編輯器擴充功能存取 DTE 物件

在 Vspackage 中，您可以取得 DTE 物件呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>DTE 物件的型別方法。 在 Managed Extensibility Framework (MEF) 擴充功能，您可以匯入<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>，然後呼叫<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>具有一種方法<xref:EnvDTE.DTE>。

## <a name="prerequisites"></a>必要條件

若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。

## <a name="get-the-dte-object"></a>取得 DTE 物件

1. 建立C#VSIX 專案，並命名**DTETest**。 新增**編輯器分類**項目範本並將它命名**DTETest**。

   如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

::: moniker range=">=vs-2019"

2. 新增下列組件參考加入專案：

    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. 在  *DTETestProvider.cs*檔案中，新增下列`using`指示詞：

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. 在 `DTETestProvider`類別中，匯入<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>。

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. 在 `GetClassifier()`方法中，新增下列程式碼，再`return`陳述式：

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. 新增下列組件參考加入專案：

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. 在  *DTETestProvider.cs*檔案中，新增下列`using`指示詞：

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. 在 `DTETestProvider`類別中，匯入<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>。

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. 在 `GetClassifier()`方法中，新增下列程式碼，再`return`陳述式：

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>另請參閱

- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
- [啟動 Visual Studio 中使用 DTE](launch-visual-studio-dte.md)