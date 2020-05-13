---
title: 從編輯器延伸器存取 DTE 物件
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e37bdb21b7c8132f0dfb166d19e03d36e838245d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697655"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>演練:從編輯器延伸器存取 DTE 物件

在 VSPackages 中,可以通過使用<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>DTE 物件的類型調用 方法來獲取 DTE 物件。 在託管擴充性框架 (MEF) 擴充中,<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>可以導入<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A><xref:EnvDTE.DTE>然後使用類型呼叫方法。

## <a name="prerequisites"></a>Prerequisites

若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 有關詳細資訊,請參閱[可視化工作室 SDK](../extensibility/visual-studio-sdk.md)。

## <a name="get-the-dte-object"></a>取得 DTE 物件

1. 建立 C# VSIX 專案並將使用**DTETest**。 新增**編輯器類別器**專案樣本並將使用**DTETest**。

   關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

::: moniker range=">=vs-2019"

2. 新增以下程式集參考:

    - 微軟.VisualStudio.shell.Framework.Framework
    - 微軟.VisualStudio.shell.不可改變.10.0

3. 在*DTETestProvider.cs*檔案中,`using`新增以下 指令:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. 在`DTETestProvider`類別中,匯<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>入 。

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. 在`GetClassifier()`方法中,在`return`敘述之前加入以下代碼:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. 新增以下程式集參考:

   - EnvDTE
   - 微軟.VisualStudio.shell.Framework.Framework

3. 在*DTETestProvider.cs*檔案中,`using`新增以下 指令:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. 在`DTETestProvider`類別中,匯<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>入 。

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. 在`GetClassifier()`方法中,在`return`敘述之前加入以下代碼:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>另請參閱

- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
- [使用 DTE 啟動 Visual Studio](launch-visual-studio-dte.md)
