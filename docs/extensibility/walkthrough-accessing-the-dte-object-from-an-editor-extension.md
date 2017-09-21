---
title: "逐步解說︰ 從編輯器延伸模組來存取 DTE 物件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，新-取得 DTE 物件"
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 逐步解說︰ 從編輯器延伸模組來存取 DTE 物件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Vspackage 中，您可以取得 DTE 物件呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> DTE 物件的型別方法。 在 Managed Extensibility Framework \(MEF\) 擴充功能，您可以匯入 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> ，然後呼叫 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 方法的類型與 <xref:EnvDTE.DTE>。  
  
## 必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 取得 DTE 物件  
  
#### 若要從 ServiceProvider 取得 DTE 物件  
  
1.  建立 C\# VSIX 專案，名為 `DTETest`。 加入編輯器分類的項目範本，並將它命名 `DTETest`。 如需詳細資訊，請參閱[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
2.  下列組件參考加入至專案︰  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  移至 DTETest.cs 檔案，並新增下列 `using` 指示詞︰  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  在 `GetDTEProvider` 類別中，匯入 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>。  
  
    ```c#  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  在 `GetClassifier()` 方法中，加入下列程式碼。  
  
    ```c#  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  如果您必須使用 <xref:EnvDTE80.DTE2> 介面，您可以將 DTE 物件轉換成它。  
  
## 請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)