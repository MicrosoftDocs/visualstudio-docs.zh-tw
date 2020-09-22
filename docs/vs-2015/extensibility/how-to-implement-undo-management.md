---
title: 如何：執行復原管理 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839204"
---
# <a name="how-to-implement-undo-management"></a>如何：實作復原管理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

用於復原管理的主要介面是 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> 由環境所執行。 若要支援復原管理，請執行個別的復原單位 (也就是 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> 可以包含多個個別步驟的。  
  
 執行復原管理的方式會根據您的編輯器是否支援多個視圖而有所不同。 下列各節將詳細說明每個執行的程式。  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>編輯器支援單一視圖的情況  
 在此案例中，編輯器不支援多個視圖。 只有一個編輯器和一份檔，並支援復原。 使用下列程式來執行復原管理。  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>支援單一視圖編輯器的復原管理  
  
1. 在的 `QueryInterface` `IServiceProvider` 視窗框架上 `IOleUndoManager` ，從檔視圖物件呼叫，以存取復原管理員 (`IID_IOLEUndoManager`) 。  
  
2. 將視圖置於視窗框架時，它會取得可用來呼叫的網站指標 `QueryInterface` `IServiceProvider` 。  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>編輯器支援多個視圖的情況  
 如果您有檔和視圖分隔，通常會有一個復原管理員與檔本身相關聯。 所有復原單位都會放置在與檔資料物件相關聯的一個復原管理員上。  
  
 檔資料物件會呼叫以具現 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 化「復原管理員」，並指定 CLSID_OLEUndoManager 的類別識別碼，而不會查詢「復原管理員」（每個視圖都有一個）。 類別識別碼是在 OCUNDOID 檔中定義的。  
  
 使用 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 建立您自己的復原管理員實例時，請使用下列程式，將您的復原管理員連結至環境。  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>將您的復原管理員連結至環境  
  
1. `QueryInterface`在針對傳回的物件上 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> 呼叫 `IID_IOleUndoManager` 。 將指標儲存至 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> 。  
  
2. `QueryInterface`在上 `IOleUndoManager` 呼叫 `IID_IOleCommandTarget` 。 將指標儲存至 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。  
  
3. 將您 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 呼叫轉送到預存 `IOleCommandTarget` 介面，以進行下列 StandardCommandSet97 命令：  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - cmdidRedo  
  
   - cmdidMultiLevelRedo  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. `QueryInterface`在上 `IOleUndoManager` 呼叫 `IID_IVsChangeTrackingUndoManager` 。 將指標儲存至 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> 。  
  
    使用的指標 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> ，即可呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> 、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> 方法。  
  
5. `QueryInterface`在上 `IOleUndoManager` 呼叫 `IID_IVsLinkCapableUndoManager` 。  
  
6. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A>使用您的檔呼叫，這也應該會執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> 介面。 當您的檔關閉時，請呼叫 `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` 。  
  
7. 當您的檔關閉時，請 `QueryInterface` 在的復原管理員上呼叫 `IID_IVsLifetimeControlledObject` 。  
  
8. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>。  
  
9. 對檔進行變更時，請 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> 使用類別在管理員上呼叫 `OleUndoUnit` 。 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>方法會保留物件的參考，因此您通常會在之後將它釋出 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> 。  
  
   `OleUndoManager`類別代表單一復原堆疊實例。 因此，針對復原或重做所追蹤的每個資料實體都會有一個復原管理員物件。  
  
> [!NOTE]
> 雖然文字編輯器廣泛使用復原管理員物件，但它是一種一般元件，不提供文字編輯器的特定支援。 如果您想要支援多層級的復原或重做，您可以使用此物件來執行此動作。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [如何：清除復原堆疊](../extensibility/how-to-clear-the-undo-stack.md)
