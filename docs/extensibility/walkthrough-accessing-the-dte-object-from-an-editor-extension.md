---
title: 'Walkthrough: Accessing the DTE Object from an Editor Extension | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: b8a44b149fe8adfcbcb7ef2d66e8b95f23378bdd
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Walkthrough: Accessing the DTE Object from an Editor Extension
In VSPackages, you can get the DTE object by calling the <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> method with the type of the DTE object. In Managed Extensibility Framework (MEF) extensions, you can import <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> and then call the <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> method with a type of <xref:EnvDTE.DTE>.  
  
## <a name="prerequisites"></a>Prerequisites  
 To follow this walkthrough, you must install the Visual Studio SDK. For more information, see [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Getting the DTE Object  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>To get the DTE object from the ServiceProvider  
  
1.  Create a C# VSIX project named `DTETest`. Add an Editor Classifier item template and name it `DTETest`. For more information, see [Creating an Extension with an Editor Item Template](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Add the following assembly references to the project:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Go to the DTETest.cs file, and add the following `using` directives:  
  
    ```cs  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  In the `GetDTEProvider` class, import a <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```cs  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  In the `GetClassifier()` method, add the following code.  
  
    ```cs  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  If you have to use the <xref:EnvDTE80.DTE2> interface, you can cast the DTE object to it.  
  
## <a name="see-also"></a>See Also  
 [Language Service and Editor Extension Points](../extensibility/language-service-and-editor-extension-points.md)
