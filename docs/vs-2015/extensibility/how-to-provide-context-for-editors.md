---
title: HOW TO：編輯器提供的內容 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435900"
---
# <a name="how-to-provide-context-for-editors"></a>HOW TO：編輯器提供的內容
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

編輯器，內容為使用中，只有當編輯器具有焦點或之前焦點已移至 工具視窗焦點時。 您可以提供編輯器的內容，執行下列動作：  
  
1. 建立內容包。  
  
2. 選取項目識別項 (SEID) 發佈的內容封包。  
  
3. 維持封包中的內容。  
  
   這些工作都涵蓋下列程序。 如需有關如何提供內容的詳細資訊，請參閱 <<c0>  **穩固的程式設計**本主題稍後的。  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>若要建立內容包編輯器或設計工具  
  
1. 呼叫`QueryService`在您<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>介面<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>服務。  
  
     指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>介面會傳回。  
  
2. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>方法用來建立新的內容或子內容包。  
  
     指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>介面會傳回。  
  
3. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>加入的內容或子內容的封包中的屬性、 查詢關鍵字或 F1 關鍵字的方法。  
  
4. 如果您要建立的子內容包，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>来連結的父代內容封包的優先型封包的方法。  
  
5. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>收到通知時**動態說明**視窗即將更新。  
  
     擁有**動態說明**視窗呼叫您的編輯器時準備好更新可讓您延遲直到更新，就會發生變更的內容。 這樣可以改善效能，因為它可讓您延遲執行耗時的演算法，直到有可用的系統閒置時間。  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>若要發佈的內容封包至 SEID  
  
1. 呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>服務傳回的指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>介面。  
  
2. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>，指定的項目識別項 (`elementid`參數) 來表示，您會將內容傳遞給全域層級的 SEID_UserContext 的值。  
  
3. 編輯器或設計工具變成作用中時中的值及其<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>物件會傳播至全球的選取項目。 您只需要完成此程序工作階段中，每一次，然後將儲存的指標呼叫時所建立的全域內容<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>。  
  
### <a name="to-maintain-the-context-bag"></a>若要維護的內容封包  
  
1. 實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>，確保**動態說明**視窗之前，會呼叫編輯器或設計工具便會更新。  
  
     已呼叫每個內容包<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>建立的內容封包，並已實作之後<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>，IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>通知內容提供者的內容封包將會更新。 您可以使用這個呼叫之前變更的屬性和關鍵字的內容封包，在和中任何子內容包**動態說明**視窗更新，就會發生。  
  
2. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>上表示的編輯器或設計工具是否有新內容的內容封包。  
  
     當**動態說明**視窗呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>指出正在進行更新，編輯器或設計工具可以在該時間更新適當的父代內容包和任何子內容包的內容。  
  
    > [!NOTE]
    > `SetDirty`旗標會自動設為`true`每當加入或移除的內容封包的內容。 **動態說明** 視窗只會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>上的內容封包如果`SetDirty`旗標設為`true`。 它會重設為`false`之後更新。  
  
3. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>將內容新增至作用中的內容集合或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>移除內容。  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您正在撰寫自己的編輯器，您必須完成所有三個為編輯器提供內容，本主題中的程序。  
  
> [!NOTE]
> 若要正常啟動編輯器或設計工具 視窗，並確保命令路由更新正確，您必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>讓焦點視窗元件上。  
  
 SEID 是變更選取項目為基礎的屬性集合。 SEID 資訊是透過全域選取範圍。 全域的選取項目會連結至所觸發的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>介面，且有一份所有項目，是選取 （目前的編輯器、 目前的工具視窗、 目前的階層，等等）。  
  
 為編輯器和設計工具，可以每次變更的內容中將游標移在 word 內不斷更新的內容封包的效率較低。 若要讓更新更有效率的偵測資料指標移動編輯器或設計工具視窗內的任何時間，您可以呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>。 這樣做可讓您保存您的內容變更，直到閒置時間，且 IDE 的內容服務會傳送通知給編輯器或設計工具，**動態說明**視窗正在更新。 這種方法可在此主題的 「 若要維護的內容封包 」 程序。  
  
 提供您的編輯器或設計工具內的活動的內容之後，您應該提供特定的 F1 關鍵字，若要讓使用者能夠取得編輯器或設計工具本身的說明。  
  
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
