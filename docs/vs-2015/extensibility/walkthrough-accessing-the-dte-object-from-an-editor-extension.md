---
title: 逐步解說：從編輯器延伸模組存取 DTE 物件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b14b59465b94ddd0a09748f0e309166bf3d4114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148882"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>逐步解說：從編輯器延伸模組存取 DTE 物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Vspackage 中，您可以 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 使用 dte 物件的型別來呼叫方法，以取得 dte 物件。 在 Managed Extensibility Framework (MEF) 擴充功能的情況下，您可以匯入， <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 然後 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 使用的類型來呼叫方法 <xref:EnvDTE.DTE> 。  
  
## <a name="prerequisites"></a>Prerequisites  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="getting-the-dte-object"></a>取得 DTE 物件  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>從 ServiceProvider 取得 DTE 物件  
  
1. 建立名為的 c # VSIX 專案 `DTETest` 。 加入編輯器分類專案範本並將其命名 `DTETest` 。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
2. 將下列元件參考新增至專案：  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - VisualStudio，不變的10。0  
  
3. 移至 DTETest.cs 檔案，並新增下列指示詞 `using` ：  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4. 在 `GetDTEProvider` 類別中，匯入 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 。  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5. 在 `GetClassifier()` 方法中，加入下列程式碼。  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6. 如果您必須使用 <xref:EnvDTE80.DTE2> 介面，您可以將 DTE 物件轉換為它。  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
