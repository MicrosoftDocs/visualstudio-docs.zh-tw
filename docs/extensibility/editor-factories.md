---
title: "編輯器 Factory | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版的編輯器 factory"
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 編輯器 Factory
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

編輯器工廠建立編輯器物件，並將它們置於視窗外框，稱為 「 實體檢視。  它會建立文件資料和建立編輯器和設計工具所需的文件檢視物件。  編輯器工廠，才能建立 Visual Studio 的核心編輯器和其他標準的編輯器。  自訂編輯器也可以選擇性地由編輯器工廠。  
  
 您藉由實作建立編輯器工廠<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面。  下列範例會說明如何實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>來建立編輯器工廠：  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-cs[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 編輯器便會載入第一次您開啟該編輯器所處理的檔案類型。  您可以選擇開啟特定的編輯器\] 或 \[預設的編輯器。  如果您選取的預設編輯器，整合式的開發環境 \(IDE\) 決定正確的編輯器 」，然後再將它開啟。  如需詳細資訊，請參閱 [決定編輯器隨即會開啟專案中的檔案](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)。  
  
## 登錄編輯器工廠  
 您可以使用編輯器建立之前，首先必須登錄其資訊，包括它可以處理的附檔名。  
  
 如果您的 VSPackage 撰寫 managed 程式碼中，您可以使用管理套件架構 \(MPF\) 方法<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>之後您 VSPackage 已載入, 登錄編輯器。  如果您的 VSPackage unmanaged 程式碼所撰寫，那麼您必須使用登錄編輯器工廠<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>服務。  
  
### 藉由使用登錄編輯器工廠 Managed 程式碼  
 您必須註冊編輯器工廠，在您的 VSPackage `Initialize`方法。  第一次呼叫`base.Initialize`，然後呼叫<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>的每個編輯器工廠  
  
 在 managed 程式碼，並不需要取消註冊編輯器工廠，因為 VSPackage 會為您處理這。  此外，如果您的編輯器工廠實作<xref:System.IDisposable>，會自動處置時，它未註冊。  
  
### 登錄編輯器工廠使用 unmanaged 程式碼  
 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>實作的編輯器套件，使用`QueryService`方法以呼叫`SVsRegisterEditors`。  如此一來傳回變數的指標， <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>。  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>方法傳遞的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面。  您必須 mplement <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>在不同的類別。  
  
## 編輯器處理站註冊程序  
 Visual Studio 載入您使用編輯器工廠的編輯器時，就會發生下列的程序：  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案系統呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。  
  
2.  這個方法會傳回編輯器工廠。  Visual Studio 的延遲載入編輯器的套件，不過，直到專案系統實際需要在編輯器\]。  
  
3.  當專案系統需要編輯器\] 中時，會呼叫 Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>，特定的方法會傳回文件檢視\] 與 \[文件的資料物件。  
  
4.  如果呼叫程式編輯器工廠使用 Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>傳回文件的資料物件和文件檢視物件、 Visual Studio 再建立文件視窗、 將文件中的 view 物件，以及讓項目加入文件資料的物件執行文件表格 \(RDT\)。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [執行中的文件表格](../extensibility/internals/running-document-table.md)