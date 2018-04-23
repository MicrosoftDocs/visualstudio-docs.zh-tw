---
title: 如何： 實作復原管理 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b01b7b8edf5ebe4b8c3e5277e87f9797860b552f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-implement-undo-management"></a>如何： 實作復原管理
用於復原管理的主要介面為<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>，由環境實作。 支援管理復原，請實作不同的復原單位 (也就是<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>，其中可以包含多個個別的步驟。  
  
 視您的編輯器是否支援多個檢視實作復原管理的方式而有所不同。 下列各節會詳細說明每個實作的程序。  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>其中一個編輯器支援單一檢視的情況下  
 在此案例中，編輯器不支援多個檢視。 只有一個編輯器和一份文件，並支援復原。 您可以使用下列程序來實作復原管理。  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>若要為單一檢視的編輯器支援復原管理  
  
1.  呼叫`QueryInterface`上`IServiceProvider`介面上的視窗框架`IOleUndoManager`，從 文件檢視物件，來存取復原管理員 (`IID_IOLEUndoManager`)。  
  
2.  當檢視設置視窗框架時，它會取得網站的指標，它可以用來呼叫`QueryInterface`如`IServiceProvider`。  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>編輯器支援多個檢視的位置的情況下  
 如果您有文件和檢視區隔，就與文件本身相關聯的一個正常復原管理員。 所有的復原單位會放在文件資料物件與相關聯的一個復原管理員。  
  
 而不是復原管理員，其中有一個針對每個檢視，以檢視查詢的文件資料物件會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>，具現化復原管理員，並指定 CLSID_OLEUndoManager 類別識別項。 OCUNDOID.h 檔案中定義的類別識別項。  
  
 當使用<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>若要建立您自己的復原管理員執行個體，請使用下列程序復原管理員連接到環境。  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>復原管理員連接到環境  
  
1.  呼叫`QueryInterface`從傳回的物件上<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>如`IID_IOleUndoManager`。 儲存的指標<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>。  
  
2.  呼叫`QueryInterface`上`IOleUndoManager`如`IID_IOleCommandTarget`。 儲存的指標<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
3.  轉送您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>呼叫預存的`IOleCommandTarget`下列 StandardCommandSet97 命令介面：  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  呼叫`QueryInterface`上`IOleUndoManager`如`IID_IVsChangeTrackingUndoManager`。 儲存的指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>。  
  
     使用指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>，而<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A>方法。  
  
5.  呼叫`QueryInterface`上`IOleUndoManager`如`IID_IVsLinkCapableUndoManager`。  
  
6.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A>與文件，其中應同時實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient>介面。 您的文件關閉時，呼叫`IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`。  
  
7.  您的文件關閉時，呼叫`QueryInterface`上為您復原管理員`IID_IVsLifetimeControlledObject`。  
  
8.  呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>。  
  
9. 文件變更時，呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>上的管理員`OleUndoUnit`類別。 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>方法會保留物件參考，所以通常在發行之後<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>。  
  
 `OleUndoManager`類別代表單一復原堆疊執行個體。 因此，為每個受到追蹤的復原或取消復原的資料實體的一個復原管理員物件。  
  
> [!NOTE]
>  復原管理員物件經常使用文字編輯器，而它是沒有特定支援的文字編輯器的一般元件。 如果您想要支援多層級復原或取消復原，您可以使用此物件，若要這樣做。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [如何： 清除復原堆疊](../extensibility/how-to-clear-the-undo-stack.md)