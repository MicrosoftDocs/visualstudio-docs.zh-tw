---
title: 新增或變更的行為，與編輯器介面卡 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22028b1b2725f184c3d5748f2885a17d4bff0c60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>新增或變更的行為，與編輯器介面卡
如果您要更新舊版的 Visual Studio 核心編輯器中，針對所撰寫的程式碼，而且您打算使用編輯器介面卡 （或填充碼），而不是使用新的 API，您應留意下列中的編輯器配接器行為的差異相對於前一個核心編輯器中。  
  
## <a name="features"></a>功能  
  
#### <a name="using-setsite"></a>使用 SetSite()  
 您必須呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A>共同建立文字緩衝區，文字檢視和程式碼視窗，然後再執行其他任何作業在其上的時。 不過，這不需要，如果您使用<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>建立它們，因為這項服務的 create （） 方法本身呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>。  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>在您自己的內容中裝載必須搭配和 IVsTextView  
 您可以同時裝載<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>您自己使用 Win32 模式或 WPF 模式的內容中。 不過，您應該記住有兩種模式的一些差異。  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>使用 Win32 和 WPF 必須搭配版本  
 程式碼編輯器 視窗衍生自<xref:Microsoft.VisualStudio.Shell.WindowPane>，它會實作較舊的 Win32<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>介面以及新的 WPF<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane>介面。 您可以使用<xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A>方法來建立 HWND 型裝載環境中，或<xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A>方法來建立 WPF 裝載環境。 基礎編輯器一定會使用 WPF 中，但您可以建立適合您的裝載需求，如果您要直接將您自己的內容內嵌此視窗窗格的視窗窗格的類型。  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>使用 Win32 和 WPF IVsTextView 版本  
 您可以設定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>Win32 模式或 WPF 模式。  
  
 當編輯器 factory 建立文字檢視中，依預設，位於 HWND，和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A>傳回 HWND。 您不應該使用此模式中內嵌的 WPF 控制項的編輯器。  
  
 若要設定 WPF 模式文字檢視，您必須呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A>並傳入<xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3>中初始化的其中一個旗標為`InitView`參數。 您可以取得<xref:System.Windows.FrameworkElement>藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>。  
  
 WPF 模式不同於 Win32 模式有兩種。 首先，[文字] 檢視可以裝載 WPF 內容中。 您可以存取 [WPF] 窗格中，透過將轉型<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>至<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane>，然後呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>。 第二個，<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A>仍會傳回 HWND，但此 HWND 可以只能用來檢查它的位置，並將焦點設在其上。 您必須使用這個 HWND 回應 WM_PAINT 訊息時，因為它不會影響編輯器如何繪製視窗。 這個 HWND 存在於只為了轉換至新的編輯器程式碼透過介面卡。 強烈建議，您不應該使用`VIF_NO_HWND_SUPPORT`如果您的元件需要運作，因為從傳回的 HWND 中限制 HWND`GetWindowHandle`而在此模式中。  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>傳遞陣列當做原生程式碼中的參數  
 有許多在舊版的應用程式開發介面編輯器中的方法都有包含計數和陣列的參數。 範例如下：  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 如果您在原生程式碼中呼叫這些方法，您必須一次傳遞中只有一個項目。 如果您將多個項目中，呼叫會遭到拒絕，因為主要的 interop 實作發生問題。  
  
 問題是更複雜的方法如<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>。 每次呼叫此方法時，它會清除先前略過的標記類型清單，所以不可能只是要呼叫這個方法三次包含三種不同的標記類型。 呼叫這個方法只能在 managed 程式碼中是唯一的補救方法。  
  
#### <a name="threading"></a>執行緒  
 您永遠應該從 UI 執行緒呼叫緩衝區配接器。 緩衝區配接器是受管理的物件，這表示它從呼叫 managed 程式碼將會略過 COM 封送處理，而且您的呼叫將不會自動封送處理至 UI 執行緒。  如果您從背景執行緒呼叫緩衝區配接器，您必須使用<xref:System.Windows.Threading.Dispatcher.Invoke%2A>或類似的方法。  
  
#### <a name="lockbuffer-methods"></a>LockBuffer 方法  
 所有 LockBuffer() 方法已被都取代。 範例如下：  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>認可事件  
 認可不支援的事件。 呼叫的方法，則建議為這些事件會導致方法傳回失敗碼。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> Commit （） 上不會再引發。 相反地，則引發在每次文字變更。  
  
#### <a name="text-markers"></a>文字標記  
 您必須呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A>上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>物件時，您將它們移除。 在舊版中，您只需要到發行的標記。  
  
#### <a name="line-numbers"></a>行號  
 各種不同的方法上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>、 行號對應至基礎緩衝區行號、 不限行號納入大綱和自動換行，如 Visual Studio 2008 所示。  
  
 受影響的方法包括的下列 （清單未全部列出）：  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>大綱  
 用戶端的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>會看到只使用加入這些大綱區域<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>。 它們不會看到特定區域，因為它們不會加入到編輯器介面卡。 同樣地，這些用戶端不會看到大綱區域新增的語言 （包括 C# 和 c + +），會使用新的編輯器程式碼，而不是編輯器介面卡。  
  
#### <a name="line-heights"></a>行高度  
 在新的編輯器中，文字線條可以具有不同的高度，根據字型大小和可能會移動相對於其他行線條的線條可能轉換。 例如，由方法傳回的行高<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A>是使用套用沒有列轉換的預設字型大小線條的高度。 這個高度可能也不一定能反映實際檢視中的資料行的高度。  
  
#### <a name="eventing-and-undo"></a>事件處理和復原  
 在新的編輯器中，檢視會繼續執行作業，例如轉譯和持續，引發事件，即使已開啟的復原叢集。 此行為是不同於舊版的檢視，並未執行這些作業在關閉之前的復原叢集。  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A>方法將會失敗，如果您要傳入的類別未實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2>或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>。 不再支援自訂 Win32 描繪快顯。  
  
#### <a name="smarttags"></a>智慧標籤  
 沒有配接器支援的智慧標籤，以建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>，和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2>介面。  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> 未實作。  
  
## <a name="unimplemented-methods"></a>未實作的方法  
 文字緩衝區配接器、 文字檢視配接器，以及文字層配接器並未實作一些方法。  
  
|介面|未實作|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` 未實作。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> 被實作的介面卡，但忽略大綱 ui。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> 被實作的介面卡，但忽略大綱 ui。|