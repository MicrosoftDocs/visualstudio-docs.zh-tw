---
title: 視覺工作室的常見控制模式 |微軟文件
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5a1904c01f5688a00e45de7feed7ae326d9b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698706"
---
# <a name="common-control-patterns-for-visual-studio"></a>適用於 Visual Studio 的通用控制項模式
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>常見控制項

### <a name="overview"></a>概觀
常見控件占可視化工作室中用戶介面的大多數。 視覺化工作室介面中使用的大多數常見控制項應遵循[Windows 桌面互動指南](/windows/desktop/uxguide/controls)。 本主題特定於 Visual Studio,並介紹增強這些 Windows 指南的特殊情況或詳細資訊。

#### <a name="common-controls-in-this-topic"></a>本主題中的常見控制項

- [捲動條圖](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [輸入欄位](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [組合框與下拉清單](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [核取方塊](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [點選按鈕](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [組幀](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [文字控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [按鈕與超連結](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [樹狀檢視](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>視覺樣式
樣式控件時首先要考慮的是控件是否將在主題 UI 中使用。 標準 UI 中的控制項是非主題 UI,必須遵循[正常的 Windows 桌面樣式](/windows/desktop/uxguide/controls),這意味著它們不會重新範本化,並且應出現在其預設控制元件外觀中。

- **標準(實用程式)對話方塊:** 非主題對話方塊。 不要重新範本化。 使用基本控制樣式預設值。

- **工具視窗、文件編輯器、設計曲面和主題對話框:** 使用彩色服務使用專門的主題外觀。

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a>捲動條圖
 滾動條應遵循[Windows 滾動欄的常見交互模式](/windows/desktop/Controls/about-scroll-bars),除非它們包含內容資訊(如代碼編輯器中)。"

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>輸入欄位
 對於典型的互動行為,請遵循[文字框的 Windows 桌面指南](/windows/desktop/uxguide/ctrl-text-boxes)。

#### <a name="visual-style"></a>視覺樣式

- 輸入欄位不應在實用程式對話框中設置樣式。 使用控件固有的基本樣式。

- 主題輸入欄位應僅用於主題對話框和工具視窗。

#### <a name="specialized-interactions"></a>專業互動

- 唯讀欄位將具有灰色(禁用)背景,但預設(活動)前景。

- 所需的欄位應具有**\<所需的>** 作為浮浮浮水印。 除非在極少數情況下,否則不應更改背景的顏色。

- 錯誤驗證:請參閱[可視化工作室的通知和進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- 輸入欄位的大小應適合內容,而不是適合顯示它們的視窗的寬度,也不應任意匹配長欄位的長度(如路徑)。 長度可能向使用者指示欄位中允許的字元數的限制。

     ![輸入欄位長度不正確:名稱不太可能長。](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />輸入欄位長度不正確:名稱不太可能長。

     ![正確的輸入欄位長度:輸入欄位是預期內容的合理寬度。](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />正確的輸入欄位長度:輸入欄位是預期內容的合理寬度。

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>組合框與下拉清單
對於典型的交互行為,請遵循[Windows 桌面指南,查看下拉列表和組合框](/windows/desktop/uxguide/ctrl-drop)。

#### <a name="visual-style"></a>視覺樣式

- 在實用程式對話方塊中,不要重新範本控制項。 使用控件固有的基本樣式。

- 在主題 UI 中,組合框和下拉清單遵循控制項的標準主題。

#### <a name="layout"></a>配置
組合框和下拉清單的大小應適合內容,不適合顯示它們的視窗的寬度,也不必像路徑一樣任意匹配長欄位的長度。

![不正確:下拉寬度太長,無法顯示內容。](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />不正確:下拉寬度太長,無法顯示內容。

![正確:下拉清單的大小允許翻譯增長,但並非不必要地長。](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />正確:下拉清單的大小允許翻譯增長,但並非不必要地長。

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>勾選方塊
對於典型的交互行為,請按照[「Windows 桌面」指南進行複選框](/windows/desktop/uxguide/ctrl-check-boxes)。

#### <a name="visual-style"></a>視覺樣式

- 在實用程式對話方塊中,不要重新範本控制項。 使用控件固有的基本樣式。

- 在主題 UI 中,複選框遵循控制件的標準主題。

#### <a name="specialized-interactions"></a>專業互動

- 與複選框的交互絕不能彈出對話框或導航到其他區域。

- 將複選框與第一行文本的基線對齊。

     ![不正確:複選框以文本為中心。](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />不正確:複選框以文本為中心。

     ![正確:複選框與文本的第一行對齊。](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />正確:複選框與文本的第一行對齊。

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>點選按鈕
對於典型的互動行為,請遵循[Windows 桌面指南進行單選按鈕](/windows/desktop/uxguide/ctrl-radio-buttons)。

#### <a name="visual-style"></a>視覺樣式
在實用程式對話方塊中,不要設置單選按鈕的樣式。 使用控件固有的基本樣式。

#### <a name="specialized-interactions"></a>專業互動
不需要使用組幀來封閉無線電選擇,除非您需要在緊湊的佈局中保持組區分。

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>組幀
對於典型的互動行為,請遵循[組幀的 Windows 桌面指南](/windows/desktop/uxguide/ctrl-group-boxes)。

#### <a name="visual-style"></a>視覺樣式
在實用程序對話方塊中,不要對組框架進行樣式設置。 使用控件固有的基本樣式。

#### <a name="layout"></a>配置

- 不需要使用組幀來封閉無線電選擇,除非您需要在緊湊的佈局中保持組區分。

- 切勿將組幀用於單個控件。

- 有時可以使用水平規則而不是組幀容器。

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>文字控制項

### <a name="static-text-fields"></a>靜態文字欄位

靜態文字欄位顯示唯讀資訊,使用者無法選擇。 避免將其用於使用者可能想要複製到剪貼簿的任何文本。 但是,唯讀靜態文本可以更改以反映狀態的變化。 在下面的示例中,「資訊」群組下的「輸出名稱」靜態文本將更改以反映對它上方的根命名空間文本框所做的任何更改。

有兩種方法可以顯示靜態文本資訊。

當不存在分組衝突時,靜態文本可以在對話框中自行顯示,沒有任何包含。 確定是否確實有必要使用框的額外行。 例如,在組行創建的節下顯示目錄路徑,如下所示:

![文字控制器中的靜態文字資訊](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "顯示靜態文字.png")<br />文字控制器中的靜態文字資訊

在存在其他分組區域的對話框中,資訊包含將有助於可讀性,並且當可以隱藏或顯示節(如 **"屬性"視窗**描述窗格中)或希望與類似 UI 保持一致時,將靜態文本放在框中。 此組框應為單一規則,並帶有以下`ButtonShadow`顏色:

![屬性屬性視窗中的靜態文字](../../extensibility/ux-guidelines/media/PropertiesWindow.png "屬性視窗.png")<br />屬性屬性視窗中的靜態文字

### <a name="read-only-text-box"></a>唯讀文字盒

這允許用戶選擇欄位中的文本,但不能編輯它。 這些文本框與通常的 3D 鑿子接壤,`ButtonShadow`帶有 填充。

當使用者更改關聯的控制項(如選中/取消選中複選框或選擇/取消選擇單選按鈕)時,文本框可能會變為活動(可編輯)。 例如,在下面顯示**的&gt;「工具選項**」頁中,「**主頁」文字**框在取消選中 **「使用預設**」選選框時變為活動狀態。

![唯讀文字盒,顯示非作用狀態與作用狀態](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "閱讀唯一文字盒.png")<br />唯讀文字盒,顯示非作用狀態與作用狀態

### <a name="using-text-in-dialogs"></a>在對話框中使用文字

對話框中文字的關鍵準則:

- 文字框、清單框和框架的標籤在非主題對話框中以動詞開頭,僅對第一個單詞具有初始大寫,以冒號結尾。

    > 主題對話框中的文字控件遵循[Windows 桌面 UX 準則](/windows/desktop/uxguide/top-violations),不採用結束標點符號,但幫助連結中的問號除外。

- 複選方塊和選項按鈕的標籤以動詞開頭,第一個單詞的初始大寫字母,並且沒有結束標點符號。

- 按鈕、功能表、功能表項和選項卡的標籤在每個單詞(標題大小寫)上都有初始大寫字母。

- 標籤術語應與其他對話框中的類似標籤一致。

- 如果可能,請讓編寫器/編輯器在文本提交開發人員進行實現之前編寫或批准該文本。

- 所有控件都應具有標籤,除非在選項卡已足夠的特殊情況下。
在適當時使用幫助器文本。

### <a name="helper-text"></a>說明者文字

包含在對話方塊中,以説明使用者瞭解對話方塊的用途或指示要執行的操作。 僅當需要時才應使用幫助器文本,以避免使簡單對話框變得雜亂無章。 幫助器文本的兩種變體是對話框和浮浮浮水印。

遵循幫助器文本的常見位置,並選擇性地引入新區域。 說明器文字的常見方案包括:

- 對話框中的幫助器文本,以提供有關如何與複雜對話方塊互動的其他方向。

- 在空工具視窗或對話框中為文本加水印,以解釋為什麼沒有內容可見。

- 描述窗格,如 **"屬性"視窗**的底部。

- 在空編輯器中添加浮浮浮水印文本,以解釋用戶應該採取哪些操作來開始。

### <a name="dialog-helper-text"></a>對話方塊 Helper 文字

用戶體驗設計器可以幫助確定幫助器文本何時合適。 設計器可以定義幫助器文本的顯示位置及其一般內容。 用戶幫助可以編寫/編輯實際文本。

### <a name="watermarks"></a>浮水印

對話框受益於略有不同的浮浮水印準則。 由於對話框可能顯示許多 UI 元素(標籤、提示文本、按鈕和其他包含文本的容器控制項),因此,尤其是當這些控制項以黑色顯示時,浮浮浮水印在深`ButtonShadow`灰色(VSColor: ) 中效果更好。 通常,水印出現在控件內,就像帶有白色背景的列表框 (VSColor: `Window`)。

- 文字以深灰色顯示 (VSColor: `ButtonShadow`)。 但是,如果水印出現在中等灰色或其他顏色 (VSColor: `ButtonFace`) 背景上,並且擔心其可讀性,請使用黑色文本`WindowText`(VSColor: )。

- 水印可以居中或向左刷新。 在做出對齊決策時應用標準設計規則。 無法在背景上選擇浮浮浮水印。

![水印文字範例](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />水印文字範例

### <a name="context-specific-dynamic-text"></a>特定於上下文(動態)的文字

動態文本可以在對話方塊或無模式 UI 中使用兩種方式之一:作為動態標籤或動態內容。

- 動態標籤:動態文本的常見用在描述性面板中,這些面板為所選專案提供了更多資訊,例如,在對話框中,其中包含顯示在右側網格中的元素和屬性的清單。 屬性格格的標籤可能是動態的,因此當在左側選擇專案時,右側的網格將顯示該特定項的資訊。

- 動態文本:在需要以這種方式顯示特定資訊而不是常規資訊的情況下非常有用,但應注意不要過度使用。

如果希望用戶能夠複製資訊,則動態文本應位於唯讀文本欄位中。

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>按鈕與超連結

### <a name="overview"></a>概觀
按鈕和連結控制項(超連結)應遵循[有關超連結的基本 Windows 桌面指南](/windows/desktop/uxguide/ctrl-links),以便進行使用、措辭、大小調整和間距。

### <a name="choosing-between-buttons-and-links"></a>在按鈕與連結之間進行選擇
傳統上,按鈕已用於操作,超連結已保留用於導航。 按鈕可用於所有情況,但連結的角色已在 Visual Studio 中擴展,以便在某些情況下,按鈕和連結更容易互換。

何時使用指令按鈕:

- 主要命令

- 顯示用於收集輸入或做出選擇的視窗,即使它們是協助命令

- 破壞性或不可逆轉的行動

- 匯及頁面串流的承諾按鈕

避免在工具視窗中出現命令按鈕,或者需要標籤的單詞超過兩個單詞。 連結可以具有較長的標籤。

 何時使用連結:

- 瀏覽到其他視窗、文件或網頁

- 需要較長的標籤或短句來描述行動意圖的情況

- 按鈕將淹沒 UI 的狹小空間,前提是該操作不具有破壞性或不可逆性

- 在存在許多指令的情況下取消強調輔助命令

#### <a name="examples"></a>範例
![狀態訊息後資訊列中使用的命令連結](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />狀態訊息後資訊列中使用的命令連結

![CodeLens 快顯視窗中所使用的連結](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />CodeLens 快顯視窗中所使用的連結

![用於次要命令的連結,其中按鈕會吸引太多注意力](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />用於次要命令的連結,其中按鈕會吸引太多注意力

### <a name="common-buttons"></a>常用按鈕

#### <a name="text"></a>Text
遵循[UI 文本和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)中的編寫指南。

#### <a name="visual-style"></a>視覺樣式

##### <a name="standard-unthemed"></a>標準(無主題)
Visual Studio 中的大多數按鈕將顯示在實用程式對話方塊中,不應設置樣式。 它們應反映操作系統規定的按鈕的標準外觀。

##### <a name="themed"></a>主題
在某些情況下,可以在樣式的 UI 中使用按鈕,並且這些按鈕必須正確設置樣式。 有關主題控制件的資訊[,請參閱對話框](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)。

### <a name="special-buttons"></a>特殊按鈕

#### <a name="browse-buttons"></a>流覽。。。按鈕
**[流覽...]** 按鈕用於網格、對話框、工具視窗以及其他無模式 UI 元素。 它們顯示一個選取器,可幫助使用者將值填充到控制項中。 此按鈕有兩種變體,長和短。

![長 [瀏覽...] 按鈕](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />長 [瀏覽...] 按鈕

![僅省略號短 [...] 按鈕](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />僅省略號短 [...] 按鈕

何時使用只有橢圓短按鈕:

- 如果對話框中有多個長 **[Browse... ] 按鈕**,例如多個字段允許流覽時。 使用每個短 **[...]** 按鈕,以避免此情況創建的混亂訪問密鑰 **(&瀏覽**和 B **&行**在同一對話方塊)。

- 在緊密對話框中,或者當沒有合理位置放置長按鈕時。

- 如果按鈕將顯示在網格控制項中。

使用按鈕的指南:

- 不要使用訪問金鑰。 要使用鍵盤訪問它,用戶必須從相鄰控件選項卡。 確保選項卡順序使任何瀏覽按鈕在將填充的欄位之後立即落下。 切勿在第一個期間下方使用下劃線。

- 將 Microsoft 活動輔助功能 (MSAA)**名稱**屬性設置為 **「流覽..."(** 包括省略號),以便螢幕閱讀器將其讀取為「瀏覽」,而不是「點點」或「週期週期」。 對於托管控件,這意味著設置 **「可訪問名稱」** 屬性。

- 切勿對除流覽操作以外的任何內容使用省略**號 [...]** 按鈕。 例如,如果您需要 **[New...]** 按鈕,但沒有足夠的空間用於文本,則需要重新設計對話方塊。

##### <a name="sizing-and-spacing"></a>大小調整與間距
![大小調整 [瀏覽... ] 按鈕:標準版本為 75x23 像素,短版本為 26x23 圖元](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />調整 [瀏覽...] 按鈕的大小

![間距 [瀏覽...] 按鈕:相關控制項和標準流覽按鈕 7 像素之間的間距,相關控制項和短流覽按鈕之間的間距 5 像素](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />調整 [瀏覽...] 按鈕的間距

#### <a name="graphical-buttons"></a>圖形按鈕
某些按鈕應始終使用圖形圖像,並且絕不包含文本以節省空間並避免本地化問題。 這些通常用於欄位選取器和其他可排序列表。

> [!NOTE]
> 用戶必須選項卡到這些按鈕(沒有訪問鍵),所以將它們按合理的順序排列。 將`name`按鈕的屬性映射到它所執行的操作,以便螢幕閱讀器正確解釋按鈕操作。

| 函式 | 按鈕 |
| --- | --- |
| 加 | ![圖形 [加入] 按鈕](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| 移除 | ![圖形 [移動] 按鈕](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| 加入全部 | ![圖形 [全部加入] 按鈕](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| 全部移除 | ![圖形 [全部移除] 按鈕](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| 上移 | ![圖形 [上移] 按鈕](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| 下移 | ![圖形 [下移] 按鈕](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| 刪除 | ![圖形 [刪除] 按鈕](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>大小調整與間距
圖形按鈕的尺寸與 **[Browse...]** 按鈕(26x23 像素)的簡短版本相同:

![按鈕上的圖形影像的外觀,帶透明顏色顯示,不顯示透明顏色](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />按鈕上的圖形影像的外觀,帶透明顏色顯示,不顯示透明顏色

### <a name="hyperlinks"></a>超連結
超連結非常適合基於導航的操作,例如打開説明主題、模式對話方塊或嚮導。 如果用於命令的超連結,它應始終顯示對 UI 的可見且明顯的更改。 通常,最好使用按鈕傳達提交操作的操作(如保存、取消和刪除)。

#### <a name="writing-style"></a>撰寫樣式
依[Windows 桌面指南進行使用者介面文字](/windows/desktop/uxguide/text-ui)。 不要使用"瞭解更多","告訴我更多關於"或"獲取有關此説明"的短語。 相反,短語"説明"會連結文本,以表示幫助內容回答的主要問題。 例如,"**如何向伺服器資源管理器添加伺服器?"**

#### <a name="visual-style"></a>視覺樣式

- 超連結應永遠使用[VSColor 服務](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。 如果超鏈接的樣式不正確,則在啟動時閃爍紅色,或在訪問后顯示其他顏色。

- 除非連結是完整句子中的句子片段(如浮浮浮水印中)中,否則不要在控件靜止狀態處包含下劃線。

- 下劃線不應顯示在懸停上。 相反,向用戶反饋的鏈接處於活動狀態是輕微的顏色變化和相應的連結游標。

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>樹狀圖

樹視圖提供了一種將複雜列表組織到父子組的方法。 用戶可以展開或摺疊父組以顯示或隱藏基礎子項。 可以選擇樹視圖中的每個項以提供進一步操作。

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>樹視圖視覺樣式

#### <a name="expanders"></a>擴充器
樹視圖控件應符合 Windows 和可視化工作室使用的擴展程式設計。 每個節點使用擴展器控制項來顯示或隱藏基礎項。 使用延伸器控制項為在 Windows 和 Visual Studio 中遇到不同樹視圖的使用者提供一致性。

![正確:使用延伸器控制元件正確設定樹檢視節點樣式](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />正確:使用延伸器控制元件正確設定樹檢視節點樣式

![不正確:樹檢視節點的樣式不正確](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />不正確:樹檢視節點的樣式不正確

#### <a name="selection"></a>選取項目
在樹視圖中選擇節點時,高光應擴展到樹視圖控件的完整寬度。 這有助於使用者清楚地識別他們選擇了哪些專案。 選擇顏色應反映當前視覺工作室主題。

![正確:所選節點的高光適合樹視圖控件的整個寬度。](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />正確:所選節點的高光適合樹視圖控件的整個寬度。

![不正確:所選節點的高光不適合樹視圖控件的整個寬度。](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />不正確:所選節點的高光不適合樹視圖控件的整個寬度。

#### <a name="icons"></a>圖示
僅當圖示有助於直觀地識別項之間的差異時,才應在樹視圖控件中使用圖示。 通常,圖示應僅在異構清單中使用,其中圖示攜帶資訊以區分元素的類型。 在使用圖示的同質清單中通常可以被視為雜訊,應避免使用圖示。 在這種情況下,組圖示(父圖示)可以傳達其中的項目類型。 此規則的例外情況是,如果圖示是動態的,並且用於指示狀態。

#### <a name="scroll-bars"></a>捲軸
如果內容適合樹視圖控件,應始終隱藏滾動條。 捲動條可以隱藏,或在可滾動視窗中半透明,並在包含樹視圖的視窗具有焦點時或在樹視圖本身的懸停時顯示。

![顯示垂直滾動條和水平滾動條,因為內容已超過樹視圖控件的限制。](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />顯示垂直滾動條和水平滾動條,因為內容已超過樹視圖控件的限制。

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a>樹狀圖互動

#### <a name="context-menus"></a>操作功能表
樹視圖節點可以在上下文菜單中顯示子功能表選項。 通常,當使用者右鍵單擊某個專案或在選擇該專案的情況下按下 Windows 鍵盤上的「功能表」鍵時,將發生這種情況。 節點獲得焦點並被選中非常重要。 這有助於用戶識別子功能表屬於哪個項。

![已生成上下文菜單的項獲得焦點,以通知使用者已選擇哪個項。](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />已生成上下文菜單的項獲得焦點,以通知使用者已選擇哪個項。

#### <a name="keyboard"></a>鍵盤
樹視圖應提供使用鍵盤選擇項和展開/摺疊節點的能力。 這可確保導航滿足我們的輔助功能要求。

##### <a name="tree-view-control"></a>樹狀圖控制項
可視化工作室樹控件應遵循常見的鍵盤導航:

- **向上箭號:** 從移動樹來選擇項目

- **向下箭號:** 以移動樹來選擇項目

- **右箭號:** 展開樹中的節點

- **左箭號:** 折疊樹中的節點

- **輸入鍵:** 啟動、載入、執行選取的項目

##### <a name="trid-tree-view-and-grid-view"></a>Trid(樹檢視和網格檢視)
trid 控件是一種複雜控件,其中包含網格中的樹視圖。 展開、摺疊和導航樹應遵循與樹視圖相同的鍵盤命令,並添加以下內容:

- **右箭號:** 展開節點。 擴展節點后,它應繼續導航到右側最近的列。 導航應在行的末尾停止。

- **選項卡:** 導航到右側最近的單元格。  在行的末尾,導航繼續到下一行。

- **移位 + 選項卡:** 導航到左側最近的單元格。  在行的開頭,導航繼續到上一行中最右側的單元格。

![視覺工作室中的一個三惡維控制](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />視覺工作室中的一個三惡維控制
