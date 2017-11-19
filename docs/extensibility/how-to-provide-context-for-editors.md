---
title: "如何： 提供的內容編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6687ce3ed73a96778b84cec6e77d5c0b3145702d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-context-for-editors"></a>如何： 提供的內容編輯器
編輯器中，內容為使用中，只有當編輯器具有焦點或之前在焦點已移至 工具視窗有焦點時。 您可以提供編輯器的內容，執行下列動作：  
  
1.  建立的內容封包。  
  
2.  選取項目識別項 (SEID) 發行內容屬性包。  
  
3.  維護屬性包中的內容。  
  
 下列程序所涵蓋這些工作。 如需提供內容的詳細資訊，請參閱**強固程式設計**本主題稍後。  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>若要建立的內容封包，編輯器或設計工具  
  
1.  呼叫`QueryService`上您<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>介面<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>服務。  
  
     指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>介面傳回。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>方法來建立新的內容或子內容包。  
  
     指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>介面傳回。  
  
3.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>加入內容或子內容的屬性包中的屬性、 查詢關鍵字或 F1 關鍵字的方法。  
  
4.  如果您要建立子內容包，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>方法來連結至父內容包子內容的屬性包。  
  
5.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>接收通知時**動態說明**視窗即將更新。  
  
     具有**動態說明**視窗呼叫您的編輯器它已準備好更新可讓您有機會延遲，直到更新發生變更的內容。 這樣可以改善效能，因為它可讓您延遲執行耗時的演算法，直到系統允許的閒置時間為止。  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>若要發行內容包 SEID 至  
  
1.  呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>服務傳回的指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>介面。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>，指定的項目識別項 (`elementid`參數)，表示您會將內容傳遞給全域層級 SEID_UserContext 的值。  
  
3.  當編輯器或設計工具變成作用中 」、 「 中的值及其<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>物件會傳播至全域選取範圍。 您只需要完成此程序一次每個工作階段，並儲存您所呼叫時所建立的全域內容的指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>。  
  
### <a name="to-maintain-the-context-bag"></a>若要維護內容包  
  
1.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>，確保**動態說明**視窗之前，會呼叫編輯器或設計工具便會更新。  
  
     已呼叫每個內容包<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>建立內容屬性包，並已實作之後<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>，IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>通知內容提供者內容包將會更新。 您可以使用這個呼叫之前變更的屬性和關鍵字，在內容屬性包，和任何子內容竄改包，**動態說明**視窗更新，就會發生。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>上內容屬性包，指出編輯器或設計工具是否有新的內容。  
  
     當**動態說明**視窗呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>來表示它正在更新，請在編輯器或設計工具可以在該時間更新適用於父內容包和任何子內容包的內容。  
  
    > [!NOTE]
    >  `SetDirty`旗標會自動設為`true`每當加入或移除內容包從內容。 **動態說明**視窗只會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>內容包上如果`SetDirty`旗標設為`true`。 它會重設為`false`更新之後。  
  
3.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>將內容新增至作用中的內容集合或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>移除內容。  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您要撰寫您自己的編輯器，您必須完成所有三個編輯器提供內容本主題中的程序。  
  
> [!NOTE]
>  若要正常啟動編輯器或設計工具的視窗，並確保命令路由會更新正確，您必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>讓焦點視窗元件上。  
  
 SEID 是變更選取項目為基礎的屬性集合。 SEID 資訊可透過全域選取範圍。 全域選取範圍有線網路到所觸發的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>介面，而且已為每個清單選取 （目前編輯器、 目前的工具視窗、 目前的階層，等等）。  
  
 為編輯器和設計工具，在每當變更其內容，可以將游標移在文字內、 沒有效率經常更新內容包。 若要讓更新更有效率地偵測編輯器或設計師視窗內移動資料指標的任何時間，您可以呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>。 這樣做可讓您保留您的內容變更，直到閒置一段時間和 IDE 的內容服務會傳送通知給編輯器或設計工具的**動態說明**視窗正在更新。 這個方法會用於本主題 < 若要維護內容包 」 程序。  
  
 您的編輯器或設計工具內的活動提供內容之後，您應該提供特定 F1 關鍵字可讓使用者取得的編輯器或設計工具本身的說明。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>