---
title: Visual Studio 的通用控制項模式 |Microsoft Docs
description: 瞭解 Visual Studio 通用控制項如何遵循 Windows 桌面互動指導方針，以及加強這些指導方針的特殊情況。
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12d514bdc0aa37598ad57e0466bf57ba75ed2601
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899299"
---
# <a name="common-control-patterns-for-visual-studio"></a>適用於 Visual Studio 的通用控制項模式
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> 通用控制項

### <a name="overview"></a>概觀
通用控制項是 Visual Studio 中大部分的使用者介面。 Visual Studio 介面中使用的最常見控制項應遵循 [Windows 桌面互動指導方針](/windows/desktop/uxguide/controls)。 本主題僅適用于 Visual Studio，並涵蓋加強這些 Windows 指導方針的特殊情況或詳細資料。

#### <a name="common-controls-in-this-topic"></a>本主題中的通用控制項

- [捲軸](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [輸入欄位](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [下拉式方塊和下拉式清單](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [核取方塊](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [選項按鈕](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [群組框架](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [文字控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [按鈕和超連結](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [樹狀檢視](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>視覺樣式
設定控制項樣式時要考慮的第一件事，就是控制項是否會在主題的 UI 中使用。 標準 UI 中的控制項是不具有主題的 UI，而且必須遵循 [一般的 Windows 桌面樣式](/windows/desktop/uxguide/controls)，這表示它們不會重新樣板化，而且應該會出現在其預設控制面板中。

- **標準 (公用程式) 對話方塊：** 未主題。 請勿重新範本。 使用基本控制項樣式的預設值。

- **工具視窗、檔編輯器、設計介面和主題對話方塊：** 使用色彩服務來使用特殊主題外觀。

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> 捲軸
 捲軸應該遵循 [Windows 捲軸的一般互動模式](/windows/desktop/Controls/about-scroll-bars) ，除非它們是使用內容資訊（例如程式碼編輯器）擴充。

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> 輸入欄位
 針對一般互動行為，請依照 [文字方塊的 Windows 桌面指導方針](/windows/desktop/uxguide/ctrl-text-boxes)操作。

#### <a name="visual-style"></a>視覺樣式

- 輸入欄位不應該在公用程式對話方塊中設計樣式。 使用控制項的基本樣式內建函式。

- 主題輸入欄位只能在主題對話方塊和工具視窗中使用。

#### <a name="specialized-interactions"></a>特殊化互動

- 唯讀欄位將會有灰色 (停用) 背景，但預設 (active) 前景。

- 必要欄位的其中應該有 **\<Required>** 浮水印。 除非在罕見的情況下，您不應該變更背景的色彩。

- 錯誤驗證：請參閱 [Visual Studio 的通知和進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- 輸入欄位應該調整大小以符合內容，而不符合顯示視窗的寬度，也不會任意比對長欄位的長度，例如路徑。 如果欄位中允許的字元數目有限制，則長度可能會指出使用者的限制。

     ![輸入欄位長度不正確：名稱不太可能太長。](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />輸入欄位長度不正確：名稱不太可能太長。

     ![正確的輸入欄位長度：輸入欄位是預期內容的合理寬度。](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />正確的輸入欄位長度：輸入欄位是預期內容的合理寬度。

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> 下拉式方塊和下拉式清單
針對一般互動行為，請依照 [下拉式清單和下拉式方塊的 Windows 桌面指導方針](/windows/desktop/uxguide/ctrl-drop)操作。

#### <a name="visual-style"></a>視覺樣式

- 在 [公用程式] 對話方塊中，不要重新範本控制項。 使用控制項的基本樣式內建函式。

- 在主題 UI 中，下拉式方塊和下拉式清單會依照控制項的標準主題進行。

#### <a name="layout"></a>Layout
下拉式方塊和下拉式清單應該調整大小以符合內容，而不符合顯示視窗的寬度，也不會任意比對長欄位的長度，例如路徑。

![不正確：下拉式寬度對將顯示的內容而言太長。](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />不正確：下拉式寬度對將顯示的內容而言太長。

![正確：下拉式清單會調整大小以允許轉譯成長，但不需要太長的時間。](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />正確：下拉式清單會調整大小以允許轉譯成長，但不需要太長的時間。

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> 核取方塊
如需一般的互動行為，請依照 [核取方塊的 Windows 桌面指導方針](/windows/desktop/uxguide/ctrl-check-boxes)操作。

#### <a name="visual-style"></a>視覺樣式

- 在 [公用程式] 對話方塊中，不要重新範本控制項。 使用控制項的基本樣式內建函式。

- 在主題 UI 中，核取方塊會遵循控制項的標準主題。

#### <a name="specialized-interactions"></a>特殊化互動

- 與核取方塊的互動絕對不能彈出對話方塊或流覽至另一個區域。

- 將核取方塊與第一行文字的基準對齊。

     ![不正確：核取方塊是在文字的中央。](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />不正確：核取方塊是在文字的中央。

     ![正確：核取方塊會與文字的第一行對齊。](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />正確：核取方塊會與文字的第一行對齊。

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> 選項按鈕
若為一般的互動行為，請依照 [Windows 桌面指導方針來進行選項按鈕](/windows/desktop/uxguide/ctrl-radio-buttons)。

#### <a name="visual-style"></a>視覺樣式
在公用程式對話方塊中，請勿將選項按鈕樣式。 使用控制項的基本樣式內建函式。

#### <a name="specialized-interactions"></a>特殊化互動
除非您需要在嚴密的版面配置中維護群組的差異，否則不需要使用群組框架來括住單選選擇。

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> 群組框架
針對一般互動行為，請依照 [群組框架的 Windows 桌面指導方針](/windows/desktop/uxguide/ctrl-group-boxes)操作。

#### <a name="visual-style"></a>視覺樣式
在公用程式對話方塊中，不要將群組框架樣式。 使用控制項的基本樣式內建函式。

#### <a name="layout"></a>Layout

- 除非您需要在嚴密的版面配置中維護群組的差異，否則不需要使用群組框架來括住單選選擇。

- 請勿將群組框架用於單一控制項。

- 有時可以接受使用水準規則，而不是群組框架容器。

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> 文字控制項

### <a name="static-text-fields"></a>靜態文字欄位

靜態文字欄位會顯示唯讀資訊，而且無法由使用者選取。 避免將它用於使用者可能想要複製到剪貼簿中的任何文字。 但是，唯讀的靜態文字可能會變更，以反映狀態的變更。 在下列範例中，資訊群組下的輸出名稱靜態文字會變更，以反映對其上方的根命名空間文字方塊所做的任何變更。

有兩種方式可以顯示靜態文字資訊。

當沒有任何群組衝突時，靜態文字可以在對話方塊中單獨使用，而不需要任何包含專案。 決定是否真的需要方塊的額外行。 例如，在群組行所建立的區段下顯示目錄路徑，如下所示：

![文字控制項中的靜態文字資訊](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />文字控制項中的靜態文字資訊

在其他群組區域存在的對話方塊中，以及資訊的內含專案有助於可讀性，以及當區段可以隱藏或顯示 (如 **屬性視窗** 描述窗格) 或您想要與類似的 UI 一致，請將靜態文字放在方塊內。 此群組方塊應該是單一規則，並以下列色彩標示 `ButtonShadow` ：

![屬性視窗中的靜態文字](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />屬性視窗中的靜態文字

### <a name="read-only-text-box"></a>唯讀文字方塊

這可讓使用者選取欄位內的文字，但不能加以編輯。 這些文字方塊會以一般的立體雕刻（填滿）來加上邊框 `ButtonShadow` 。

當使用者更改相關聯的控制項（例如檢查/取消選取核取方塊或選取/取消選取選項按鈕）時，文字方塊可能會變成作用中 (可編輯) 。 例如，在如下所示的 [**工具 &gt; 選項**] 頁面中，如果未核取 [**使用預設值**] 核取方塊，[**首頁**] 文字方塊就會變成 [作用中]。

![顯示非作用中和作用中狀態的唯讀文字方塊](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />顯示非作用中和作用中狀態的唯讀文字方塊

### <a name="using-text-in-dialogs"></a>在對話方塊中使用文字

對話方塊中文字的主要指導方針：

- Unthemed 對話方塊中文字方塊、清單方塊和框架的標籤是以動詞開頭，只有第一個單字的初始大寫，並以冒號結尾。

    > 主題對話方塊中的文字控制項會遵循 [Windows 桌面 UX 指導方針](/windows/desktop/uxguide/top-violations) ，而不會使用結尾標點符號，但說明連結中的問號除外。

- 核取方塊和選項按鈕的標籤開頭為動詞、第一個單字的初始大寫，而且沒有結束標點符號。

- 按鈕、功能表、功能表項目和索引標籤的標籤會在每個字 (標題案例) 的開頭為大寫。

- 標籤術語應與其他對話方塊中類似的標籤一致。

- 可能的話，請先編寫寫入器/編輯器或核准文字，然後再進入開發人員進行執行。

- 除了定位已足夠的特殊情況下，所有控制項都應該有標籤。
適當時，請使用 helper 文字。

### <a name="helper-text"></a>Helper 文字

包含在對話方塊中，以協助使用者瞭解對話的用途，或指出所要採取的動作。 只有在需要時才應該使用協助程式文字，以避免雜亂的簡單對話。 Helper 文字的兩個變化是對話方塊和浮水印。

遵循協助程式文字的常見位置，並在新區域推出時選擇選擇。 Helper 文字的常見案例包括：

- 對話方塊中的協助程式文字，以提供有關如何與複雜對話互動的其他方向。

- 空白的工具視窗或對話方塊中的浮水印文字，說明為何沒有顯示任何內容。

- 描述窗格，例如 **屬性視窗** 底部。

- 空白編輯器中的浮水印文字，以說明使用者開始執行的動作。

### <a name="dialog-helper-text"></a>對話方塊 Helper 文字

使用者體驗設計人員可能有助於判斷協助程式文字是否適當。 設計工具可以定義 helper 文字出現的位置，以及其一般內容。 使用者協助可以撰寫/編輯實際的文字。

### <a name="watermarks"></a>浮水印

對話方塊受益于略有不同的浮水印指導方針。 因為對話可能會在許多 UI 元素中出現， (標籤、提示文字、按鈕和其他具有文字) 的容器控制項，尤其是當那些以黑色顯示浮水印時，浮水印在暗灰色 (VSColor：) 會更好用 `ButtonShadow` 。 浮水印通常會出現在控制項內，例如具有白色背景 (VSColor：) 的清單方塊 `Window` 。

- 文字會以暗灰色顯示 (VSColor： `ButtonShadow`) 。 但是，如果浮水印出現在中等灰色或其他彩色的 (VSColor： `ButtonFace`) 背景，而且有關于其可讀性的問題，請使用黑色文字 (VSColor： `WindowText`) 。

- 浮水印可置中或靠左對齊。 進行對齊決策時套用標準設計規則。 無法在背景選取水位線。

![浮水印文字範例](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />浮水印文字範例

### <a name="context-specific-dynamic-text"></a>特定內容 (動態) 文字

您可以使用下列兩種方式之一，在對話方塊或無模式 UI 中使用動態文字：作為動態磁碟區標或動態內容。

- 動態磁碟區標：動態文字的常見用法是在描述性面板中，為選取的專案提供詳細資訊，例如，在包含右邊方格中顯示之元素和屬性清單的對話方塊中。 屬性方格的標籤可能是動態的，因此在左邊選取專案時，右邊的方格會顯示該特定專案的資訊。

- 動態文字：在您需要以這種方式顯示特定資訊，而不是一般資訊的情況下，可能會很有用，但請小心不要過度取用。

如果您希望使用者能夠複製資訊，動態文字應該會在唯讀文字欄位中。

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> 按鈕和超連結

### <a name="overview"></a>概觀
按鈕和連結控制項 (超連結) 應遵循使用方式、用語、調整大小和間距之 [超連結的基本 Windows 桌面指南](/windows/desktop/uxguide/ctrl-links) 。

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
![資訊列中用於狀態訊息的命令連結](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />資訊列中用於狀態訊息的命令連結

![CodeLens 快顯視窗中所使用的連結](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />CodeLens 快顯視窗中所使用的連結

![用於次要命令的連結，其中按鈕會吸引太多注意力](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />用於次要命令的連結，其中按鈕會吸引太多注意力

### <a name="common-buttons"></a>一般按鈕

#### <a name="text"></a>Text
遵循 [UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)中的寫作指導方針。

#### <a name="visual-style"></a>視覺樣式

##### <a name="standard-unthemed"></a>標準 (unthemed) 
Visual Studio 中的大部分按鈕會出現在公用程式對話方塊中，不應進行樣式。 它們應該會反映依作業系統規定之按鈕的標準外觀。

##### <a name="themed"></a>主題
在某些情況下，按鈕可能會在已樣式的 UI 中使用，而這些按鈕必須適當地設計樣式。 如需主題控制項的詳細資訊，請參閱 [對話方塊](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) 。

### <a name="special-buttons"></a>特殊按鈕

#### <a name="browse-buttons"></a>流覽。。。按鈕
**[流覽 ...]** 按鈕用於方格、對話方塊和工具視窗，以及其他無模式 UI 元素。 它們會顯示選擇器，協助使用者將值填入控制項。 這個按鈕有兩種變化： long 和 short。

![完整的 [流覽 ...] 按鈕](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />完整的 [流覽 ...] 按鈕

![僅省略號的簡短 [...] 按鈕](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />僅省略號的簡短 [...] 按鈕

使用僅限省略號的簡短按鈕：

- 如果對話方塊中有一個以上的長 **[流覽 ...]** 按鈕，例如當有數個欄位允許流覽時。 針對每個使用 **[...]** 按鈕，以避免此情況所建立的令人困惑的存取金鑰 (在相同對話方塊) 中 **&流覽** 和 **B&流覽)** 。

- 在嚴密的對話中，或沒有適當的位置來放置長按鈕時。

- 如果按鈕會出現在方格控制項中。

使用按鈕的指導方針：

- 請勿使用存取金鑰。 若要使用鍵盤來存取它，使用者必須在連續的控制項中使用 tab 鍵。 確定定位順序是讓任何瀏覽按鈕緊接在其填滿的欄位之後。 絕對不要在第一個期間使用底線。

- 將 Microsoft Active Accessibility (MSAA) **名稱** ] 屬性設定為 **[流覽 ...]** (包含省略號) ，讓螢幕讀取器將其讀取為「流覽」，而不是「點點-點」或「期間期間」。 針對 managed 控制項，這表示設定 **AccessibleName** 屬性。

- 絕對不要使用省略號 **[...]** 按鈕進行流覽動作以外的任何動作。 例如，如果您需要 **[新增 ...]** 按鈕，但沒有足夠的空間來容納文字，則必須重新設計對話方塊。

##### <a name="sizing-and-spacing"></a>調整大小和間距
![調整 [流覽 ...] 按鈕的大小：標準版本為75x23 圖元，較短版本為26x23 圖元](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />調整 [瀏覽...] 按鈕的大小

![間距 [流覽 ...] 按鈕：關聯控制項和標準瀏覽按鈕7圖元之間的間距、相關控制項和簡短瀏覽按鈕之間的間距5圖元](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />調整 [瀏覽...] 按鈕的間距

#### <a name="graphical-buttons"></a>圖形按鈕
有些按鈕應該一律使用圖形影像，而且永遠不會包含文字來節省空間並避免當地語系化問題。 這些通常用於欄位選擇器和其他可排序清單。

> [!NOTE]
> 使用者必須索引標籤至這些按鈕 (沒有) 的存取金鑰，因此請以合理的順序放置它們。 將 `name` 按鈕的屬性對應至它所採取的動作，讓畫面讀取器正確地解讀按鈕動作。

| 函數 | 按鈕 |
| --- | --- |
| 加 | ![圖形 [加入] 按鈕](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| 移除 | ![圖形 [移動] 按鈕](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| 加入全部 | ![圖形 [全部加入] 按鈕](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| 全部移除 | ![圖形 [全部移除] 按鈕](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| 上移 | ![圖形 [上移] 按鈕](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| 下移 | ![圖形 [下移] 按鈕](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| 刪除 | ![圖形 [刪除] 按鈕](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>調整大小和間距
圖形按鈕的大小調整與 **[流覽 ...]** 按鈕的簡短版本相同 (26x23 圖元) ：

![按鈕上圖形影像的外觀，顯示和不顯示透明色彩](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />按鈕上圖形影像的外觀，顯示和不顯示透明色彩

### <a name="hyperlinks"></a>超連結
超連結很適合以導覽為基礎的動作，例如開啟說明主題、強制回應對話方塊或 wizard。 如果有用於命令的超連結，則應該一律顯示 UI 的可見和明顯變更。 一般來說，認可至動作 (例如儲存、取消和刪除) 的動作，會使用按鈕進行較佳的通訊。

#### <a name="writing-style"></a>撰寫樣式
遵循 [Windows 桌面的使用者介面文字指引](/windows/desktop/uxguide/text-ui)。 請勿使用「深入瞭解」、「告訴我更多資訊」或「取得此措辭的協助」。 相反地，片語說明會以說明內容所回答的主要問題為依據來連結文字。 例如，「**如何? 將伺服器新增至伺服器總管？**」

#### <a name="visual-style"></a>視覺樣式

- 超連結應該一律使用 [VSColor 服務](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。 如果超連結的樣式不正確，則會在作用中或在造訪之後顯示不同的色彩時閃爍紅色。

- 請勿在控制項停留狀態包含底線，除非連結是完整句子中的句子片段，例如浮水印。

- 停留時不應顯示底線。 相反地，對使用者而言，連結為作用中的意見反應是稍微改變的色彩，以及適當的連結游標。

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> 樹狀檢視

樹狀檢視可讓您將複雜清單組織成父子式群組。 使用者可以展開或折迭父群組，以顯示或隱藏基礎子專案。 您可以選取樹狀檢視中的每個專案，以提供進一步的動作。

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> 樹狀檢視視覺效果樣式

#### <a name="expanders"></a>展開器
樹狀檢視控制項應該符合 Windows 和 Visual Studio 所使用的擴充項設計。 每個節點都會使用展開器控制項來顯示或隱藏基礎專案。 使用擴充器控制項可為可能在 Windows 和 Visual Studio 中遇到不同樹狀檢視的使用者提供一致性。

![更正：使用展開器控制項之樹狀檢視節點的適當樣式](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />更正：使用展開器控制項之樹狀檢視節點的適當樣式

![不正確：樹狀檢視節點的不適當樣式](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />不正確：樹狀檢視節點的不適當樣式

#### <a name="selection"></a>選取
當您在樹狀檢視內選取節點時，反白顯示應該會擴充至樹狀檢視控制項的全形。 這可協助使用者清楚地識別他們所選取的專案。 選取色彩應該會反映目前的 Visual Studio 主題。

![正確：反白顯示選取的節點符合整個樹狀檢視控制項的寬度。](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />正確：反白顯示選取的節點符合整個樹狀檢視控制項的寬度。

![不正確：反白顯示選取的節點無法容納整個樹狀檢視控制項的寬度。](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />不正確：反白顯示選取的節點無法容納整個樹狀檢視控制項的寬度。

#### <a name="icons"></a>圖示
如果圖示有助於以視覺化方式識別專案之間的差異，則應該只在樹狀檢視控制項中使用。 一般情況下，圖示只能用在不同的清單中，這些圖示會攜帶資訊來區分專案類型。 在使用圖示的同質清單中，經常會看到雜訊，應予以避免。 在這種情況下， (父) 的群組圖示可以傳達內的專案類型。 這項規則的例外狀況是，如果圖示為動態，而且是用來表示狀態。

#### <a name="scroll-bars"></a>捲軸
如果內容適用于樹狀檢視控制項，則應該一律隱藏捲軸。 捲軸可接受隱藏，或是可滾動視窗中的半透明，並且在包含樹狀檢視的視窗具有焦點，或在樹狀檢視本身停留時出現。

![垂直和水準捲軸會顯示，因為內容已超過樹狀檢視控制項的限制。](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />垂直和水準捲軸會顯示，因為內容已超過樹狀檢視控制項的限制。

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> 樹狀檢視互動

#### <a name="context-menus"></a>操作功能表
樹狀檢視節點可顯示內容功能表中的子功能表選項。 一般來說，當使用者以滑鼠右鍵按一下專案，或按下 Windows 鍵盤上的功能表鍵並選取專案時，就會發生這種情況。 節點必須獲得焦點並選取。 這可協助使用者識別子功能表所屬的專案。

![已產生內容功能表的專案會取得焦點，以通知使用者已選取哪一個專案。](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_CoNtextMenu")<br />已產生內容功能表的專案會取得焦點，以通知使用者已選取哪一個專案。

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

![Visual Studio 中的 trid 控制項](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Visual Studio 中的 trid 控制項
