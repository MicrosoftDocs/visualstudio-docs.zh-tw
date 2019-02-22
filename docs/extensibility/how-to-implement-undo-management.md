---
title: HOW TO：實作復原管理 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8d5059ddca1d428f1a1f66cb45e32cdc6f37de3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929532"
---
# <a name="how-to-implement-undo-management"></a>HOW TO：實作復原管理
用於復原管理的主要介面是<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>，這由環境實作。 若要支援復原管理，請實作不同的復原單位 (也就是<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>，其中可以包含多個個別的步驟。  
  
 實作復原管理的方式，需視您的編輯器是否支援多個檢視的方法而有所不同。 下列各節會詳細說明每個實作的程序。  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>其中的編輯器支援單一檢視的情況下  
 在此案例中，編輯器不支援多個檢視。 只有一個編輯器和一份文件，並支援復原。 您可以使用下列程序來實作復原管理。  
  
### <a name="to-support-undo-management-for-a-single-view-editor"></a>若要支援單一檢視編輯器復原管理  
  
1.  呼叫`QueryInterface`上`IServiceProvider`介面上的視窗框架`IOleUndoManager`，從 文件檢視物件來存取復原管理員 (`IID_IOLEUndoManager`)。  
  
2.  當檢視設置至視窗框架時，它會取得站台的指標，它可以用來呼叫`QueryInterface`針對`IServiceProvider`。  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>其中的編輯器支援多個檢視的情況下  
 如果您有文件和檢視區隔，就與文件本身相關聯的一個正常復原管理員。 所有的復原單位會放在一個復原管理員與文件資料物件建立關聯。  
  
 而不是復原管理員，其中有一個針對每個檢視，檢視查詢的文件資料物件會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>來具現化復原管理員，指定 CLSID_OLEUndoManager 類別識別項。 中定義的類別識別項*OCUNDOID.h*檔案。  
  
 當使用<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>連結至環境的復原管理員建立您自己的復原管理員執行個體，請使用下列程序。  
  
### <a name="to-hook-your-undo-manager-into-the-environment"></a>若要將您的復原管理員連結至環境  
  
1. 呼叫`QueryInterface`傳回的物件上<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>如`IID_IOleUndoManager`。 儲存的指標<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>。  
  
2. 呼叫`QueryInterface`上`IOleUndoManager`如`IID_IOleCommandTarget`。 儲存的指標<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
3. 轉送您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>並<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>呼叫預存的`IOleCommandTarget`下列 StandardCommandSet97 命令介面：  
  
   -   cmdidUndo  
  
   -   cmdidMultiLevelUndo  
  
   -   cmdidRedo  
  
   -   cmdidMultiLevelRedo  
  
   -   cmdidMultiLevelUndoList  
  
   -   cmdidMultiLevelRedoList  
  
4. 呼叫`QueryInterface`上`IOleUndoManager`如`IID_IVsChangeTrackingUndoManager`。 儲存的指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>。  
  
    使用指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>來呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>，則<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>，和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A>方法。  
  
5. 呼叫`QueryInterface`上`IOleUndoManager`如`IID_IVsLinkCapableUndoManager`。  
  
6. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A>與文件時，它也應該實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient>介面。 當您的文件關閉時，呼叫`IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`。  
  
7. 當您的文件關閉時，呼叫`QueryInterface`在您的復原經理`IID_IVsLifetimeControlledObject`。  
  
8. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>。  
  
9. 文件變更時，呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>上的管理員`OleUndoUnit`類別。 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>方法會保留物件參考，因此通常您在釋放之後<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>。  
  
   `OleUndoManager`類別代表單一復原 stack 執行個體。 因此，為每個受到追蹤的復原或取消復原的資料實體的一個復原管理員物件。  
  
> [!NOTE]
>  文字編輯器是廣泛使用復原管理員物件，就沒有特定的支援的文字編輯器的一般元件。 如果您想要支援多層級復原或取消復原，您可以使用此物件，若要這樣做。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [如何：清除復原堆疊](../extensibility/how-to-clear-the-undo-stack.md)