---
title: 編輯器介面卡的新行為或變更行為 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc7ddaf7ec67a1e33248d5ce424868849200d3e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194183"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>編輯器配接器的新行為或變更行為
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您要更新針對舊版 Visual Studio core 編輯器所撰寫的程式碼，而且想要使用編輯器介面卡 (或填充碼) 而不是使用新的 API，您應該留意與先前的核心編輯器相關之編輯器介面卡行為的下列差異。  
  
## <a name="features"></a>特性  
  
#### <a name="using-setsite"></a>使用 SetSite ( # A1  
 當您在 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> 執行任何其他作業之前，必須先呼叫 CoCreate 文字緩衝區、文字視圖和程式碼視窗。 但是，如果您使用來建立它們，就不需要這麼做 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> ，因為這項服務的 create ( # A1 方法本身會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> 。  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>在您自己的內容中裝載 IVsCodeWindow 和 IVsTextView  
 您可以 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 使用 Win32 模式或 WPF 模式，在您自己的內容中裝載和。 不過，請記住，這兩種模式有一些差異。  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>使用 Win32 和 WPF 版本的 IVsCodeWindow  
 編輯器程式碼視窗是衍生自 <xref:Microsoft.VisualStudio.Shell.WindowPane> ，它會實作為舊的 Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 介面以及新的 WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> 介面。 您可以使用 <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> 方法來建立以 HWND 為基礎的裝載環境，或使用 <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> 方法來建立 WPF 主控環境。 基礎編輯器一律使用 WPF，但如果您將此視窗窗格直接內嵌到您自己的內容中，則可以建立適合您裝載需求的視窗窗格類型。  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>使用 Win32 和 WPF 版本的 IVsTextView  
 您可以將設定 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 為 Win32 模式或 WPF 模式。  
  
 當編輯器 factory 建立文字視圖時，根據預設，它會裝載于 HWND 內，並傳回 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> hwnd。 您不應該使用這個模式將編輯器內嵌到 WPF 控制項內。  
  
 若要將文字視圖設定為 WPF 模式，您必須呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> ，並傳入 <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> 做為參數中的其中一個初始化旗標 `InitView` 。 您可以藉 <xref:System.Windows.FrameworkElement> 由呼叫來取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> 。  
  
 WPF 模式與 Win32 模式有兩種不同之處。 首先，文字視圖可以裝載于 WPF 內容中。 您可以藉由將轉換 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 成和呼叫來存取 WPF 窗格 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> 。 其次， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> 仍然會傳回 hwnd，但是這個 hwnd 只能用來檢查它的位置並設定焦點。 您不得使用這個 HWND 來回應 WM_PAINT 的訊息，因為它不會影響編輯器繪製視窗的方式。 這個 HWND 只是為了透過介面卡來加速轉換至新的編輯器程式碼。 `VIF_NO_HWND_SUPPORT`如果您的元件需要 hwnd 才能使用，強烈建議您不要使用，因為 `GetWindowHandle` 在這個模式下，從中傳回的 hwnd 有限制。  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>以機器碼中的參數傳遞陣列  
 舊版編輯器 API 中有許多方法，其中包含陣列及其計數的參數。 範例包括：  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 如果您在機器碼中呼叫這些方法，您一次只能傳入一個元素。 如果您傳入一個以上的元素，呼叫將會遭到拒絕，因為主要 interop 執行有問題。  
  
 使用之類的方法時，問題更複雜 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> 。 每次呼叫這個方法時，它會清除先前已忽略標記類型的清單，因此不可能直接以三種不同的標記類型呼叫這個方法三次。 唯一的解決方法是只在 managed 程式碼中呼叫這個方法。  
  
#### <a name="threading"></a>執行緒  
 您應該一律從 UI 執行緒呼叫緩衝區介面卡。 緩衝區介面卡是受管理物件，這表示從 managed 程式碼呼叫它將會略過 COM 封送處理，而您的呼叫將不會自動封送處理至 UI 執行緒。  如果您是從背景執行緒呼叫緩衝區介面卡，則必須使用 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 或類似的方法。  
  
#### <a name="lockbuffer-methods"></a>LockBuffer 方法  
 所有 LockBuffer ( # A1 方法都已被取代。 範例包括：  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>認可事件  
 不支援 Commit 事件。 呼叫針對這些事件建議的方法，會導致方法傳回失敗碼。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents>認可 ( # A1 不會再引發。 相反地，它們會在每次文字變更時引發。  
  
#### <a name="text-markers"></a>文字標記  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A>移除物件時，您必須對 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> 物件呼叫。 在先前的版本中，您只需要釋放標記。  
  
#### <a name="line-numbers"></a>行號  
 針對和上的各種方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> ，行號會對應到基礎緩衝區行號，而不是對應于大綱和自動換行的行號，如 Visual Studio 2008。  
  
 受影響的方法包括下列 (清單不是完整) ：  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>大綱  
 的用戶端 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 只會看到使用或新增的大綱區域 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> 。 他們不會看到臨機操作區域，因為它們不是透過編輯器介面卡新增的。 同樣地，這些用戶端將不會看到語言新增的大綱區域 (包括使用新編輯器程式碼的 c # 和 c + +) ，而非編輯器介面卡。  
  
#### <a name="line-heights"></a>線條高度  
 在新的編輯器中，文字線條可以有不同的高度，視字型大小和可能移動線條相對於其他線條的可能線條轉換而定。 方法所傳回的線條高度 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> 是使用預設字型大小，而不套用任何線條轉換的線條高度。 這個高度可能或不會反映視圖中線條的實際高度。  
  
#### <a name="eventing-and-undo"></a>事件和復原  
 在新的編輯器中，視圖會繼續執行作業，例如，即使在開啟復原叢集時，也會持續地轉譯和引發事件。 此行為不同于舊版視圖的行為，不會執行這些作業，直到關閉復原叢集為止。  
  
#### <a name="intellisense"></a>IntelliSense  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A>如果您傳入的類別未執行或，方法將會失敗 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> 。 不再支援自訂的 Win32 主控描繪快顯視窗。  
  
#### <a name="smarttags"></a>標記  
 使用、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData> 、和介面建立的智慧標籤不支援介面卡 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> 。  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> 未實作為。  
  
## <a name="unimplemented-methods"></a>未實現的方法  
 某些方法尚未在文字緩衝卡、text view adapter 和 text layer adapter 上執行。  
  
|介面|未實作|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` 未實作為。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> 會在介面卡中執行，但會被大綱 UI 忽略。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> 會在介面卡中執行，但會被大綱 UI 忽略。|
