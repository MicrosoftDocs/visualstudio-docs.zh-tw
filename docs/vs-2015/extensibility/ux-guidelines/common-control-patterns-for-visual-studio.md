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
ms.openlocfilehash: efde723cfb72c8f91b0ba88c0a24bb2d9a3d245d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938985"
---
# <a name="common-control-patterns-for-visual-studio"></a>適用於 Visual Studio 的通用控制項模式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> 通用控制項

### <a name="overview"></a>總覽
 通用控制項組成大部分的 Visual Studio 中的使用者介面。 在 Visual Studio 介面中使用的最常見控制項應該遵循[Windows 桌面互動的指導方針](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)。 本文件旨在說明 Visual Studio，並涵蓋特殊的情況下或擴充這些 Windows 指導方針的詳細資料。

#### <a name="common-controls-in-this-topic"></a>本主題中的通用控制項

-   [捲軸](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

-   [輸入的欄位](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

-   [下拉式方塊和下拉式清單](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

-   [核取方塊](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

-   [選項按鈕](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

-   [群組的畫面格](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

-   [文字控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

-   [按鈕和超連結](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

-   [樹狀檢視](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>視覺化樣式
 首先要考慮設定控制項的樣式時是否將控制項使用中佈景主題 UI 中。 標準的 UI 中的控制項為非佈景主題 UI，且必須遵照[一般的 Windows 桌面樣式](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx)，這表示它們不重新範本化，而且應該會出現在其預設控制項外觀。

-   **標準 （公用程式） 對話方塊：** 未配置其佈景主題。 執行不重新範本。 使用基本的控制項樣式的預設值。

-   **工具視窗、 文件編輯器、 設計介面和反映一定主題的對話方塊：** 使用特製化佈景主題的外觀，使用色彩服務。

###  <a name="BKMK_Scrollbars"></a> 捲軸
 捲軸所應遵循[常見 Windows 捲軸的互動模式](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx)除非它們會夾帶內容的詳細資訊，例如程式碼編輯器中。

###  <a name="BKMK_InputFields"></a> 輸入的欄位
 典型的互動行為，請遵循[文字方塊中的 Windows 桌面方針](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx)。

#### <a name="visual-style"></a>視覺化樣式

-   輸入的欄位不能在公用程式的對話方塊中設定樣式。 使用基本內建控制項的樣式。

-   佈景主題的輸入的欄位應該只用在佈景主題的對話方塊和工具視窗。

#### <a name="specialized-interactions"></a>特製化的互動

-   唯讀欄位會顯示有但 （使用中） 的預設前景灰色 （停用） 背景。

-   所需欄位應有**\<需要 >** 做為其中的標準。 您不應該變更除了在少數情況下的背景色彩。

-   錯誤驗證：請參閱[通知和適用於 Visual Studio 的進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

-   輸入的欄位都應該調整大小以符合內容，不以符合在其中，它們會顯示，視窗的寬度，也不能以任意符合長的欄位，例如路徑的長度。 長度可能是向使用者表示的欄位中允許多少個字元的限制。

     ![不正確的輸入的欄位控制項寬度](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707年 01_IncorrectInputFieldControl") **不正確的輸入的欄位長度：不可能的名稱會是此種長度。**

     ![更正的輸入的欄位控制項寬度](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707年 02_CorrectInputFieldControl") **更正輸入欄位長度：輸入的欄位是合理的寬度，如預期的內容。**

###  <a name="BKMK_ComboBoxesAndDropDowns"></a> 下拉式方塊和下拉式清單
 典型的互動行為，請遵循[下拉式清單和下拉式方塊的 Windows 桌面方針](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx)。

#### <a name="visual-style"></a>視覺化樣式

-   在 公用程式的對話方塊，請執行不重新範本控制項。 使用基本內建控制項的樣式。

-   在佈景主題 UI 中，下拉式方塊和下拉式清單，請遵循標準的佈景主題的控制項。

#### <a name="layout"></a>配置
 下拉式方塊和下拉式清單應該調整大小以符合內容，不以符合在其中，它們會顯示，視窗的寬度，也不能以任意符合長的欄位，例如路徑的長度。

 ![不正確的卸除&#45;下配置](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707年 03_IncorrectDropDownLayout")

 **下拉式清單控制項的不正確的欄位長度**

 ![正確的拖放&#45;下配置](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707年 04_CorrectDropDownLayout")

 **下拉式清單控制項的正確的欄位長度**

###  <a name="BKMK_CheckBoxes"></a> 核取方塊
 典型的互動行為，請遵循[核取方塊的 Windows 桌面方針](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx)。

#### <a name="visual-style"></a>視覺化樣式

-   在 公用程式的對話方塊，請執行不重新範本控制項。 使用基本內建控制項的樣式。

-   在佈景主題 UI 中，核取方塊會遵循標準的佈景主題的控制項。

#### <a name="specialized-interactions"></a>特製化的互動

-   核取方塊的互動必須永遠不會快顯對話方塊，或瀏覽至另一個區域。

-   對齊文字的第一行基準線的核取方塊。

     ![不正確的核取方塊對齊](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707年 05_IncorrectCheckBoxAlign") **不正確的核取方塊對齊方式：文字置中 核取方塊。**

     ![修正核取方塊對齊](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707年 06_CorrectCheckBoxAlign") **修正核取方塊對齊方式：第一行文字的基準線對齊核取方塊。**

###  <a name="BKMK_RadioButtons"></a> 選項按鈕
 典型的互動行為，請遵循[選項按鈕的 Windows 桌面方針](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx)。

#### <a name="visual-style"></a>視覺化樣式
 在公用程式對話方塊中，執行樣式選項按鈕。 使用基本內建控制項的樣式。

#### <a name="specialized-interactions"></a>特製化的互動
 您不需要使用在群組範圍，來括住選項選擇。

###  <a name="BKMK_GroupFrames"></a> 群組的畫面格
 典型的互動行為，請遵循[Windows 桌面的指導方針群組框架](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx)。

#### <a name="visual-style"></a>視覺化樣式
 在公用程式對話方塊中，執行樣式群組框架。 使用基本內建控制項的樣式。

#### <a name="layout"></a>配置

-   您不需要使用群組框來括住選項選擇，除非您需要維護群組差別，在於緊密的版面配置。

-   永遠不會使用單一控制項群組框架。

-   有時候會接受使用水平尺規，而不是群組的範圍容器。

##  <a name="BKMK_TextControls"></a> 文字控制項

### <a name="labels"></a>標籤

#### <a name="active-label-state"></a>作用中的標籤狀態

##### <a name="utility-standard-dialogs"></a>公用程式 （標準） 的對話方塊）

-   一般情況下，請依照下列控制項標籤的 Windows 桌面指引。

-   在 公用程式的對話，標籤會顯示非粗體，標準環境的字型和文字色彩。 請參閱[字型和格式適用於 Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)。

-   省略符號應永遠遵循標籤。

##### <a name="signature-themed-dialogs"></a>簽章 （佈景主題） 的對話方塊）
 Label 控制項可能會變成粗體或淺灰色。

#### <a name="disabled-label-state"></a>已停用的標籤狀態
 標籤應反映出它們相關聯控制項的外觀。 比方說，如果已停用相關聯的控制項，然後標籤應該會出現灰色並停用。 這通常由作業系統，而且需要特別的處置。

#### <a name="dynamic-labels"></a>動態標籤
 根據目前的選取範圍的動態標籤變更。 可能的話，請在主要/詳細資料的版面配置中使用動態的標籤，來協助使用者了解顯示的資訊適用於特定選取項目和非一般的資訊。

 ![使用具有動態內容的動態標籤](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702 01_DynamicLabel")

 **搭配 動態內容的動態標籤的範例**

#### <a name="instructional-text"></a>說明文字
 有些介面項目，受益於指示的文字，以協助使用者了解 UI 用途，或指出要採取的動作。

-   指示文字，在對話方塊頂端最常見的是，但可以出現在其他區域，以便在複雜的控制項群組的指示。

-   說明文字為非互動式的但可能包含 [說明] 主題的超連結。

-   使用指示文字，謹慎且只需要時。

##### <a name="formatting"></a>格式化
 說明文字應環境字型，標準 （非佈景主題） 的控制項文字。 請參閱[字型和格式適用於 Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)。

 如需撰寫的說明文字的詳細資訊，請參閱[UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。

 ![說明文字格式化](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702 02_InstructionalTextFormatting")

 **Visual Studio 對話方塊中的說明文字**

#### <a name="informational-text"></a>資訊文字
 資訊文字是可讓使用者的其他資訊的文字。 可能是靜態或動態的或用來做為通知。 它一律是唯讀的但如果它是適用於使用者可以複製的資訊，動態文字應該放在控制項容器，例如唯讀文字欄位中。

##### <a name="dynamic-context-specific-text"></a>動態 （特定內容） 文字
 根據內容，例如當使用者切換焦點的動態資訊文字變更。 通常，但不是一定與動態標籤成對的動態內容。

 ![動態資訊文字](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702 03_InformationalDynamicText")

 **動態資訊文字變更，視內容而定。**

##### <a name="formatting"></a>格式化
 有兩種方式來顯示唯讀文字欄位： 直接在 UI 上的其中一個介面 （如上所述），或包含在另一個控制項，例如群組框架或文字的方塊。 其中一個是正確根據這種情況。 這是由功能設計工具，來決定如何顯示唯讀資訊。

 文字可以是唯讀的文字方塊內。 這通常表示內容可以選取和複製，但無法編輯。

 ![參考用文字格式讀取&#45;只有欄位](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702 04_InformationalFormatting")

 **唯讀欄位的格式設定的資訊文字**

#### <a name="watermarks"></a>浮水印
 雖然文字可能會相同，浮水印和說明文字之間的差異是當控制項/視窗不是空的並說明文字都會繼續顯示在任何時候，浮水印會取代內容。

 是空的視窗或控制項時，應該使用浮水印。 它們會指出哪些項目要完成來填入區域，而且可能包含動作連結，以開啟相關的 windows，例如拖曳來源。

##### <a name="visual-style"></a>視覺化樣式

- 浮水印應該是水平置中視窗內。

- 浮水印應該中心對齊不靠左對齊。

- 浮水印可能垂直置中或位於最上方的區域。 如果位於最上方的區域，必須有足夠的空間上述以便浮水印凸顯出來。

- 使用`Environment.GrayText`色彩語彙基元和標準環境字型。 超連結應該使用標準的超連結共用權杖： `Environment.PanelHyperlink`， `Environment.PanelHyperlinkHover`， `Environment.PanelHyperlinkPressed`，和`Environment.PanelHyperlinkDisabled`。

- 浮水印不能選取的背景

- 可能的話，包含可協助使用者開始將浮水印的連結。

  ![設計師視窗中的文字加上浮水印](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702 05_Watermark1")

  ![浮水印文字的工具視窗中](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702 06_Watermark2")

  **在 Visual Studio 中的浮水印文字的範例**

##  <a name="BKMK_ButtonsAndHyperlinks"></a> 按鈕和超連結

### <a name="overview"></a>總覽
 按鈕和連結控制項 （超連結） 應該遵循[超連結的基本 Windows 桌面指引](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx)使用量和字詞，調整大小、 間距。

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
 ![下一個狀態訊息的資訊列命令連結](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703 01_CommandLinkInfobar")

 **在下一個狀態訊息的資訊列中使用的命令連結**

 ![使用 CodeLens 快顯視窗中的連結](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703 02_LinksInCodeLens")

 **使用 CodeLens 快顯視窗中的連結**

 ![做為次要命令使用的連結](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")

 **用於第二個命令按鈕會吸引太多加重視的其中的連結**

### <a name="common-buttons"></a>一般按鈕

#### <a name="text"></a>文字
 請依照下列中的撰寫指導方針[UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。

#### <a name="visual-style"></a>視覺化樣式

##### <a name="standard-dialogs"></a>標準對話方塊
 在 Visual Studio 中的大部分按鈕會出現在標準對話方塊，並且應該不能設定樣式。 它們應該反映出按鈕的標準外觀，如作業系統所指定。

##### <a name="themed"></a>佈景主題
 在某些情況下，按鈕可能用於已設定樣式的 UI 中，這些按鈕必須有適當的樣式。 請參閱[對話方塊](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)佈景主題控制項上的資訊。

### <a name="special-buttons"></a>特殊的按鈕

#### <a name="browse-buttons"></a>瀏覽... 按鈕
 **[瀏覽...]** 按鈕使用中格線、 對話方塊和工具視窗和其他非強制回應的 UI 項目。 它們會顯示在控制項填入值，可協助使用者選擇器。 有兩種變化，此按鈕時，完整和簡短。

 ![Long&#91;瀏覽...&#93;按鈕](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703 04_BrowseLong")

 **長的 [瀏覽...] 按鈕**

 ![簡短的省略符號&#45;只&#91;瀏覽...&#93;按鈕](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703 05_BrowseShort")

 **僅限省略符號的簡短的 [...] 按鈕**

 使用僅限省略符號的簡短按鈕的時機：

- 如果有一個以上長 **[瀏覽...]** 在對話方塊中，例如數個欄位進行瀏覽 按鈕。 使用簡短的 **[...]** 針對每個以避免這種情況下所建立令人困惑的存取金鑰 按鈕 (**（& s) 瀏覽**並**B & 覽**相同的對話方塊中)。

- 在嚴格的對話方塊中，或將長的按鈕沒有合理的地方。

- 如果按鈕會出現在方格控制項。

  使用 [] 按鈕的指導方針：

- 請勿使用存取金鑰。 若要存取它使用鍵盤，使用者必須從相鄰的控制項索引標籤。 請確定定位順序，欄位將會填滿之後，立即就會任何瀏覽 按鈕。 永遠不會使用底線字元下方的第一個週期。

- 設定 Microsoft Active Accessibility (MSAA)**名稱**屬性設**瀏覽...** （包含省略符號） 讓，螢幕助讀程式會朗讀它像是 [瀏覽]，而不"點-點-點 」 或 「 週期-期間-期間。 」 對於受管理的控制項，這表示設定**AccessibleName**屬性。

- 永遠不會使用省略符號 **[...]** 按鈕以外的瀏覽動作。 例如，如果您需要 **[新增...]** 按鈕，但沒有足夠的空間，文字、，然後需要重新設計對話方塊。

##### <a name="sizing-and-spacing"></a>調整大小和間距
 ![調整大小&#91;瀏覽...&#93;按鈕](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703 06_BrowseSizing")

 **調整 [瀏覽...] 按鈕**

 ![間距&#91;瀏覽...&#93;按鈕](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703 07_BrowseSpacing")

 **[瀏覽...] 按鈕的間距**

#### <a name="graphical-buttons"></a>圖形化的按鈕
 某些按鈕應該一律使用圖形化映像，也絕對不要包含文字，以節省空間，並避免當地語系化問題。 這些通常可在 欄位選擇器和其他可排序的清單。

> [!NOTE]
>  使用者需要這些按鈕 （沒有存取金鑰） 索引標籤，因此將它們放在合理的順序。 將按鈕的 name 屬性對應至花費，讓螢幕助讀程式正確地解譯按鈕動作的動作。

|||
|-|-|
|新增|![Graphical "Add" button](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703-08_ButtonAdd")|
|移除|![Graphical "Remove" button](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703-09_ButtonRemove")|
|全部加入|![圖形 [全部加入] 按鈕](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703 10_ButtonAddAll")|
|全部移除|![Graphical "Remove All" button](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703-11_ButtonRemoveAll")|
|上移|![圖形的 「 上移 按鈕](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703 12_ButtonMoveUp")|
|下移|![圖形 [下移] 按鈕](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703 13_ButtonMoveDown")|
|刪除|![Graphical "Delete" button](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703-14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>調整大小和間距
 調整大小的圖形化的按鈕的簡短版本一樣 **[瀏覽...]** 按鈕 （26 x 23 像素為單位）：

 ![使用或不透明的色彩顯示的按鈕](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")

 **在按鈕上，使用和不透明的色彩顯示的圖形影像的外觀**

### <a name="hyperlinks"></a>超連結
 超連結是適合用來巡覽為基礎的動作，例如開啟說明主題，強制回應對話方塊中或新的精靈。 如果命令使用超連結，它應該一律 ui 會顯示可見及明顯的變更。 一般情況下，認可至動作 （例如 [取消]，儲存和刪除） 的動作是更好溝通使用按鈕中。

#### <a name="writing-style"></a>撰寫樣式
 請遵循[使用者介面文字的 Windows 桌面指引](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)。 請勿使用 「 了解更多關於，」 「 告訴我更多關於，」 或 「 取得協助與這個"片語。 相反地，片語解答的說明內容的主要問題方面的說明連結文字。 比方說，「**方式 [伺服器總管] 來新增伺服器？**"

#### <a name="visual-style"></a>視覺化樣式

-   應該一律使用超連結[The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。 如果超連結的樣式不正確，它會閃爍紅色作用時，或顯示不同的色彩後正在瀏覽。

-   不包含底線，除非連結處於句子片段內完整的句子，例如浮水印上來狀態的控制項。

-   停留時，應該不會出現底線。 相反地，連結是作用中使用者的意見反應是稍微色彩變更，而適當的連結資料指標。

##  <a name="BKMK_TreeViews"></a> 樹狀檢視

### <a name="overview"></a>總覽
 樹狀檢視會提供一種方式組織複雜列出成父子式群組。 使用者可以展開或摺疊父群組，來顯示或隱藏基礎的子項目。 可以選取樹狀檢視中的每個項目，以提供進一步的動作。

 本主題涵蓋可接受的使用、 適當的設計和樹狀檢視的功能。

#### <a name="in-this-topic"></a>本主題內容

-   [視覺化樣式](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

-   [互動](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

###  <a name="BKMK_TreeViewVisualStyle"></a> 視覺化樣式

#### <a name="expanders"></a>展開器
 Windows 和 Visual Studio 所使用的展開器設計應該符合樹狀檢視控制項。 每個節點使用 expander 控制項來顯示或隱藏基礎項目。 使用 expander 控制項的使用者可能會遇到 Windows 和 Visual Studio 內的不同的樹狀檢視中提供一致性。

 ![更正樹狀檢視控制項](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **使用 expander 控制項的樹狀檢視節點的正確： 適當的樣式**

 ![不正確的樹狀檢視節點](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705 2_TreeViewIncorrect1")

 **不正確： 的樹狀檢視節點不適當的樣式**

#### <a name="selection"></a>選取
 在樹狀檢視中選取節點時，反白顯示應該展開成完整的樹狀檢視控制項的寬度。 這有助於使用者清楚地識別他們選取了哪一個項目。 選取範圍色彩應反映出目前的 Visual Studio 佈景主題。

 ![更正樹狀檢視控制項](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **正確： 反白顯示選取之節點的符合整個樹狀檢視控制項的寬度。**

 ![不正確的樹狀檢閱反白顯示](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705 3_TreeViewIncorrect2")

 **不正確： 反白顯示所選節點無法容納整個樹狀檢視控制項的寬度。**

#### <a name="icons"></a>圖示
 圖示只有他們協助以視覺化方式識別項目之間的差異的情況下，只應該在樹狀檢視控制項中使用。 一般情況下，圖示應該只能用於異質性清單圖示，執行區分項目類型的資訊。 同質的清單中使用的圖示通常視為非搜尋，應該予以避免。 在此情況下 （父系） 中的 [群組] 圖示可傳達其內的項目的類型。 此規則的例外狀況是如果圖示是動態的而用來指示狀態。

#### <a name="scroll-bars"></a>捲軸
 如果內容符合樹狀檢視控制項一律應隱藏捲軸。 它是可接受的捲軸在可捲動視窗中會隱藏，或具有半透明和時包含樹狀檢視中的視窗有焦點，顯示或樹狀結構的滑鼠停留在檢視本身。

 ![樹狀檢視含捲軸](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705 4_Scrollbars")

 **因為內容已超出限制的樹狀檢視控制項，則會顯示這兩個垂直和水平捲軸。**

###  <a name="BKMK_TreeViewInteractions"></a> 互動

#### <a name="context-menus"></a>操作功能表
 在樹狀檢視節點可能會顯示內容功能表中的子功能表選項。 通常，這就會發生當使用者以滑鼠右鍵按一下項目，或在與所選取項目的 Windows 鍵盤上按下功能表鍵。 請務必確定節點取得焦點，然後選取。 這有助於使用者識別的子功能表屬於哪一個項目。

 ![選取的樹狀節點和操作功能表](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705 5_ContextMenu")

 **已選取的已產生的項目來通知使用者的內容功能表提升焦點的項目。**

#### <a name="keyboard"></a>鍵盤
 樹狀檢視中應提供選取項目 」 和 「 展開/摺疊節點使用鍵盤的能力。 這可確保瀏覽符合我們的協助工具需求。

##### <a name="tree-view-control"></a>樹狀檢視控制項
 Visual Studio 樹狀目錄控制項應該遵循一般的鍵盤瀏覽：

-   **向上箭號：** 樹狀結構中向上移動選取項目

-   **向下箭號：** 藉由移動樹狀結構下的選取項目

-   **向右箭頭：** 展開樹狀結構中的節點

-   **向左箭號：** 摺疊樹狀結構中的節點

-   **輸入金鑰：** 起始、 載入、 執行選取的項目

##### <a name="trid-tree-view-and-grid-view"></a>Trid （樹狀檢視和格線檢視）
 Trid 控制項是複雜的控制項，其中包含 grid 內的樹狀檢視。 展開、 摺疊，並瀏覽樹狀目錄中應該遵守相同的鍵盤命令，以樹狀檢視，具有下列功能：

- **向右箭頭：** 展開節點。 節點已展開之後，則應繼續瀏覽至最接近的資料行右側。 瀏覽應該停止的資料列結尾。

- **索引標籤：** 瀏覽至最接近的儲存格右邊。  在資料列的結束時，瀏覽會繼續下一個資料列。

- **Shift + 索引標籤：** 瀏覽至最接近的資料格左邊。  開頭的資料列時，瀏覽會繼續在先前的資料列中最右邊的儲存格。

  ![在 Visual Studio 中的 Trid 控制項](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705 6_Trid")

  **在 Visual Studio 中的 trid 控制項**
