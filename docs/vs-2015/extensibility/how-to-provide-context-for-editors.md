---
title: 如何：提供編輯器的內容 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838935"
---
# <a name="how-to-provide-context-for-editors"></a>如何：為編輯器提供內容
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在編輯器中，只有當編輯器具有焦點，或在焦點移至工具視窗之前立即取得焦點時，內容才會處於作用中狀態。 您可以執行下列動作來提供編輯器的內容：  
  
1. 建立內容包。  
  
2. 將內容包發佈至選取專案識別碼 (SEID) 。  
  
3. 維護包中的內容。  
  
   下列程式涵蓋這些工作。 如需有關提供內容的詳細資訊，請參閱本主題稍後的 **健全程式設計** 。  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>若要建立編輯器或設計工具的內容包  
  
1. `QueryService`在您 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 的介面上呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> 服務。  
  
     傳回介面的指標 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> 。  
  
2. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> 方法來建立新的內容或子上下文包。  
  
     傳回介面的指標 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> 。  
  
3. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> 方法，將屬性、查閱關鍵字或 F1 關鍵字加入至內容或子上下文包。  
  
4. 如果您要建立子節點包，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> 方法，將子上下文包連結到父內容包。  
  
5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>當**動態**說明視窗即將更新時，呼叫來接收通知。  
  
     讓 [ **動態** 說明] 視窗在已準備好進行更新時呼叫編輯器，讓您有機會延遲變更內容，直到發生更新為止。 這麼做可改善效能，因為它可讓您順延強制耗時的演算法，直到系統閒置時間可用為止。  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>將內容包發佈至 SEID  
  
1. `QueryService`在服務上呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> ，以傳回介面的指標 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> 。  
  
2. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> ，指定 (`elementid` 參數的元素識別碼) SEID_UserCoNtext 的值，表示您要將內容傳遞給全域層級。  
  
3. 當編輯器或設計工具變成使用中時，其物件中的值 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> 會傳播到全域選取範圍。 您只需要在每個會話完成此程式一次，然後將指標儲存在您呼叫時所建立的全域內容 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> 。  
  
### <a name="to-maintain-the-context-bag"></a>若要維護內容包  
  
1. 執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> 以確保 **動態** 說明視窗會在其更新之前呼叫編輯器或設計工具。  
  
     針對 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> 在建立並執行內容包之後所呼叫的每個內容包 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> ，IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> 會呼叫來通知內容提供者，內容包將會更新。 您可以使用這個呼叫來變更內容包中的屬性和關鍵字，以及在任何子上下文包中，變更 [ **動態** 說明] 視窗進行更新之前的屬性和關鍵字。  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>在內容包上呼叫，以指出編輯器或設計工具具有新的內容。  
  
     當 [ **動態** 說明] 視窗呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> 來指出正在更新時，編輯器或設計工具可以針對父內容包和該時間的任何子上下文包，適當地更新內容。  
  
    > [!NOTE]
    > `SetDirty` `true` 每當從內容包中加入或移除內容時，旗標就會自動設定為。 [ **動態** 說明] 視窗只 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> 會在旗標設定為時，才呼叫內容包 `SetDirty` `true` 。 它會在更新之後重設為 `false` 。  
  
3. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> 將內容加入至使用中內容集合或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> 移除內容。  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您正在撰寫自己的編輯器，則必須完成本主題中的這三個程式，才能提供編輯器的內容。  
  
> [!NOTE]
> 若要適當地啟動編輯器或設計工具視窗，並確定命令路由已正確更新，您必須 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 在元件上呼叫，使其成為焦點視窗。  
  
 SEID 是屬性的集合，這些屬性會根據選取專案而變更。 您可以透過全域選取範圍來取得 SEID 資訊。 全域選取範圍會連接到介面所觸發的事件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> ，而且會列出已選取的所有專案 (目前的編輯器、目前的工具視窗、目前的階層等) 。  
  
 針對編輯器和設計工具，當資料指標在單字內移動時，內容可能會變更，因此，經常更新內容包會沒有效率。 當您在編輯器或設計工具視窗內偵測到游標移動時，若要讓更新更有效率，可以呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> 。 這樣做可讓您保存內容變更，直到有閒置時間，而 IDE 的內容服務會傳送通知給 **動態** 說明視窗所更新的編輯器或設計工具。 本主題的「若要維護內容包」程式中使用此方法。  
  
 在編輯器或設計工具中提供活動的內容之後，您應該提供特定的 F1 關鍵字，讓使用者能夠取得編輯器或設計工具本身的說明。  
  
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
