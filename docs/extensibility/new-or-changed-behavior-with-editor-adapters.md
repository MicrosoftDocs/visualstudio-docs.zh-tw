---
title: 新增或變更的行為，與編輯器的介面卡 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63c04e808228898e7542f67ec72bf9d36203547d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061252"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>新增或變更的行為，與編輯器的介面卡
如果您要更新舊版的 Visual Studio 核心編輯器中，針對已撰寫的程式碼，而且您想要使用的編輯器介面卡 （或填充碼），而不是使用新的 API，您應留意下列差異編輯器配接器的行為相對於前一個核心編輯器中。

## <a name="features"></a>功能

### <a name="use-setsite"></a>使用 SetSite()
 您必須呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A>當共同文字緩衝區，文字檢視，並執行在其上的任何其他作業之前，程式碼視窗。 不過，這並非必要，如果您使用<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>來建立它們，因為此服務`Create()`本身的方法呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>。

### <a name="host-ivscodewindow-and-ivstextview-in-your-own-content"></a>在您自己的內容中裝載 IVsCodeWindow 和 IVsTextView
 您可同時裝載<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>自己使用 Win32 模式或 WPF 模式的內容中。 不過，您應該記住，有兩種模式的一些差異。

#### <a name="use-win32-and-wpf-versions-of-ivscodewindow"></a>使用 Win32 和 WPF IVsCodeWindow 版本
 程式碼編輯器 視窗衍生自<xref:Microsoft.VisualStudio.Shell.WindowPane>，它會實作較舊的 Win32<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>介面以及新的 WPF<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane>介面。 您可以使用<xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A>方法用來建立 HWND 型裝載環境中，或<xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A>方法用來建立 WPF 裝載環境。 基礎編輯器一律會使用 WPF，但您可以建立適合您的裝載需求，如果您要直接將您自己的內容中內嵌此窗格的 [視窗] 窗格的種類。

#### <a name="use-win32-and-wpf-versions-of-ivstextview"></a>使用 Win32 和 WPF IVsTextView 版本
 您可以設定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>Win32 模式 」 或 「 WPF 的模式。

 當編輯器 factory 建立文字檢視中，依預設，它裝載在 HWND，和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A>傳回 HWND。 您不應該使用此模式中將 WPF 控制項內的編輯器。

 若要設定 WPF 模式的文字檢視，您必須呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A>，並傳入[TextViewInitFlags3.VIF_NO_HWND_SUPPORT](<xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3.VIF_NO_HWND_SUPPORT>)因為其中一個初始設定旗標在`InitView`參數。 您可以取得<xref:System.Windows.FrameworkElement>藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>。

 WPF 模式與兩種方式的 Win32 模式不同。 首先，[文字] 檢視可以裝載 WPF 內容中。 您可以轉型，以存取 [WPF] 窗格<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>要<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane>，然後呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>。 第二個，<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A>仍然的傳回 HWND，但此 HWND 可只能用來檢查它的位置，並將焦點設定在其上。 您必須使用此 HWND 回應 WM_PAINT 訊息時，因為它不會影響編輯器如何繪製視窗。 只是要協助自己轉換到新的編輯器程式碼透過介面卡有此 HWND。 強烈建議，您不應該使用`VIF_NO_HWND_SUPPORT`如果您的元件需要運作，由於限制傳回的 HWND HWND`GetWindowHandle`當您在此模式。

#### <a name="pass-arrays-as-parameters-in-native-code"></a>將陣列當做參數傳遞原生程式碼
 有許多 API，舊版編輯器中的方法都有包含陣列和其計數的參數。 範例如下：

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>

 如果您在原生程式碼中呼叫這些方法，您必須傳入一次只有一個項目。 如果您傳遞一個以上的項目中，呼叫將會遭到拒絕，因為主要的 interop 實作有問題。

 問題在於這類更複雜方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>。 每次呼叫此方法時，它會清除先前忽略的標記類型清單，因此它不可能只是為了呼叫這個方法三次，包含三種不同的標記類型。 唯一的補救方法是呼叫這個方法只能在 managed 程式碼中。

#### <a name="threading"></a>執行緒
 您應該一律呼叫緩衝區配接器，從 UI 執行緒。 緩衝區配接器是一個受管理的物件，表示成它從 managed 程式碼的呼叫將會略過 COM 封送處理，而且您的呼叫將不會自動封送處理至 UI 執行緒。  如果您從背景執行緒呼叫緩衝區配接器，您必須使用<xref:System.Windows.Threading.Dispatcher.Invoke%2A>或類似的方法。

#### <a name="lockbuffer-methods"></a>LockBuffer 方法
 所有 LockBuffer() 方法已被都取代。 範例如下：

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>

#### <a name="commit-events"></a>認可事件
 認可不支援事件。 建議的方法呼叫這些事件會導致方法傳回失敗碼。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>

#### <a name="texteditorevents"></a>TextEditorEvents
 <xref:EnvDTE.TextEditorEvents>上 commit （） 不會再引發。 而是會在每次文字變更。

#### <a name="text-markers"></a>文字標記
 您必須呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A>上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>物件時將它們移除。 在舊版中，您只需要到版本標記。

#### <a name="line-numbers"></a>行號
 上的方法有許多<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>、 對應至基礎緩衝區行號的行號、 不行號大綱和自動換行，與 Visual Studio 2008 中的該係數。

 受影響的方法包括 （清單未全部列出）：

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
 用戶端<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>將會看到只有那些使用新增的大綱區域<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>。 因為它們不會新增透過編輯器配接器，它們不會看到臨機操作的區域。 同樣地，這些用戶端將不會看到大綱區域新增的語言 (包括C#和C++)，使用新的編輯器程式碼，而不是編輯器介面卡。

#### <a name="line-heights"></a>線條高度
 在新的編輯器中，文字行可以有不同的高度，根據字型大小和可能的線條轉換，可能會移動相對於其他行的行。 例如，由方法傳回的行高<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A>套用的任何行 」 轉換中使用的預設字型大小之線條的高度。 此高度可能，也不一定能反映實際的檢視中的資料行的高度。

#### <a name="eventing-and-undo"></a>事件記錄和復原
 在新的編輯器中，檢視會繼續執行作業，例如轉譯和持續地引發事件。 作業繼續進行甚至復原叢集時開啟。 此行為是不同於舊版的檢視，並未執行這些作業在關閉之前的復原叢集。

#### <a name="intellisense"></a>IntelliSense

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A>方法將會失敗，如果您在不實作的類別中傳遞<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2>或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>。 不再支援主控描繪快顯的自訂 Win32。

#### <a name="smarttags"></a>SmartTags
 智慧標籤，以建立任何配接器支援<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>，和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2>介面。

#### <a name="dte"></a>DTE
 <xref:EnvDTE80.IncrementalSearch> 未實作。

## <a name="unimplemented-methods"></a>未實作的方法
 某些方法尚未實作文字緩衝區配接器、 文字檢視配接器，以及文字層配接器。

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
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> 實作的介面卡，但忽略大綱的 ui。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> 實作的介面卡，但忽略大綱的 ui。|