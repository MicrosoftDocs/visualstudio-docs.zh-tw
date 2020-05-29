---
title: Visual Studio 的影像和圖示 |Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e72d0ce7435a067ef9aa16ccc5b2daa7602926bf
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184818"
---
# <a name="images-and-icons-for-visual-studio"></a>適用於 Visual Studio 的影像和圖示
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Visual Studio 中的影像使用
 建立插圖之前，請考慮使用[Visual Studio 影像庫](https://www.microsoft.com/download/details.aspx?id=35825)中的1000個以上影像。

### <a name="types-of-images"></a>影像類型

- **圖示**。 出現在命令、階層、範本等中的小型影像。 Visual Studio 中使用的預設圖示大小為 16x16 PNG。 映射服務所產生的圖示會自動產生 HDPI 支援的 XAML 格式。

    > [!NOTE]
    > 在功能表系統中使用影像時，您不應該為每個命令建立圖示。 請參閱[Visual Studio 的功能表和命令](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)，查看您的命令是否應該取得圖示。

- **圖表.** 在對話方塊的預覽區域中使用的影像，例如 [新增專案] 對話方塊。

- **對話方塊影像。** 出現在對話方塊或嚮導中的影像，可做為描述性圖形或訊息指示器。 不常使用，而且只有在必要時才能說明很棘手的概念或取得使用者的注意（警示、警告）。

- **動畫影像。** 用於進度指標、狀態列和操作對話方塊。

- **連筆.** 用來指出是否允許作業使用滑鼠，也就是可以卸載物件的位置等等。

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>圖示設計

### <a name="overview"></a>概觀
 Visual Studio 會使用具有清楚幾何的現代化樣式圖示，以及正面/負面（淺色/深色）的50/50 平衡，並使用直接易懂的比喻。 重要的圖示設計重點中心圍繞清楚、簡化和內容。

- **清楚明瞭：** 專注于提供圖示其意義和 individuality 的核心比喻。

- **簡化：** 將圖示縮小為其核心意義-取得主題，只包含必要的元素，而不樸素。

- 內容 **：** 在概念開發期間考慮圖示符號的所有層面，這在決定哪些元素構成圖示的核心比喻時非常重要。

  有了圖示，有數個設計重點可避免：

- 請不要使用表示 UI 元素的圖示（如果適用的話）。 當 UI 元素既不是通用、明顯且唯一時，請選擇更抽象或符號方法。

- 請勿將一般專案（例如檔、資料夾、箭號和放大鏡）過度用。 只有在圖示意義有必要時，才使用這類元素。 例如，右邊的放大鏡應該只表示搜尋、流覽和尋找。

- 雖然有些舊版的圖示元素會維持使用觀點，但不會建立具有觀點的新圖示，除非該元素在沒有的情況下缺乏清晰的。

- 不要在圖示中 cram 太多資訊。 容易辨識或學習為可辨識符號的簡單映射，比過度複雜的影像更有用。 圖示無法分辨整個案例。

### <a name="icon-creation"></a>建立圖示

#### <a name="concept-development"></a>概念開發
 Visual Studio 在其 UI 中具有各種不同的圖示類型。 在開發期間仔細考慮圖示類型。 請勿針對您的圖示元素使用不清楚或不常見的 UI 物件。 在這些情況下選擇符號，例如使用智慧標籤圖示。 請注意，左邊的 abstract 標記意義比右邊的不明確、以 UI 為基礎的版本更為明顯：

|||
|-|-|
|**正確使用符號圖像**|**符號圖像的使用不正確**|
|![正確的智慧標籤圖示](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![不正確的智慧標籤圖示](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 在某些情況下，標準、容易辨識的 UI 元素會對圖示運作良好。 [新增] 視窗是其中一個範例：

|||
|-|-|
|**更正圖示中的 UI 元素**|**圖示中的 UI 元素不正確**|
|![正確的加入視窗圖示](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![不正確的加入視窗圖示](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 請不要使用檔作為基底元素，除非它是圖示意義的必要專案。 在 [新增檔] （下方）沒有檔元素的情況下，會遺失意義，而 with Refresh 則不需要傳達意義。

|||
|-|-|
|**正確使用檔圖示**|**檔圖示的使用不正確**|
|![正確的文件圖示](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![不正確的文件圖示](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 「顯示」的概念應該以最能說明所顯示內容的圖示來表示，例如使用「顯示所有檔案」範例。 如有必要，可以使用鏡頭比喻來表示 "view" 的概念，例如使用資源檢視範例。

|||
|-|-|
|**出現**|**視圖**|
|![顯示圖示](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![檢視圖示](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 右邊的放大鏡圖示應僅代表搜尋、尋找和流覽。 具有加號或負號的左邊變體，應僅代表放大/縮小。

|||
|-|-|
|**Search**|**貼近**|
|![搜尋圖示](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![[縮放] 圖示](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 在樹狀檢視中，請勿同時使用資料夾圖示和修飾詞。 當可用時，只使用修飾詞。

|||
|-|-|
|**正確的樹狀檢視圖示**|**不正確的樹狀檢視圖示**|
|![正確的樹狀檢視圖示 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![正確的樹狀檢視圖示 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![不正確的樹狀檢視圖示 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![不正確的樹狀檢視圖示 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>樣式詳細資料

#### <a name="layout"></a>Layout
 標準16x16 圖示所顯示的堆疊元素：

 ![16x16 圖示的版面配置堆疊](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />16x16 圖示的版面配置堆疊

 狀態通知元素較適合當做獨立圖示使用。 不過，有些內容是應該在基底專案上堆疊通知，例如使用工作完成圖示：

 ![Visual Studio 中的獨立通知](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />獨立通知圖示

 ![工作完成圖示](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />工作完成圖示

 專案圖示通常是包含多種大小的 .ico 檔案。 大部分的16x16 圖示都包含相同的元素。 32x32 版本具有更多詳細資料，包括適用的專案類型。

 ![Visual Studio 中的專案圖示](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />VB Windows 控制項程式庫專案圖示、16x16 和32x32

 將圖示置中在其圖元框架內。 如果無法這麼做，請將圖示對齊框架的上方和/或右方。

 ![圖示位於像素框架的中央](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />圖示位於像素框架的中央

 ![圖示對齊像素框架的右上方](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />對齊框架右上方的圖示

 ![圖示位於像素框架的中央並靠上對齊](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />圖示置中並對齊框架的頂端

 若要達到理想的對齊和平衡，請避免使用動作圖像來阻礙圖示的基底元素。 將圖像放在基底元素的左上角附近。 新增額外元素時，請考慮圖示的對齊和平衡。

|||
|-|-|
|**正確的對齊和平衡**|**不正確的對齊和餘額**|
|![正確的圖示平衡和對齊方式](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![不正確的圖示平衡和對齊方式](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 請確定共用元素且在集合中使用的圖示大小同位。 請注意，在不正確的配對中，圓形和箭號會大到不相符。

|||
|-|-|
|**正確的大小同位**|**大小不正確**|
|![正確的圖示大小和同位](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![不正確的圖示大小和同位](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 使用一致的行和視覺權數。 使用並排比較，評估您所建立的圖示如何與其他圖示相比較。 絕對不要使用整個16x16 框架，請使用15x15 或更小的畫面。 負到正面（深色到淺色）比例應為50/50。

|||
|-|-|
|**更正負到正的比率**|**負到正的比率不正確**|
|![正確的圖示視覺權數 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![正確的圖示視覺權數 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![正確的圖示視覺權數 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![不正確的圖示視覺加權](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 使用簡單、可比較的形狀和互補角度來建立您的元素，而不會犧牲元素完整性。 盡可能使用45°或90度的角度。

 ![正確的圖示角度](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>檢視方塊
 讓圖示保持清楚明瞭。 只有在必要時，才使用透視圖和光源。 雖然應避免使用 icon 元素的觀點，但有些元素無法辨識。 在這種情況下，有風格的觀點會傳達元素的清晰度。

 ![3 點透視圖](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />3 點透視圖

 ![1 點透視圖](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />1 點透視圖

 大部分的專案都應該面向或向右傾斜：

 ![圖示靠右對齊](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 只有在為物件新增必要的清晰度時，才使用光源。

|||
|-|-|
|**正確的燈來源**|**不正確的燈來源**|
|![正確的圖示光源](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![不正確的圖示光源](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 僅使用大綱來增強可讀性，或更有效地溝通比喻。 負正值（深色）餘額應為50/50。

|||
|-|-|
|**使用大綱的正確用法**|**外框的使用不正確**|
|![正確的外框](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![不正確的外框](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>圖示類型
 **Shell 和命令列**圖示包含下列三個元素：一個基底、一個修飾詞、一個動作或一個狀態。

 ![Shell 和命令列圖示的範例](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Shell 和命令列圖示的範例

 **工具視窗命令列**圖示包含不超過三個元素：一個基底、一個修飾詞、一個動作或一個狀態。

 ![工具視窗命令列圖示的範例](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />工具視窗命令列圖示的範例

 **樹狀檢視消除歧義**圖示包含不超過三個下列元素：一個基底、一個修飾詞、一個動作或一個狀態。

 ![樹狀檢視消除歧義圖示的範例](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />樹狀檢視消除歧義圖示的範例

 以**狀態為基礎的值分類法**圖示處於下列狀態： [作用中]、[已停用] 和 [非作用中停用]。

 ![以狀態為基礎的值分類法圖示範例](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />以狀態為基礎的值分類法圖示範例

 **IntelliSense**圖示由不超過三個元素所組成：一個基底、一個修飾詞和一個狀態。

 ![IntelliSense 圖示的範例](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />IntelliSense 圖示的範例

 **小型（16x16）專案**圖示不應有兩個以上的元素：一個基底和一個修飾詞。

 ![小型（16x16）專案圖示的範例](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16 專案圖示 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16 專案圖示 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />小型（16x16）專案圖示的範例

 **大型（32x32）專案**圖示由不超過下列四個元素所組成：一個基底、一個至兩個修飾詞和一個語言重迭。

 ![大型（32x32）專案圖示的範例](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />大型（32x32）專案圖示的範例

### <a name="production-details"></a>生產環境詳細資料
 所有新的 UI 元素都應該使用 Windows Presentation Foundation （WPF）來建立，而所有適用于 WPF 的新圖示應採用32位的 PNG 格式。 24位 PNG 是不支援透明度的舊版格式，因此不建議用於圖示。

 以 96 DPI 儲存解析度。

#### <a name="file-types"></a>檔案類型

- **32-BIT PNG：** 圖示的慣用格式。 不失真的資料壓縮檔案格式，可以儲存單一點陣（圖元）影像。 32位 PNG 檔案支援 Alpha 色溝透明度、gamma 校正和交錯。

- **32-BIT BMP：** 適用于非 WPF 控制項。 32-bit BMP 也稱為 XP 或 high color，這是一種 RGB/A 影像格式，這是具有 Alpha 色板透明度的真彩色影像。 Alpha 色板是 Adobe Photoshop 中指定的透明度層，然後儲存在點陣圖內做為額外的（第四個）色頻。 將圖稿生產環境中的黑色背景新增至所有32位的 BMP 檔案，以提供有關色彩深度的快速視覺提示。 這個黑色背景代表要在 UI 中遮罩的區域。

- **32-位 .ico：** 適用于專案圖示和加入專案。 所有的 .ICO 檔案都是32位的 true 色彩，具有 Alpha 色頻透明度（RGB/A）。 因為 .ICO 檔案可以儲存多種大小和色彩深度，所以 Vista 圖示通常會採用包含16x16、32x32、48x48 和256x256 影像大小的 .ICO 格式。 若要在 Windows Explorer 中正確顯示，必須針對每個影像大小，將 .ICO 檔案儲存到24位和8位色彩深度。

- **XAML：** 適用于設計介面和 Windows 裝飾項。 XAML 圖示是以向量為基礎的影像檔，支援縮放、旋轉、歸檔和透明度。 它們在現今 Visual Studio 並不常見，但因為其彈性而變得更熱門。

- **SVG**

- **24 位 BMP：** 適用于 Visual Studio 命令列。 一種純色 RGB 影像格式，24位 BMP 是一個圖示慣例，會使用洋紅（R = 255，G = 0，B = 255）做為挖出透明度圖層的色彩索引鍵，以建立一層透明度。 在24位 BMP 中，所有的洋紅色表面都會使用背景色彩來顯示。

- **24 位 GIF：** 適用于 Visual Studio 命令列。 支援透明度的真色彩 RGB 影像格式。 GIF 檔案通常用於 [Wizard] 圖稿和 [GIF 動畫]。

### <a name="icon-construction"></a>圖示結構
 Visual Studio 中最小的圖示大小為16x16。 常見用法的最大值為32x32。 設計圖示時，請記住不要填滿整個16x16、24x24 或32x32 框架。 可以清楚的是，統一的圖示結構對使用者辨識是不可或缺的。 建立圖示時，請遵守下列幾點。

- 圖示應該是清楚、易懂和一致的。

- 最好使用狀態通知元素做為單一圖示，而不是將其堆疊在圖示基底元素的上方。 在某些內容中，UI 可能需要狀態元素與基底元素配對。

- 專案圖示通常是包含數個大小的 .ico 檔案。 只會更新16x16、24x24 和32x32 圖示。 大部分的16x16 和24x24 圖示都會包含相同的元素。 32x32 圖示包含更多詳細資料，包括適用的專案語言類型。

- 若為32x32 圖示，基底元素通常會有2圖元的線條粗細。 1或2圖元的線條粗細可用於詳細元素。 請使用您的最佳判斷，判斷哪一個較合適。

- 16x16 和24x24 圖示的元素之間至少要有1個圖元的間距。 若為32x32 圖示，請在專案之間和修飾詞與基底專案之間使用2個圖元的間距。

  ![圖示的元素間距大小為16x16、24x24 和32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />圖示的元素間距大小為16x16、24x24 和32x32

#### <a name="color-and-accessibility"></a>色彩和協助工具
 Visual Studio 合規性方針需要產品中的所有圖示通過色彩和對比的協助工具需求。 這是透過圖示反轉來達成，而且當您設計時，您應該知道它們會在產品中以程式設計方式反轉。

 如需在 Visual Studio 圖示中使用色彩的詳細資訊，請參閱[使用影像中的色彩](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)。

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>使用影像中的色彩

### <a name="overview"></a>概觀
 Visual Studio 中的圖示主要是單色。 色彩會保留以傳達特定資訊，而不是裝飾。 使用色彩：

- 表示動作

- 若要向使用者通知狀態通知

- 若要指定語言關係

- 區分 IntelliSense 內的專案

### <a name="accessibility"></a>協助工具選項
 Visual Studio 合規性方針要求所有簽入產品的圖示都必須通過色彩和對比的協助工具需求。 Visual language 調色板中的色彩已經過測試，並符合這些需求。

#### <a name="color-inversion-for-dark-themes"></a>深色主題的色彩反轉
 為了讓圖示在 Visual Studio 深色主題中顯示為正確的對比比例，會以程式設計方式套用反轉。 本指南中的色彩已選擇部分，使其正確地反轉。 將色彩限制在此調色板中，或套用反轉時，將會得到無法預期的結果。

 ![已反轉色彩的圖示範例](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />已反轉色彩的圖示範例

### <a name="base-palette"></a>基本調色板
 所有標準圖示都包含三種基本色彩。 圖示不包含漸層或陰影，有一或兩個3D 工具圖示的例外狀況。

|使用方式|Name|值（淺色主題）|色樣|範例|
|-----------|----------|---------------------------|------------|-------------|
|背景/深色|VS BG|424242/66、66、66|![樣本 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![基礎調色盤範例](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|前景/淺色|VS FG|F0EFF1/240239241|![樣本 F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|外框|與 Out|F6F6F6/246246246|![樣本 F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 除了基本色彩以外，每個圖示都可能包含來自擴充調色板的另一個色彩。

### <a name="extended-palette"></a>擴充的調色板

#### <a name="action-modifiers"></a>動作修飾詞
 下列四種色彩表示動作修飾詞所需的動作類型：

|使用方式|Name|值（所有主題）|色樣|
|-----------|----------|--------------------------|------------|
|Positive|VS 動作綠色|388A34/56138、52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Neutral|VS 動作紅色|A1260D/161、38、13|![樣本 A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|中性|VS 動作 Blue|00539C/0、83156|![樣本 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|建立/新增|VS 動作橙色|C27D1A/194156，26|![樣本 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>範例
 綠色用於正動作修飾詞，例如「新增」、「執行」、「播放」和「驗證」。

|||||
|-|-|-|-|
|![執行圖示](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />執行|![執行查詢圖示](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")<br />執行查詢|![播放所有步驟圖示](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")<br />播放所有步驟|![加入控制項圖示](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")<br />加入控制項|

 紅色用於負動作修飾詞，例如 "Delete"、"Stop"、"Cancel" 和 "Close"。

|||||
|-|-|-|-|
|![刪除關聯性圖示](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")<br />刪除關聯性|![刪除資料行圖示](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")<br />刪除欄|![停止查詢圖示](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")<br />停止查詢|![連接離線圖示](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")<br />離線連接|

 藍色會套用至最常以箭號表示的中性動作修飾詞，例如「開啟」、「下一步」、「上一頁」、「匯入」和「匯出」。

|||||
|-|-|-|-|
|![移至欄位圖示](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")<br />移至欄位|![批次檢查&#45;在圖示中](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")<br />批次簽入|![地址編輯器圖示](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")<br />位址編輯器|![關聯編輯器圖示](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")<br />關聯編輯器|

 深色金主要用於 "New" 修飾詞。

|||||
|-|-|-|-|
|![新增專案圖示](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")<br />新增專案|![建立新的圖形圖示](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")<br />建立新圖形|![新增單元測試圖示](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")<br />新增單元測試|![新增清單項目圖示](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")<br />新增清單專案|

#### <a name="special-cases"></a>特殊案例
 在特殊情況下，彩色的動作修飾詞可以單獨使用，做為獨立的圖示。 用於圖示的色彩會反映與圖示相關聯的動作。 此用法僅限於一小部分的圖示，包括：

||||||
|-|-|-|-|-|
|![執行圖示](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />執行|![停止圖示](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")<br />Stop|![刪除圖示](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")<br />刪除|![[儲存] 圖示](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")<br />儲存|![向後巡覽圖示](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")<br />往回導覽|

### <a name="code-hierarchy-palette"></a>程式碼階層調色板

#### <a name="folder"></a>資料夾

|使用方式|Name|值（所有主題）|色樣|範例|
|-----------|----------|--------------------------|------------|-------------|
|資料夾|資料夾|DCB67A/220182122|![樣本 DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![資料夾色彩圖示](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio 語言
 Visual Studio 中所提供的每個通用語言或平臺都有相關聯的色彩。 這些色彩會用於基底圖示，或出現在複合圖示右上角的語言修飾詞上。

|使用方式|Name|值（所有主題）|色樣|
|-----------|----------|--------------------------|------------|
|ASP、HTML、WPF|ASP HTML WPF 藍色|0095D7/0149215|![樣本 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP 紫色|9B4F96/155、79150|![樣本 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS 綠色（VS Action 綠色）|388A34/56138、52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS 紅色|BD1E2D/189、30、45|![樣本 BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS 紫色|672878/103、40120|![樣本 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS 橙色|F16421/241100，33|![樣本 F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB 藍色（VS Action Blue）|00539C/0、83156|![樣本 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS 橙色|E04C06/224、76、6|![樣本 E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|.PY 綠色|879636/135150、54|![樣本 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>具有語言修飾詞的圖示範例

|||||||
|-|-|-|-|-|-|
|![Visual Basic 圖示](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")<br />VB|![C&#35; 圖示](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")<br />C#|![C&#43;&#43; 圖示](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![F&#35; 圖示](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")<br />F#|![JavaScript 圖示](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")<br />JavaScript|![Python 圖示](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")<br />Python|
|![HTML 圖示](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![WPF 圖示](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![ASP 圖示](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![CSS 圖示](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![TypeScript 圖示](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 IntelliSense 圖示使用專有色板。 這些色彩是用來協助使用者快速分辨 IntelliSense 快顯清單中的不同專案。

|使用方式|Name|值（所有主題）|色樣|
|-----------|----------|--------------------------|------------|
|Class、Event|VS 動作橙色|C27D1A/194125，26|![樣本 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|擴充方法，方法，模組，委派|VS 動作紫色|652D90/101、45144|![樣本 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|欄位、列舉專案、宏、結構、聯集數值型別、運算子、介面|VS 動作 Blue|00539C/0、83156|![樣本 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|VS 動作綠色|388A34/56138、52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|常數、例外狀況、列舉專案、對應、對應專案、命名空間、範本、類型定義|背景（VS BG）|424242/66、66、66|![樣本 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>IntelliSense 圖示的範例

||||||
|-|-|-|-|-|
|![IntelliSense 類別圖示](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")<br />類別|![IntelliSense 私用事件圖示](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")<br />私用事件|![IntelliSense 委派圖示](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")<br />代理人|![IntelliSense 方法 Friend 圖示](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")<br />Friend 方法|![欄位圖示](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")<br />欄位|
|![IntelliSense 受保護的列舉項目圖示](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")<br />受保護的列舉專案|![IntelliSense 物件圖示](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")<br />Object|![IntelliSense 範本圖示](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")<br />[範本]|![IntelliSense 例外狀況捷徑圖示](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")<br />例外狀況快捷方式||

### <a name="notifications"></a>通知
 Visual Studio 中的通知是用來表示狀態。 通知選擇區會使用下列四種色彩，以及黑色或白色前景填滿選項，來定義具有下列狀態層級的通知。

|使用方式|Name|值（所有主題）|色樣|
|-----------|----------|--------------------------|------------|
|狀態：中性|通知藍色（VS 藍色）|1BA1E2/27161226|![樣本 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|狀態：正面|通知綠色（VS 綠色）|339933/51153，51|![樣本 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|狀態：負|紅色通知（VS 紅色）|E51400/229、20、0|![樣本 E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|狀態：警告|通知黃色（VS 橙色）|FFCC00/255204、0|![樣本 FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|前景填滿|通知黑色（黑色）|000000/0，0，0|![樣板 &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|前景填滿|通知白（白色）|FFFFFF/255255255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>通知圖示的範例

|||||
|-|-|-|-|
|![警示圖示](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")<br />警示|![警告圖示](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")<br />警告|![完成圖示](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")<br />完成|![停止圖示](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")<br />Stop|