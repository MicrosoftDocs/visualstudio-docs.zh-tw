---
title: "提供復原設計工具支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 98243c15f5f69a9aecba589b966d56a68201ab2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="supplying-undo-support-to-designers"></a>提供給設計工具的復原支援
設計工具，如編輯器，通常需要支援復原作業，因此使用者就可以反轉最近的變更時修改程式碼項目。  
  
 大部分設計工具中執行 Visual Studio 中，有自動環境所提供的復原支援。  
  
 設計工具的實作必須提供復原功能的支援：  
  
-   藉由實作抽象基底類別提供復原管理<xref:System.ComponentModel.Design.UndoEngine>  
  
-   藉由實作提供持續性和 codedom 之間支援<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>和<xref:System.ComponentModel.Design.IComponentChangeService>類別。  
  
 如需有關撰寫使用設計工具[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，請參閱[擴充設計階段支援](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供的預設復原基礎結構：  
  
-   提供復原管理實作透過<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>和<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>類別。  
  
-   提供的持續性和所有預設的 CodeDOM 支援<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>和<xref:System.ComponentModel.Design.IComponentChangeService>實作。  
  
## <a name="obtaining-undo-support-automatically"></a>自動取得復原支援  
 任何的設計工具中建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]有自動和完整的復原支援 if、 設計工具：  
  
-   利用<xref:System.Windows.Forms.Control>基礎其使用者介面的類別。  
  
-   採用標準的 CodeDOM 程式碼產生和剖析系統程式碼產生和持續性。  
  
     如需使用 Visual Studio CodeDOM 支援的詳細資訊，請參閱[動態原始程式碼的產生和編譯](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>何時使用明確的設計工具恢復支援  
 如果使用圖形化使用者介面，稱為檢視配接器，而其中所提供的設計工具必須提供自己的復原管理<xref:System.Windows.Forms.Control>。  
  
 舉例來說，這可能會以 web 為基礎的圖形設計介面建立產品而不是[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]基礎的圖形化介面。  
  
 在這種情況下，則需要註冊使用此檢視配接器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用<xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>，並提供明確的復原管理。  
  
 設計工具需要提供 CodeDOM 和持續性支援如果它們不會使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中提供的程式碼產生模型<xref:System.CodeDom>命名空間。  
  
## <a name="undo-support-features-of-the-designer"></a>復原設計工具的支援功能  
 環境 SDK 提供可供未使用的設計工具的支援復原功能提供所需的介面的預設實作<xref:System.Windows.Forms.Control>基礎類別及其使用者介面或標準 CodeDOM 和持續性的模型。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>類別衍生自[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]<xref:System.ComponentModel.Design.UndoEngine>類別使用的實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>類別以管理復原操作。  
  
 Visual Studio 提供下列功能來設計工具的復原：  
  
-   跨多個設計工具的連結的復原功能。  
  
-   設計工具中的子單位可以藉由實作與互動其父系<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>上<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>。  
  
 環境 SDK 提供 CodeDOM 和持續性支援藉由提供：  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>為實作<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 A<xref:System.ComponentModel.Design.IComponentChangeService>提供[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' 設計主應用程式。  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>若要提供復原功能支援使用環境 SDK 功能  
 若要取得復原的支援，必須實作設計工具的物件：  
  
-   具現化，並初始化的執行個體<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>的有效類別<xref:System.IServiceProvider>實作。  
  
-   這<xref:System.IServiceProvider>類別必須提供下列服務：  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         使用設計工具[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]CodeDOM 序列化可能會選擇使用<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>隨附[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]做為它的實作<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>。  
  
         在此情況下，<xref:System.IServiceProvider>類別提供給<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>建構函式應該的實作會傳回此物件<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>類別。  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         使用預設的設計工具<xref:System.ComponentModel.Design.DesignSurface>提供[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]保證設計主應用程式都有的預設實作<xref:System.ComponentModel.Design.IComponentChangeService>類別。  
  
 實作的設計工具<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>根據的復原機制會自動追蹤變更，如果：  
  
-   屬性變更都會經過<xref:System.ComponentModel.TypeDescriptor>物件。  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>認可復原變更時，會以手動方式產生事件。  
  
-   修改設計工具上的內容中建立<xref:System.ComponentModel.Design.DesignerTransaction>。  
  
-   在設計工具選擇明確建立的實作所提供的標準復原單位使用的復原單位<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>或 Visual Studio 特定實作<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>，其衍生自<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>也會提供兩者的實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [擴充設計階段支援](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)