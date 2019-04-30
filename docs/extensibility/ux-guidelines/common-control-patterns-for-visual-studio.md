---
title: 適用於 Visual Studio 的通用控制項模式 |Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c89babf7dc9f90b4042d917bf5843a0703628883
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62799151"
---
# <a name="common-control-patterns-for-visual-studio"></a>適用於 Visual Studio 的通用控制項模式
## <a name="BKMK_CommonControls"></a> 通用控制項

### <a name="overview"></a>總覽
通用控制項組成大部分的 Visual Studio 中的使用者介面。 在 Visual Studio 介面中使用的最常見控制項應該遵循[Windows 桌面互動的指導方針](/windows/desktop/uxguide/controls)。 本主題旨在說明 Visual Studio，並涵蓋了特殊的情況下或擴充這些 Windows 指導方針的詳細資料。

#### <a name="common-controls-in-this-topic"></a>本主題中的通用控制項

- [捲軸](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [輸入的欄位](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [下拉式方塊和下拉式清單](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [核取方塊](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [選項按鈕](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [群組的畫面格](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [文字控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [按鈕和超連結](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [樹狀檢視](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>視覺化樣式
首先要考慮設定控制項的樣式時是否將控制項使用中佈景主題 UI 中。 標準的 UI 中的控制項為非佈景主題 UI，且必須遵照[一般的 Windows 桌面樣式](/windows/desktop/uxguide/controls)，這表示它們不重新範本化，而且應該會出現在其預設控制項外觀。

- **標準 （公用程式） 對話方塊：** 未配置其佈景主題。 不重新範本。 使用基本的控制項樣式的預設值。

- **工具視窗、 文件編輯器、 設計介面和反映一定主題的對話方塊：** 使用特製化佈景主題的外觀，使用色彩服務。

### <a name="BKMK_Scrollbars"></a> 捲軸
 捲軸所應遵循[常見的 Windows 互動模式，捲軸](/windows/desktop/Controls/about-scroll-bars)除非它們夾帶內容資訊，例如程式碼編輯器中。

### <a name="BKMK_InputFields"></a> 輸入的欄位
 典型的互動行為，請遵循[文字方塊中的 Windows 桌面方針](/windows/desktop/uxguide/ctrl-text-boxes)。

#### <a name="visual-style"></a>視覺化樣式

- 不應該在公用程式的對話方塊中設定輸入的欄位的樣式。 使用基本內建控制項的樣式。

- 佈景主題的輸入的欄位應該只用在佈景主題的對話方塊和工具視窗。

#### <a name="specialized-interactions"></a>特製化的互動

- 唯讀欄位會顯示有但 （使用中） 的預設前景灰色 （停用） 背景。

- 所需欄位應有**\<需要 >** 做為其中的標準。 您不應該變更除了在少數情況下的背景色彩。

- 錯誤驗證：請參閱[通知和適用於 Visual Studio 的進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- 輸入的欄位都應該調整大小以符合內容，不以符合在其中，它們會顯示，視窗的寬度，也不能以任意符合長的欄位，例如路徑的長度。 長度可能是向使用者表示的欄位中允許多少個字元的限制。

     ![不正確的輸入的欄位長度： 不太可能的名稱會是此種長度。](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707年 01_IncorrectInputFieldControl")<br />不正確的輸入的欄位長度： 不太可能的名稱會是此種長度。

     ![更正的輸入的欄位長度： 輸入的欄位是合理的寬度，如預期的內容。](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707年 02_CorrectInputFieldControl")<br />更正的輸入的欄位長度： 輸入的欄位是合理的寬度，如預期的內容。

### <a name="BKMK_ComboBoxesAndDropDowns"></a> 下拉式方塊和下拉式清單
典型的互動行為，請遵循[下拉式清單和下拉式方塊的 Windows 桌面方針](/windows/desktop/uxguide/ctrl-drop)。

#### <a name="visual-style"></a>視覺化樣式

- 公用程式的對話方塊，在不重新範本控制項。 使用基本內建控制項的樣式。

- 在佈景主題 UI 中，下拉式方塊和下拉式清單，請遵循標準的佈景主題的控制項。

#### <a name="layout"></a>配置
下拉式方塊和下拉式清單應該調整大小以符合內容，不以符合在其中，它們會顯示，視窗的寬度，也不能以任意符合長的欄位，例如路徑的長度。

![不正確： 下拉式清單寬度是將顯示的內容太長。](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707年 03_IncorrectDropDownLayout")<br />不正確： 下拉式清單寬度是將顯示的內容太長。

![正確： 下拉式清單會調整大小以允許轉譯成長，但不是會不必要的長。](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707年 04_CorrectDropDownLayout")<br />正確： 下拉式清單會調整大小以允許轉譯成長，但不是會不必要的長。

### <a name="BKMK_CheckBoxes"></a> 核取方塊
典型的互動行為，請遵循[核取方塊的 Windows 桌面方針](/windows/desktop/uxguide/ctrl-check-boxes)。

#### <a name="visual-style"></a>視覺化樣式

- 公用程式的對話方塊，在不重新範本控制項。 使用基本內建控制項的樣式。

- 在佈景主題 UI 中，核取方塊會遵循標準的佈景主題的控制項。

#### <a name="specialized-interactions"></a>特製化的互動

- 核取方塊的互動必須永遠不會快顯對話方塊，或瀏覽至另一個區域。

- 對齊文字的第一行基準線的核取方塊。

     ![不正確： 核取方塊會置中的文字。](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707年 05_IncorrectCheckBoxAlign")<br />不正確： 核取方塊會置中的文字。

     ![正確： 核取方塊對齊文字的第一行。](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707年 06_CorrectCheckBoxAlign")<br />正確： 核取方塊對齊文字的第一行。

### <a name="BKMK_RadioButtons"></a> 選項按鈕
典型的互動行為，請遵循[選項按鈕的 Windows 桌面方針](/windows/desktop/uxguide/ctrl-radio-buttons)。

#### <a name="visual-style"></a>視覺化樣式
在公用程式對話方塊中，執行樣式選項按鈕。 使用基本內建控制項的樣式。

#### <a name="specialized-interactions"></a>特製化的互動
您不需要使用群組框來括住選項選擇，除非您需要維護群組差別，在於緊密的版面配置。

### <a name="BKMK_GroupFrames"></a> 群組的畫面格
典型的互動行為，請遵循[Windows 桌面的指導方針群組框架](/windows/desktop/uxguide/ctrl-group-boxes)。

#### <a name="visual-style"></a>視覺化樣式
公用程式中的對話，不要樣式群組畫面格。 使用基本內建控制項的樣式。

#### <a name="layout"></a>配置

- 您不需要使用群組框來括住選項選擇，除非您需要維護群組差別，在於緊密的版面配置。

- 永遠不會使用單一控制項群組框架。

- 有時候會接受使用水平尺規，而不是群組的範圍容器。

## <a name="BKMK_TextControls"></a> 文字控制項

### <a name="static-text-fields"></a>靜態文字欄位

靜態文字欄位不能選取使用者，與顯示唯讀資訊。 請避免使用任何文字，使用者可能會想要複製到剪貼簿。 不過，唯讀的靜態文字可以變更以反映在狀態變更。 在下列範例中，以反映其上方的 [根命名空間] 文字方塊中所做的變更資訊群組變更底下的輸出名稱靜態文字。

有兩種方式，以顯示靜態文字的資訊。

可以是靜態文字，在它自己在對話方塊中，而不需要任何內含項目時，沒有群組衝突。 決定是否真的需要額外的行方塊。 舉例來說，群組列，所建立的區段下的目錄路徑的顯示，如下所示：

![在文字控制項中的靜態文字資訊](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />在文字控制項中的靜態文字資訊

在對話方塊中，存在其他群組的區域，內含項目資訊的協助增加可讀性，和區段時可以隱藏或顯示 (依照**屬性 視窗**podokno popisu) 或您想要與類似的 UI，一致將靜態文字放在方塊內。 此群組方塊應該是單一規則，並加上`ButtonShadow`:

![在 [屬性] 視窗中的靜態文字](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />在 [屬性] 視窗中的靜態文字

### <a name="read-only-text-box"></a>唯讀文字方塊

這可讓使用者選取的文字欄位內，但無法編輯它。 這些文字方塊由一般 3d 字 （平頭） 與起`ButtonShadow`填滿。

文字方塊可以變成作用中 （編輯） 時使用者會改變為相關聯的控制項，例如檢查/取消核取方塊，或選取/取消選取的選項按鈕。 例如，在**工具&gt;選項**頁面，如下所示**首頁**文字方塊將會變成作用中時**使用預設的**核取方塊未核取。

![唯讀的文字方塊中，顯示非作用中和作用中狀態](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />唯讀的文字方塊中，顯示非作用中和作用中狀態

### <a name="using-text-in-dialogs"></a>使用對話方塊中的文字

在對話方塊中的文字的關鍵指導方針：

- 文字方塊、 清單方塊和 unthemed 對話方塊中的畫面格的標籤開頭的動詞命令、 對，第一個字組的初始資本和冒號的結尾。

    > 請依照下列主題的對話方塊中的文字控制項[Windows 桌面的 UX 指導方針](/windows/desktop/uxguide/top-violations)，而且不接受結尾的標點符號，除了說明連結中的問號。

- 核取方塊和選項按鈕的標籤開頭的動詞命令，在第一個字組，初始資本，而且有沒有結束標點符號。

- 按鈕、 功能表、 功能表項目和索引標籤的標籤會將第一個字母大寫對每個單字 （字首大寫）。

- 標籤的用語應該與其他對話方塊中的類似標籤一致。

- 可能的話，有撰寫或開發人員實作，它會進入之前，核准將文字寫入器/編輯器。

- 所有控制項都應該在特殊情況下都具有以外的標籤在哪一個定位停駐點即已足夠。
使用適當時的協助程式文字。

### <a name="helper-text"></a>Helper 文字

包含在對話方塊可協助使用者了解在對話方塊目的，或指出要採取的動作。 Helper 文字應該只在需要時用來避免而過於凌亂簡單的對話方塊。 Helper 文字兩種變化是對話方塊和浮水印。

請依照下列常見協助程式文字的位置，而且是選擇性中引入新的區域。 Helper 文字的常見案例包括：

- 協助程式對話方塊，提供有關如何與複雜的對話方塊互動的其他方向中的文字。

- 在空白的工具視窗或對話方塊，說明為什麼沒有內容會顯示浮水印文字。

- 描述 窗格中，例如底部**屬性 視窗**。

- 浮水印文字在空白的編輯器，來說明使用者應開始執行的動作。

### <a name="dialog-helper-text"></a>對話方塊 Helper 文字

使用者經驗設計工具可協助判斷 helper 文字適當。 設計工具可以定義 helper 文字，以及其一般的內容會出現。 使用者協助可以寫入/編輯的實際文字。

### <a name="watermarks"></a>浮水印

對話方塊受益於稍有不同的水位線的指導方針。 因為一個對話方塊，會出現忙著處理許多 UI 項目 （標籤、 提示文字、 按鈕和其他容器控制項中的文字），特別是當這些顯示為黑色，浮水印脫穎而出美好暗灰色 (VSColor: `ButtonShadow`)。 浮水印通常會出現在這類具有白色背景的清單方塊控制項 (VSColor: `Window`)。

- 文字會出現在暗灰色 (VSColor: `ButtonShadow`)。 不過，如果出現中型灰色或其他彩色的浮水印 (VSColor: `ButtonFace`) 背景，並沒有其可讀性的相關考量，請以黑色文字 (VSColor: `WindowText`)。

- 浮水印可以置中或靠左對齊。 對齊決策時，請套用標準設計規則。 無法選取水位線的背景。

![浮水印文字範例](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />浮水印文字範例

### <a name="context-specific-dynamic-text"></a>特定內容 （動態） 的文字

動態文字可以是使用的其中一個對話方塊中或非強制回應 UI 中的兩種方式： 動態的標籤或動態內容。

- 動態標籤： 動態文字的常見用法是描述性的面板，例如提供選取的項目，如需詳細資訊，在對話方塊中包含的元素和屬性在右邊方格中顯示這些項目的清單中。 屬性方格的標籤可能是動態的以便在右邊方格左側選取項目時，顯示該特定項目的資訊。

- 動態文字： 在其中您要顯示的特定資訊並不是針對一般資訊，如此一來，但應該小心過度使用的執行個體很有用。

如果您希望使用者能夠將資訊複製時，動態文字應該是唯讀的文字欄位中。

## <a name="BKMK_ButtonsAndHyperlinks"></a> 按鈕和超連結

### <a name="overview"></a>總覽
按鈕和連結控制項 （超連結） 應該遵循[超連結的基本 Windows 桌面指引](/windows/desktop/uxguide/ctrl-links)使用量和字詞，調整大小、 間距。

### <a name="choosing-between-buttons-and-links"></a>選擇按鈕或連結
傳統上，按鈕已用於動作，並已保留的超連結以瀏覽。 按鈕可用於所有情況下，但已連結的角色擴充 Visual Studio 中，因此是在某些情況下，更可互換的按鈕和連結。

使用命令按鈕的時機：

- 主要的命令

- 顯示用來收集輸入的 windows，或選擇較高，即使它們為次要命令

- 具破壞性或無法復原的動作

- 精靈和頁面內的承諾用量按鈕流程

避免命令按鈕的工具視窗，或如果您需要兩個以上的文字標籤。 連結可以有較長的標籤。

 使用連結的時機：

- 瀏覽至另一個視窗、 文件或網頁

- 需要較長的標籤或簡短的句子來描述動作的意圖的情況

- 其中一個按鈕會會拖垮 UI，前提是該動作不是破壞性或無法復原的緊密空格

- 取消強調情況中的第二個命令有許多命令

#### <a name="examples"></a>範例
![命令使用在下一個狀態訊息的資訊列中的連結](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />在下一個狀態訊息的資訊列中使用的命令連結

![使用 CodeLens 快顯視窗中的連結](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />CodeLens 快顯視窗中所使用的連結

![連結用於第二個命令，按鈕會吸引太多加重視](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />用於第二個命令按鈕會吸引太多加重視的其中的連結

### <a name="common-buttons"></a>一般按鈕

#### <a name="text"></a>文字
請依照下列中的撰寫指導方針[UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。

#### <a name="visual-style"></a>視覺化樣式

##### <a name="standard-unthemed"></a>標準 (unthemed)
在 Visual Studio 中的大部分按鈕會出現在公用程式的對話方塊，並且應該不能設定樣式。 它們應該反映出按鈕的標準外觀，如作業系統所指定。

##### <a name="themed"></a>佈景主題
在某些情況下，按鈕可能用於已設定樣式的 UI 中，這些按鈕必須有適當的樣式。 請參閱[對話方塊](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)佈景主題控制項上的資訊。

### <a name="special-buttons"></a>特殊的按鈕

#### <a name="browse-buttons"></a>瀏覽 按鈕
**[瀏覽...]** 按鈕使用中格線、 對話方塊和工具視窗和其他非強制回應的 UI 項目。 它們會顯示在控制項填入值，可協助使用者選擇器。 有兩種變化，此按鈕時，完整和簡短。

![長的 [瀏覽...] 按鈕](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />長的 [瀏覽...] 按鈕

![僅限省略符號的簡短的 [...] 按鈕](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />僅限省略符號的簡短的 [...] 按鈕

使用僅限省略符號的簡短按鈕的時機：

- 如果有一個以上長 **[瀏覽...]** 在對話方塊中，例如數個欄位進行瀏覽 按鈕。 使用簡短的 **[...]** 針對每個以避免這種情況下所建立令人困惑的存取金鑰 按鈕 (**（& s) 瀏覽**並**B & 覽**相同的對話方塊中)。

- 在嚴格的對話方塊中，或將長的按鈕沒有合理的地方。

- 如果按鈕會出現在方格控制項。

使用 [] 按鈕的指導方針：

- 請勿使用存取金鑰。 若要存取它使用鍵盤，使用者必須從相鄰的控制項索引標籤。 請確定定位順序，欄位將會填滿之後，立即就會任何瀏覽 按鈕。 永遠不會使用底線字元下方的第一個週期。

- 設定 Microsoft Active Accessibility (MSAA)**名稱**屬性設**瀏覽...** （包含省略符號） 讓，螢幕助讀程式會朗讀它像是 [瀏覽]，而不"點-點-點 」 或 「 週期-期間-期間。 」 對於受管理的控制項，這表示設定**AccessibleName**屬性。

- 永遠不會使用省略符號 **[...]** 按鈕以外的瀏覽動作。 例如，如果您需要 **[新增...]** 按鈕，但沒有足夠的空間，文字、，然後需要重新設計對話方塊。

##### <a name="sizing-and-spacing"></a>調整大小和間距
![調整 [瀏覽...] 按鈕： standard 版本為 75 x 23 像素、 簡短版本為 26 x 23 像素](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />調整 [瀏覽...] 按鈕的大小

![間距 [瀏覽...] 按鈕： 相關的控制項與標準瀏覽按鈕 7 個像素之間的間距，間距相關的控制項，並簡短的瀏覽按鈕 5 像素](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />調整 [瀏覽...] 按鈕的間距

#### <a name="graphical-buttons"></a>圖形化的按鈕
某些按鈕應該一律使用圖形化映像，也絕對不要包含文字，以節省空間，並避免當地語系化問題。 這些通常可在 欄位選擇器和其他可排序的清單。

> **注意：** 使用者需要這些按鈕 （沒有存取金鑰） 索引標籤，因此將它們放在合理的順序。 對應`name`花費，讓螢幕助讀程式正確地解譯按鈕動作的動作按鈕的屬性。

| 功能 | 按鈕 |
| --- | --- |
| 新增 | ![Graphical "Add" button](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| 移除 | ![Graphical "Remove" button](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| 全部加入 | ![圖形 [全部加入] 按鈕](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| 全部移除 | ![Graphical "Remove All" button](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| 上移 | ![圖形的 「 上移 按鈕](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| 下移 | ![圖形 [下移] 按鈕](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| 刪除 | ![Graphical "Delete" button](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>調整大小和間距
調整大小的圖形化的按鈕的簡短版本一樣 **[瀏覽...]** 按鈕 （26 x 23 像素為單位）：

![在按鈕上，使用和不透明的色彩顯示的圖形影像的外觀](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />在按鈕上，使用和不透明的色彩顯示的圖形影像的外觀

### <a name="hyperlinks"></a>超連結
超連結是適合用來巡覽為基礎的動作，例如開啟說明主題、 強制回應對話方塊中或精靈。 如果命令使用超連結，它應該一律 ui 會顯示可見及明顯的變更。 一般情況下，認可至動作 （例如儲存，請 [取消]，並刪除） 的動作是更好溝通使用按鈕中。

#### <a name="writing-style"></a>撰寫樣式
請遵循[使用者介面文字的 Windows 桌面指引](/windows/desktop/uxguide/text-ui)。 請勿使用 「 了解更多關於，」 「 告訴我更多關於，」 或 「 取得協助與這個"片語。 相反地，片語解答的說明內容的主要問題方面的說明連結文字。 比方說，「**方式 [伺服器總管] 來新增伺服器？**"

#### <a name="visual-style"></a>視覺化樣式

- 應該一律使用超連結[The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。 如果超連結的樣式不正確，它會閃爍紅色作用時，或顯示不同的色彩後正在瀏覽。

- 請不要包含在控制項上來狀態，除非連結處於句子片段內完整的句子，例如浮水印的底線。

- 暫留時，不應出現底線。 相反地，連結是作用中使用者的意見反應是稍微色彩變更，而適當的連結資料指標。

## <a name="BKMK_TreeViews"></a> 樹狀檢視

樹狀檢視會提供一種方式組織複雜列出成父子式群組。 使用者可以展開或摺疊父群組，來顯示或隱藏基礎的子項目。 可以選取樹狀檢視中的每個項目，以提供進一步的動作。

### <a name="BKMK_TreeViewVisualStyle"></a> 樹狀結構檢視中的視覺化樣式

#### <a name="expanders"></a>展開器
Windows 和 Visual Studio 所使用的展開器設計應該符合樹狀檢視控制項。 每個節點使用 expander 控制項來顯示或隱藏基礎項目。 使用 expander 控制項的使用者可能會遇到 Windows 和 Visual Studio 內的不同的樹狀檢視中提供一致性。

![正確： 使用 expander 控制項的樹狀檢視節點的適當的樣式](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />使用 expander 控制項的樹狀檢視節點的正確： 適當的樣式

![不正確： 不正確樣式的樹狀檢視節點](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />不正確： 的樹狀檢視節點不適當的樣式

#### <a name="selection"></a>選取
在樹狀檢視中選取節點時，反白顯示應該展開成完整的樹狀檢視控制項的寬度。 這有助於使用者清楚地識別他們選取了哪一個項目。 選取範圍色彩應反映出目前的 Visual Studio 佈景主題。

![正確： 反白顯示選取之節點的符合整個樹狀檢視控制項的寬度。](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />正確： 反白顯示選取之節點的符合整個樹狀檢視控制項的寬度。

![不正確： 反白顯示選取之節點的容納不下整個樹狀檢視控制項的寬度。](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />不正確： 反白顯示選取之節點的容納不下整個樹狀檢視控制項的寬度。

#### <a name="icons"></a>圖示
圖示只有他們協助以視覺化方式識別項目之間的差異的情況下，只應該在樹狀檢視控制項中使用。 一般情況下，圖示應該只能用於異質性清單圖示，執行區分項目類型的資訊。 同質的清單中使用的圖示通常視為非搜尋，應該予以避免。 在此情況下 （父系） 中的 [群組] 圖示可傳達其內的項目的類型。 此規則的例外狀況是如果圖示是動態的而用來指示狀態。

#### <a name="scroll-bars"></a>捲軸
如果內容符合樹狀檢視控制項一律應隱藏捲軸。 它是可接受的捲軸在可捲動視窗中會隱藏，或具有半透明和時包含樹狀檢視中的視窗有焦點，顯示或樹狀結構的滑鼠停留在檢視本身。

![因為內容已超出限制的樹狀檢視控制項，則會顯示這兩個垂直和水平捲軸。](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />因為內容已超出限制的樹狀檢視控制項，則會顯示這兩個垂直和水平捲軸。

### <a name="BKMK_TreeViewInteractions"></a> 樹狀結構檢視的互動

#### <a name="context-menus"></a>操作功能表
在樹狀檢視節點可能會顯示內容功能表中的子功能表選項。 通常，這就會發生當使用者以滑鼠右鍵按一下項目，或在與所選取項目的 Windows 鍵盤上按下功能表鍵。 請務必確定節點取得焦點，然後選取。 這有助於使用者識別的子功能表屬於哪一個項目。

![已選取的已產生的項目來通知使用者的內容功能表提升焦點的項目。](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />已選取的已產生的項目來通知使用者的內容功能表提升焦點的項目。

#### <a name="keyboard"></a>鍵盤
樹狀檢視中應提供選取項目 」 和 「 展開/摺疊節點使用鍵盤的能力。 這可確保瀏覽符合我們的協助工具需求。

##### <a name="tree-view-control"></a>樹狀檢視控制項
Visual Studio 樹狀目錄控制項應該遵循一般的鍵盤瀏覽：

- **向上箭號：** 樹狀結構中向上移動選取項目

- **向下箭號：** 藉由移動樹狀結構下的選取項目

- **向右箭頭：** 展開樹狀結構中的節點

- **向左箭號：** 摺疊樹狀結構中的節點

- **輸入金鑰：** 起始、 載入、 執行選取的項目

##### <a name="trid-tree-view-and-grid-view"></a>Trid （樹狀檢視和格線檢視）
Trid 控制項是複雜的控制項，其中包含 grid 內的樹狀檢視。 展開、 摺疊，並瀏覽樹狀目錄中應該遵守相同的鍵盤命令，以樹狀檢視，具有下列功能：

- **向右箭頭：** 展開節點。 節點已展開之後，則應繼續瀏覽至最接近的資料行右側。 瀏覽應該停止的資料列結尾。

- **索引標籤：** 瀏覽至最接近的儲存格右邊。  在資料列的結束時，瀏覽會繼續下一個資料列。

- **Shift + 索引標籤：** 瀏覽至最接近的資料格左邊。  開頭的資料列時，瀏覽會繼續在先前的資料列中最右邊的儲存格。

![在 Visual Studio 中的 trid 控制項](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />在 Visual Studio 中的 trid 控制項