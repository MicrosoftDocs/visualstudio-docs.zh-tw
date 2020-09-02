---
title: 常見控制項模式
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd2b2723a5ecfe66e9471cfea1e8eb55ed7ced59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547442"
---
# <a name="common-control-patterns-for-visual-studio"></a>適用於 Visual Studio 的通用控制項模式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> 通用控制項

### <a name="overview"></a>概觀
 通用控制項是 Visual Studio 中大部分的使用者介面。 Visual Studio 介面中使用的最常見控制項應遵循 [Windows 桌面互動指導方針](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)。 這份檔是 Visual Studio 特有的，並涵蓋加強這些 Windows 指導方針的特殊情況或詳細資料。

#### <a name="common-controls-in-this-topic"></a>本主題中的通用控制項

- [杆](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [輸入欄位](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [下拉式方塊和下拉式清單](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [核取方塊](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [選項按鈕](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [群組框架](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [文字控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [按鈕和超連結](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [樹狀檢視](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>視覺樣式
 設定控制項樣式時要考慮的第一件事，就是控制項是否會在主題的 UI 中使用。 標準 UI 中的控制項是不具有主題的 UI，而且必須遵循 [一般的 Windows 桌面樣式](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx)，這表示它們不會重新樣板化，而且應該會出現在其預設控制面板中。

- **標準 (公用程式) 對話方塊：** 未主題。 請勿重新範本。 使用基本控制項樣式的預設值。

- **工具視窗、檔編輯器、設計介面和主題對話方塊：** 使用色彩服務來使用特殊主題外觀。

### <a name="scrollbars"></a><a name="BKMK_Scrollbars"></a> 杆
 捲軸應該遵循 [Windows 捲軸的一般互動模式](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) ，除非它們是以內容資訊（例如在程式碼編輯器中）擴充。

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> 輸入欄位
 針對一般互動行為，請依照 [文字方塊的 Windows 桌面指導方針](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx)操作。

#### <a name="visual-style"></a>視覺樣式

- 輸入欄位不應該在公用程式對話方塊中設計樣式。 使用控制項的基本樣式內建函式。

- 主題輸入欄位只能在主題對話方塊和工具視窗中使用。

#### <a name="specialized-interactions"></a>特殊化互動

- 唯讀欄位將會有灰色 (停用) 背景，但預設 (active) 前景。

- 必要欄位的其中應該有 **\<Required>** 浮水印。 除非在罕見的情況下，您不應該變更背景的色彩。

- 錯誤驗證：請參閱 [Visual Studio 的通知和進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- 輸入欄位應該調整大小以符合內容，而不符合顯示視窗的寬度，也不會任意比對長欄位的長度，例如路徑。 如果欄位中允許的字元數目有限制，則長度可能會指出使用者的限制。

     ![不正確的輸入欄位控制項寬度](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")**不正確的輸入欄位長度：名稱不太可能太長。**

     ![正確的輸入欄位控制項寬度](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")**正確的輸入欄位長度：輸入欄位是預期內容的合理寬度。**

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> 下拉式方塊和下拉式清單
 針對一般互動行為，請依照 [下拉式清單和下拉式方塊的 Windows 桌面指導方針](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx)操作。

#### <a name="visual-style"></a>視覺樣式

- 在 [公用程式] 對話方塊中，請勿重新範本控制項。 使用控制項的基本樣式內建函式。

- 在主題 UI 中，下拉式方塊和下拉式清單會依照控制項的標準主題進行。

#### <a name="layout"></a>Layout
 下拉式方塊和下拉式清單應該調整大小以符合內容，而不符合顯示視窗的寬度，也不會完全符合長欄位的長度，例如路徑。

 ![不正確的 drop&#45;down 配置](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")

 **下拉式控制項的欄位長度不正確**

 ![更正 drop&#45;down 配置](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707-04_CorrectDropDownLayout")

 **下拉式控制項的欄位長度正確**

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> 核取方塊
 如需一般的互動行為，請依照 [核取方塊的 Windows 桌面指導方針](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx)操作。

#### <a name="visual-style"></a>視覺樣式

- 在 [公用程式] 對話方塊中，請勿重新範本控制項。 使用控制項的基本樣式內建函式。

- 在主題 UI 中，核取方塊會遵循控制項的標準主題。

#### <a name="specialized-interactions"></a>特殊化互動

- 與核取方塊的互動絕對不能彈出對話方塊或流覽至另一個區域。

- 將核取方塊與第一行文字的基準對齊。

     ![不正確的核取方塊對齊](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")**不正確的核取方塊對齊：核取方塊是在文字的中央。**

     ![正確的核取方塊對齊](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")**正確的核取方塊對齊：核取方塊與第一行文字的基線對齊。**

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> 選項按鈕
 若為一般的互動行為，請依照 [Windows 桌面指導方針來進行選項按鈕](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx)。

#### <a name="visual-style"></a>視覺樣式
 在公用程式對話方塊中，請勿將選項按鈕樣式。 使用控制項的基本樣式內建函式。

#### <a name="specialized-interactions"></a>特殊化互動
 不需要使用群組框架來括住廣播選項。

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> 群組框架
 針對一般互動行為，請依照 [群組框架的 Windows 桌面指導方針](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx)操作。

#### <a name="visual-style"></a>視覺樣式
 在公用程式對話方塊中，請勿將群組框架樣式。 使用控制項的基本樣式內建函式。

#### <a name="layout"></a>Layout

- 除非您需要在嚴密的版面配置中維護群組的差異，否則不需要使用群組框架來括住單選選擇。

- 請勿將群組框架用於單一控制項。

- 有時可以接受使用水準規則，而不是群組框架容器。

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> 文字控制項

### <a name="labels"></a>標籤

#### <a name="active-label-state"></a>作用中標籤狀態

##### <a name="utility-standard-dialogs"></a>公用程式 (標準) 對話方塊) 

- 一般情況下，請遵循 Windows 桌面的控制項標籤指引。

- 在 [公用程式] 對話方塊中，標籤在標準環境的字型和文字色彩中應該會顯示為非粗體。 請參閱 [Visual Studio 的字型和格式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)。

- 省略號應一律遵循標籤。

##### <a name="signature-themed-dialogs"></a>簽名 (主題) 對話方塊) 
 標籤控制項可能是粗體或淺灰色。

#### <a name="disabled-label-state"></a>停用標籤狀態
 標籤應該會反映與其相關聯之控制項的外觀。 例如，如果關聯的控制項已停用，則標籤應該會顯示為灰色並停用。 這通常是由 OS 處理，不需要進行特殊處理。

#### <a name="dynamic-labels"></a>動態磁碟區標
 動態磁碟區標會根據目前的選取專案而變更。 可能的話，請在主版/詳細資料版面配置中使用動態磁碟區標，以協助使用者瞭解顯示的資訊與特定選取專案相關，而不是一般資訊。

 ![搭配動態內容使用的動態標籤](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702-01_DynamicLabel")

 **搭配動態內容使用的動態磁碟區標範例**

#### <a name="instructional-text"></a>教學文字
 某些介面元素可從教學文字中獲益，以協助使用者瞭解 UI 用途，或指出所要採取的動作。

- 教學文字最常用於對話方塊頂端，但可以出現在其他區域中，以將指令提供給複雜的控制項群組。

- 解說文字並非互動式的，但可能包含說明主題的超連結。

- 在需要時，請謹慎使用解說文字。

##### <a name="formatting"></a>格式化
 教學文字應為環境字型、標準 (非主題) 控制項文字。 請參閱 [Visual Studio 的字型和格式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)。

 如需撰寫解說文字的詳細資訊，請參閱 [UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。

 ![說明文字格式設定](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702-02_InstructionalTextFormatting")

 **Visual Studio 對話方塊中的解說文字**

#### <a name="informational-text"></a>資訊文字
 資訊文字是提供使用者其他資訊的文字。 它可能是靜態或動態，或用作通知。 它一律是唯讀的，但如果使用者可以複製資訊，則應該將動態文字放在控制項容器中，例如唯讀文字欄位中。

##### <a name="dynamic-context-specific-text"></a>動態 (內容特定的) 文字
 動態資訊文字會根據內容而變更，例如當使用者切換焦點時。 動態內容通常（但不一定）會與動態磁碟區標配對。

 ![動態資訊文字](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702-03_InformationalDynamicText")

 **動態資訊文字會根據內容而變更。**

##### <a name="formatting"></a>格式化
 有兩種方式可以顯示唯讀文字欄位：直接在 UI 介面上 (查看上述) 或包含在另一個控制項中（例如，群組框架或文字方塊）。 視情況而定，兩者都是正確的。 它是由功能設計工具決定如何呈現唯讀資訊。

 文字可以在唯讀的文字方塊內。 這通常表示可以選取和複製內容，但無法編輯內容。

 ![唯讀&#45;欄位的資訊文字格式設定](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702-04_InformationalFormatting")

 **唯讀欄位的資訊文字格式設定**

#### <a name="watermarks"></a>浮水印
 雖然措辭可能相同，浮水印和解說文字之間的差異在於，當控制項/視窗不是空的時，浮水印會以內容取代，而且教學文字會隨時保持可見。

 當視窗或控制項為空白時，應使用浮水印。 它們表示需要完成才能填入區域，而且可能包含開啟相關視窗的動作連結，例如拖曳來源。

##### <a name="visual-style"></a>視覺樣式

- 浮水印應該在視窗內水準置中。

- 浮水印應該靠左對齊，而不是靠左對齊。

- 浮水印可能會垂直置中或置於區域頂端附近。 如果位於接近區域頂端的位置，則必須有足夠的空間，才能讓水位線出現。

- 使用 [ `Environment.GrayText` 色彩標記] 和 [標準環境] 字型。 超連結應使用標準超連結共用標記： `Environment.PanelHyperlink` 、 `Environment.PanelHyperlinkHover` 、 `Environment.PanelHyperlinkPressed` 和 `Environment.PanelHyperlinkDisabled` 。

- 無法在背景選取浮水印

- 可能的話，請在浮水印中包含連結，以協助使用者開始使用。

  ![設計工具視窗中的浮水印文字](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702-05_Watermark1")

  ![工具視窗中的浮水印文字](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702-06_Watermark2")

  **Visual Studio 中的浮水印文字範例**

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> 按鈕和超連結

### <a name="overview"></a>概觀
 按鈕和連結控制項 (超連結) 應遵循使用方式、用語、調整大小和間距之 [超連結的基本 Windows 桌面指南](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) 。

### <a name="choosing-between-buttons-and-links"></a>選擇按鈕和連結
 傳統上，按鈕已用於動作，而超連結已保留供導覽之用。 按鈕可以在所有情況下使用，但連結的角色已在 Visual Studio 中展開，因此在某些情況下，按鈕和連結可互換。

 使用命令按鈕的時機：

- 主要命令

- 顯示用來收集輸入或進行選擇的視窗，即使它們是次要命令

- 破壞性或無法復原的動作

- 在嚮導和頁面流程內的承諾按鈕

  避免在工具視窗中的命令按鈕，或者，如果您的標籤需要兩個以上的字組。 連結可以有較長的標籤。

  使用連結的時機：

- 導覽至另一個視窗、檔或網頁

- 需要較長的標籤或簡短句子來描述動作意圖的情況

- 如果動作不具破壞性或無法復原，則按鈕會讓 UI 過度負荷的緊密空間

- 在有許多命令的情況下，取消強調次要命令

#### <a name="examples"></a>範例
 ![追蹤狀態訊息的資訊列命令連結](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703-01_CommandLinkInfobar")

 **資訊列中用於狀態訊息的命令連結**

 ![CodeLens 快顯視窗中所使用的連結](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703-02_LinksInCodeLens")

 **CodeLens 快顯視窗中所使用的連結**

 ![做為次要命令使用的連結](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")

 **用於次要命令的連結，其中按鈕會吸引太多注意力**

### <a name="common-buttons"></a>一般按鈕

#### <a name="text"></a>Text
 遵循 [UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)中的寫作指導方針。

#### <a name="visual-style"></a>視覺樣式

##### <a name="standard-dialogs"></a>標準對話
 Visual Studio 中的大部分按鈕會出現在標準對話方塊中，不應進行樣式。 它們應該會反映依作業系統規定之按鈕的標準外觀。

##### <a name="themed"></a>主題
 在某些情況下，按鈕可能會在已樣式的 UI 中使用，而這些按鈕必須適當地設計樣式。 如需主題控制項的詳細資訊，請參閱 [對話方塊](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) 。

### <a name="special-buttons"></a>特殊按鈕

#### <a name="browse-buttons"></a>流覽。。。 按鈕
 **[流覽 ...]** 按鈕用於方格、對話方塊和工具視窗，以及其他無模式 UI 元素。 它們會顯示選擇器，協助使用者將值填入控制項。 這個按鈕有兩種變化： long 和 short。

 ![長 &#91;流覽 ... &#93; 按鈕](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703-04_BrowseLong")

 **完整的 [流覽 ...] 按鈕**

 ![簡短省略號&#45;只 &#91;流覽 ... &#93; 按鈕](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703-05_BrowseShort")

 **僅省略號的簡短 [...] 按鈕**

 使用僅限省略號的簡短按鈕：

- 如果對話方塊中有一個以上的長 **[流覽 ...]** 按鈕，例如當有數個欄位允許流覽時。 針對每個使用 **[...]** 按鈕，以避免此情況所建立的令人困惑的存取金鑰 (在相同對話方塊) 中 **&流覽** 和 **B&流覽) ** 。

- 在嚴密的對話中，或沒有適當的位置來放置長按鈕時。

- 如果按鈕會出現在方格控制項中。

  使用按鈕的指導方針：

- 請勿使用存取金鑰。 若要使用鍵盤來存取它，使用者必須在連續的控制項中使用 tab 鍵。 確定定位順序是讓任何瀏覽按鈕緊接在其填滿的欄位之後。 絕對不要在第一個期間使用底線。

- 將 Microsoft Active Accessibility (MSAA) **名稱** ] 屬性設定為 **[流覽 ...]** (包含省略號) ，讓螢幕讀取器將其讀取為「流覽」，而不是「點點-點」或「期間期間」。 針對 managed 控制項，這表示設定 **AccessibleName** 屬性。

- 絕對不要使用省略號 **[...]** 按鈕進行流覽動作以外的任何動作。 例如，如果您需要 **[新增 ...]** 按鈕，但沒有足夠的空間來容納文字，則必須重新設計對話方塊。

##### <a name="sizing-and-spacing"></a>調整大小和間距
 ![調整 &#91;流覽 ... &#93; 按鈕](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703-06_BrowseSizing")

 **調整 [流覽 ...] 按鈕的大小**

 ![&#91;流覽 ... &#93; 按鈕的間距](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703-07_BrowseSpacing")

 **間距 [流覽 ...] 按鈕**

#### <a name="graphical-buttons"></a>圖形按鈕
 有些按鈕應該一律使用圖形影像，而且永遠不會包含文字來節省空間並避免當地語系化問題。 這些通常用於欄位選擇器和其他可排序清單。

> [!NOTE]
> 使用者必須索引標籤至這些按鈕 (沒有) 的存取金鑰，因此請以合理的順序放置它們。 將按鈕的 [名稱] 屬性對應到所採取的動作，讓螢幕讀取器正確地解讀按鈕動作。

|Name|Image|
|-|-|
|加|![圖形 [加入] 按鈕](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703-08_ButtonAdd")|
|移除|![圖形 [移動] 按鈕](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703-09_ButtonRemove")|
|加入全部|![圖形 [全部加入] 按鈕](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703-10_ButtonAddAll")|
|全部移除|![圖形 [全部移除] 按鈕](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703-11_ButtonRemoveAll")|
|上移|![圖形 [上移] 按鈕](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703-12_ButtonMoveUp")|
|下移|![圖形 [下移] 按鈕](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703-13_ButtonMoveDown")|
|刪除|![圖形 [刪除] 按鈕](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703-14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>調整大小和間距
 圖形按鈕的大小調整與 **[流覽 ...]** 按鈕的簡短版本相同 (26x23 圖元) ：

 ![顯示和不顯示透明色彩的按鈕](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")

 **按鈕上圖形影像的外觀，顯示和不顯示透明色彩**

### <a name="hyperlinks"></a>超連結
 超連結很適合以導覽為基礎的動作，例如開啟說明主題、強制回應對話方塊或 wizard。 如果有用於命令的超連結，則應該一律顯示 UI 的可見和明顯變更。 一般來說，認可至動作 (例如儲存、取消和刪除) 的動作，會使用按鈕進行較佳的通訊。

#### <a name="writing-style"></a>撰寫樣式
 遵循 [Windows 桌面的使用者介面文字指引](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)。 請勿使用「深入瞭解」、「告訴我更多資訊」或「取得此措辭的協助」。 相反地，片語說明會以說明內容所回答的主要問題為依據來連結文字。 例如，「**如何? 將伺服器新增至伺服器總管？**」

#### <a name="visual-style"></a>視覺樣式

- 超連結應該一律使用 [VSColor 服務](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。 如果超連結的樣式不正確，則會在作用中或在造訪之後顯示不同的色彩時閃爍紅色。

- 請勿在控制項停留狀態包含底線，除非連結是完整句子中的句子片段，例如浮水印。

- 停留時不應顯示底線。 相反地，對使用者而言，連結為作用中的意見反應是稍微改變的色彩，以及適當的連結游標。

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> 樹狀檢視

### <a name="overview"></a>概觀
 樹狀檢視可讓您將複雜清單組織成父子式群組。 使用者可以展開或折迭父群組，以顯示或隱藏基礎子專案。 您可以選取樹狀檢視中的每個專案，以提供進一步的動作。

 本主題涵蓋樹狀檢視的可接受使用、適當的設計和功能。

#### <a name="in-this-topic"></a>本主題內容

- [視覺化樣式](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [互動](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> 視覺化樣式

#### <a name="expanders"></a>展開器
 樹狀檢視控制項應該符合 Windows 和 Visual Studio 所使用的擴充項設計。 每個節點都會使用展開器控制項來顯示或隱藏基礎專案。 使用擴充器控制項可為可能在 Windows 和 Visual Studio 中遇到不同樹狀檢視的使用者提供一致性。

 ![正確的樹狀檢閱控制項](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **更正：使用展開器控制項之樹狀檢視節點的適當樣式**

 ![不正確的樹狀檢閱節點](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705-2_TreeViewIncorrect1")

 **不正確：樹狀檢視節點的不適當樣式**

#### <a name="selection"></a>選取
 當您在樹狀檢視內選取節點時，反白顯示應該會擴充至樹狀檢視控制項的全形。 這可協助使用者清楚地識別他們所選取的專案。 選取色彩應該會反映目前的 Visual Studio 主題。

 ![正確的樹狀檢閱控制項](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **正確：反白顯示選取的節點符合整個樹狀檢視控制項的寬度。**

 ![不正確的樹狀檢閱反白顯示](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705-3_TreeViewIncorrect2")

 **不正確：反白顯示選取的節點無法容納整個樹狀檢視控制項的寬度。**

#### <a name="icons"></a>圖示
 如果圖示有助於以視覺化方式識別專案之間的差異，則應該只在樹狀檢視控制項中使用。 一般情況下，圖示只能用在不同的清單中，這些圖示會攜帶資訊來區分專案類型。 在使用圖示的同質清單中，經常會看到雜訊，應予以避免。 在這種情況下， (父) 的群組圖示可以傳達內的專案類型。 這項規則的例外狀況是，如果圖示為動態，而且是用來表示狀態。

#### <a name="scroll-bars"></a>捲軸
 如果內容適用于樹狀檢視控制項，則應該一律隱藏捲軸。 捲軸可接受隱藏，或是可滾動視窗中的半透明，並且在包含樹狀檢視的視窗具有焦點，或在樹狀檢視本身停留時出現。

 ![含捲軸的樹狀結構檢視](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705-4_Scrollbars")

 **垂直和水準捲軸會顯示，因為內容已超過樹狀檢視控制項的限制。**

### <a name="interactions"></a><a name="BKMK_TreeViewInteractions"></a> 相互 作用

#### <a name="context-menus"></a>操作功能表
 樹狀檢視節點可顯示內容功能表中的子功能表選項。 一般來說，當使用者以滑鼠右鍵按一下專案，或按下 Windows 鍵盤上的功能表鍵並選取專案時，就會發生這種情況。 節點必須獲得焦點並選取。 這可協助使用者識別子功能表所屬的專案。

 ![選取的樹狀節點和內容功能表](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705-5_CoNtextMenu")

 **已產生內容功能表的專案會取得焦點，以通知使用者已選取哪一個專案。**

#### <a name="keyboard"></a>鍵盤
 樹狀檢視應提供使用鍵盤選取專案和展開/折迭節點的功能。 這可確保導覽符合我們的協助工具需求。

##### <a name="tree-view-control"></a>樹狀檢視控制項
 Visual Studio 樹狀目錄控制項應遵循一般鍵盤導覽：

- **向上箭號：** 藉由向上移動樹狀結構來選取專案

- **向下箭號：** 藉由向下移動樹狀結構來選取專案

- **向右箭號：** 展開樹狀結構中的節點

- **向左箭號：** 折迭樹狀結構中的節點

- **輸入金鑰：** 起始、載入、執行選取的專案

##### <a name="trid-tree-view-and-grid-view"></a>Trid (樹狀檢視和方格視圖) 
 Trid 控制項是包含方格內樹狀檢視的複雜控制項。 展開、折迭和流覽樹狀結構應該與樹狀檢視採用相同的鍵盤命令，並具有下列新增專案：

- **向右箭號：** 展開節點。 展開節點之後，應繼續導覽至右邊最接近的資料行。 導覽應該會在資料列的結尾處停止。

- **Tab：** 導覽至右邊最接近的儲存格。  在資料列的結尾，導覽會繼續前往下一個資料列。

- **Shift + Tab：** 導覽至左側最接近的儲存格。  在資料列的開頭，導覽會繼續前往上一個資料列中最右邊的儲存格。

  ![Visual Studio 中的 Trid 控制項](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705-6_Trid")

  **Visual Studio 中的 trid 控制項**
