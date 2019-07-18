---
title: 映像和適用於 Visual Studio 的圖示 |Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ba4a5c52bf972236914c06ec9672653fbde9cea
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67891049"
---
# <a name="images-and-icons-for-visual-studio"></a>映像和適用於 Visual Studio 的圖示
## <a name="BKMK_ImageUseInVisualStudio"></a> 在 Visual Studio 中的映像使用
 在之前建立圖檔，請考慮讓使用 1,000 個以上中的映像[Visual Studio 影像程式庫](http://www.microsoft.com/en-my/download/details.aspx?id=35825)。

### <a name="types-of-images"></a>類型的映像

- **圖示**。 會出現在命令、 階層、 範本和等等的小型影像。 在 Visual Studio 中使用的預設圖示大小是 16 x 16 PNG。 自動產生的映像服務的圖示會產生 XAML 格式的 HDPI 支援。

    > [!NOTE]
    > 雖然映像會用於功能表系統，您不應建立為每個命令的圖示。 請參閱[功能表和命令適用於 Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) ，了解您的命令是否應該取得圖示。

- **縮圖。** 在對話方塊中，例如 [新增專案] 對話方塊的 [預覽] 區域中使用的映像。

- **對話方塊的映像。** 會出現在對話方塊或精靈，為具描述性的圖形或訊息指標的影像。 使用常且只在必要說明難理解的概念，或取得使用者的注意力 （警示，警告） 時。

- **動畫的映像。** 用於進度指標、 狀態列和作業的對話方塊。

- **資料指標。** 用來表示作業是否允許使用的滑鼠，其中物件可能會中斷，依此類推。

## <a name="BKMK_IconDesign"></a> 迶蒩飶耵

### <a name="overview"></a>總覽
 Visual Studio 使用現代化樣式圖示，會有全新的幾何和 50/50 兼顧正/負 （淡/濃），並使用直接且容易了解的隱喻。 重要迶蒩飶耵點圍繞在清楚、 簡化方式，以及內容。

- **避免混淆：** 專注於提供圖示，其意義和責難 core 比喻。

- **簡化：** 減少其核心意義圖示-只是必要的項目與任何 frills 取得佈景主題。

- **內容：** 概念在開發期間，這很重要，決定哪些項目構成圖示的核心比喻時，請考慮圖示之角色的所有層面。

  使用圖示，有幾個的設計重點，以避免：

- 請勿使用表示 UI 項目除外，在適當的圖示。 UI 項目是不常見，顯而易見地，也不是唯一時，請選擇較抽象或符號的方法。

- 不過度使用的常見項目，例如文件、 資料夾、 箭號和放大鏡。 使用只在必要圖示的意義時，這類項目。 比方說，向右放大鏡應該指出只搜尋、 瀏覽，並尋找。

- 雖然某些傳統圖示項目會維護使用觀點來看，不建立新圖示透視除非元素缺少清晰度，而不需要它。

- 不 cram 太多資訊圖示。 簡單的映像可以輕鬆地辨識或做為可辨識的符號已了解更適合比過於複雜的映像。 圖示不能反映全貌。

### <a name="icon-creation"></a>建立圖示

#### <a name="concept-development"></a>證明開發
 Visual Studio UI 中有各種不同的圖示類型。 在開發期間，請仔細考慮圖示類型。 請勿使用不明確或不常見的 UI 物件圖示項目的。 選擇符號在這些情況下，例如使用智慧標籤圖示。 請注意，在左側的抽象標記的意義更明顯比右邊含糊不清、 以 UI 為基礎的版本：

|||
|-|-|
|**符號影像的正確用法**|**不正確地使用符號的影像**|
|![正確的智慧標籤圖示](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404年 01_SmartTagCorrect")|![不正確的智慧標籤圖示](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404年 02_SmartTagIncorrect")|

 沒有適合圖示標準且易於辨識的 UI 項目執行工作所在的執行個體。 加入視窗是其中一個範例：

|||
|-|-|
|**正確的圖示中的 UI 項目**|**不正確的圖示中的 UI 項目**|
|![正確的加入視窗圖示](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404年 03_AddWindowCorrect")|![不正確的加入視窗圖示](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404年 04_AddWindowIncorrect")|

 請勿使用文件作為基底的項目，除非它是不可或缺的圖示的意義。 沒有文件 （下方） 的意義上新增文件的項目是遺失，而使用重新整理文件項目為必要通訊的意義。

|||
|-|-|
|**正確使用文件圖示**|**使用不正確的文件圖示**|
|![正確的文件圖示](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404年 05_DocumentIconCorrect")|![不正確的文件圖示](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404年 06_DocumentIconIncorrect")|

 "Show"的概念，都應最能說明顯示的內容，例如與顯示所有檔案的範例一樣的圖示來表示。 功能濾鏡比喻可能用來指出如有必要，例如資源檢視的範例 「 檢視 」 的概念。

|||
|-|-|
|**"Show"**|**"View"**|
|![顯示圖示](../../extensibility/ux-guidelines/media/0404-07_show.png "0404年 07_Show")|![檢視項目圖示](../../extensibility/ux-guidelines/media/0404-08_view.png "0404年 08_View")|

 向右放大半透明效果的圖示應該代表只會搜尋、 尋找和瀏覽。 向左 variant 加號或減號應該代表唯一放大/縮小。

|||
|-|-|
|**"Search"**|**"Zoom"**|
|![搜尋圖示](../../extensibility/ux-guidelines/media/0404-09_search.png "0404年 09_Search")|![顯示比例 圖示](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404年 10_Zoom")|

 在樹狀結構檢視中，請勿使用 [資料夾] 圖示和修飾詞。 在使用時，使用的修飾詞。

|||
|-|-|
|**正確的樹狀檢視圖示**|**不正確的樹狀檢視圖示**|
|![正確的樹狀檢閱圖示&#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404年 11_TreeViewCorrect1") ![正確的樹狀檢閱圖示&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404年 12_TreeViewCorrect2")|![不正確的樹狀檢視項目圖示&#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404年 13_TreeViewIncorrect1") ![不正確的樹狀檢閱圖示&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404年 14_TreeViewIncorrect2")|

### <a name="style-details"></a>樣式的詳細資料

#### <a name="layout"></a>配置
 堆疊項目之標準的 16x16 圖示所示：

 ![16x16 圖示的版面配置堆疊](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404年 15_LayoutStack")<br />16x16 圖示的版面配置堆疊

 狀態通知項目是更好用來做為獨立的圖示。 有的內容，不過，在其中通知應該會堆疊在基底的項目，例如工作完成圖示：

 ![在 Visual Studio 中的獨立通知](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404年 16_StandaloneNotificationIcons")<br />獨立通知圖示

 ![工作完成圖示](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404年 17_TaskComplete")<br />工作完成圖示

 專案圖示通常會包含多個大小的.ico 檔案。 大部分的 16x16 圖示會包含相同的項目。 32x32 版本有更多詳細資料，包括專案類型時適用。

 ![專案 Visual Studio 中的圖示](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404年 18_IconProjectThreeSizes")<br />VB Windows 控制項程式庫專案圖示，16 x 16 及 32 x 32

 置中於像素框架內的圖示。 如果不可行，對齊圖示上方，及/或畫面格的權限。

 ![內置中像素框架的圖示](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404年 19_IconCentered")<br />圖示位於像素框架的中央

 ![圖示對齊像素框架的右上方](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404年 20_IconTopRight")<br />圖示對齊右上方的框架

 ![圖示位於中央且對齊像素框架的頂端](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404年 21_IconTopAlign")<br />圖示位於中央且對齊框架頂端

 若要達到最理想的對齊方式和平衡，避免阻礙的圖示與動作圖像的基底項目。 將放在頂端附近的圖像方的基底的項目。 當加入其他項目，請考慮對齊和圖示的平衡。

|||
|-|-|
|**正確的對齊方式和平衡**|**不正確的對齊方式和平衡**|
|![更正的圖示平衡和對齊](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404年 22_AlignBalanceCorrect")|![不正確的圖示平衡和對齊](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404年 23_AlignBalanceIncorrect")|

 請確定共用的項目和設定中所使用的圖示大小的同位檢查。 請注意，在不正確的配對，圓形和箭號會過大，而且不符合。

|||
|-|-|
|**正確的大小同位檢查**|**不正確的大小同位檢查**|
|![更正的圖示大小和同位檢查](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404年 24_SizeParityCorrect")|![不正確的圖示大小和同位](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404年 25_SizeParityIncorrect")|

 使用一致的列和視覺化的加權。 評估其他圖示到您要建置的圖示比較使用並排顯示的比較方式。 永遠不會使用整個 16 x 16 框架中，會使用 15，15 倍或更小。 負-正值 （淺到深） 比例應該 50/50。

|||
|-|-|
|**正確的負數-正數比例**|**不正確的負數-肯定比率**|
|![更正的圖示視覺加權&#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404年 26_VisualWeightCorrect1")<br /><br /> ![更正的圖示視覺加權&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404年 27_VisualWeightCorrect2")<br /><br /> ![更正的圖示視覺加權&#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404年 28_VisualWeightCorrect3")|![圖示不正確視覺比例](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404年 29_VisualWeightIncorrect")|

 使用簡單、 可比較的圖形和互補的角度來建置您的項目而不會犧牲元素完整性。 請盡可能使用 45 度或 90 度的角度。

 ![更正的圖示角度](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404年 30_IconAnglesCorrect")

#### <a name="perspective"></a>透視圖
 保留清楚且容易了解的圖示。 檢視方塊和光源只在必要時使用。 應避免使用圖示的項目上的觀點來看，雖然某些項目都沒有它無法辨識。 在這種情況下，樣式化的檢視方塊進行通訊的項目清晰度。

 ![3 點透視](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404年 31_3PointPerspective")<br />3 點透視圖

 ![1 點透視](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404年 32_1PointPerspective")<br />1 點透視圖

 大部分的項目應該對向，或向右角：

 ![圖示靠右對齊](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404年 33_AngledRight")

 只有在必要的清晰度加入物件時，才，請使用光源。

|||
|-|-|
|**正確的光源**|**不正確光線的來源**|
|![更正的圖示光源](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404年 34_LightSourcesCorrect")|![不正確的圖示光源](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404年 35_LightSourcesIncorrect")|

 使用外框輪廓，只是用來提高可讀性，或進一步通訊所用的隱喻。 負正 （亮暗色調） 平衡應該 50/50。

|||
|-|-|
|**外框輪廓的正確用法**|**外框輪廓的用法不正確**|
|![修正外框輪廓](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404年 36_OutlinesCorrect")|![不正確的外框輪廓](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404年 37_OutlinesIncorrect")|

#### <a name="icon-types"></a>圖示類型
 **殼層和命令列**圖示包含超過三個下列項目： 一個基底、 一個修飾詞，一個動作或一種狀態。

 ![殼層和命令列圖示的範例](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404年 38_ShellIcons")<br />殼層和命令列圖示的範例

 **工具視窗命令列**圖示包含超過三個下列項目： 一個基底、 一個修飾詞，一個動作或一種狀態。

 ![工具視窗的範例命令列圖示](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404年 39_ToolWindowCommandBarIcons")<br />工具視窗命令列圖示的範例

 **樹狀結構檢視消歧義器**圖示包含超過三個下列項目： 一個基底、 一個修飾詞，一個動作或一種狀態。

 ![樹狀目錄中的範例檢視消歧義器圖示](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404年 40_TreeViewIcons")<br />樹狀目錄中的範例檢視消歧義器圖示

 **狀態為基礎的值分類**圖示存在於下列狀態： 作用中、 停用，作用中及非作用中的已停用。

 ![狀態為基礎的值分類圖示的範例](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404年 41_StateBasedTaxonomy")<br />狀態為基礎的值分類圖示的範例

 **IntelliSense**圖示包含超過三個下列項目： 一個基底、 一個修飾詞和一種狀態。

 ![IntelliSense 圖示的範例](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404年 42_IntelliSenseIcons")<br />IntelliSense 圖示的範例

 **小型 (16 x 16) 專案**圖示應該有不超過兩個項目： 一個基底和一個修飾詞。

 ![小型 (16 x 16) 的範例專案圖示](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404年 43_16x16Project1") ![16x16 專案圖示&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404年 44_16x16Project2") ![16x16 專案圖示&#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404年 45_16x16Project3")<br />小型 (16 x 16) 的範例專案圖示

 **大型 (32x32) 專案**圖示包含不超過四個下列項目： 一個基底 」、 「 一到兩個修飾詞和 「 重疊的一種語言。

 ![大型 (32 x 32) 的範例專案圖示](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404年 46_32x32Project")<br />大型 (32 x 32) 的範例專案圖示

### <a name="production-details"></a>生產環境的詳細資料
 應該使用 Windows Presentation Foundation (WPF) 來建立所有新的 UI 項目和所有新的圖示，WPF 的應該是 32 位元 PNG 格式。 24 位元 PNG 是舊版的格式不支援透明，因此不建議用於圖示。

 將儲存在 96 DPI 的解析度。

#### <a name="file-types"></a>檔案類型

- **32 位元 PNG:** 圖示的慣用的格式。 可以儲存 （像素） 的單一點陣影像不失真的資料壓縮的檔案格式。 32 位元 PNG 檔案支援 alpha 色板透明度、 gamma 修正和交錯式。

- **32 位元 BMP:** 非 WPF 控制項。 也稱為 XP 或高彩，32 位元 BMP 是 RGB/A 映像格式，使用 alpha 色板透明效果的全彩映像。 Alpha 色板為圖層的透明度，然後儲存為其他 （第四個） 點陣圖內 Adobe Photoshop 中指定色頻。 黑色背景會加入插圖來提供快速的視覺提示的色彩深度相關的所有 32 位元 BMP 檔案的實際執行期間。 此黑色背景代表要遮罩時，在 UI 中的區域。

- **32 位元 ICO:** 專案圖示和加入項目。 所有的 ICO 檔案都是 32 位元，則為 true 的色彩 alpha 色板的透明度 (RGB/A)。 因為 ICO 檔案可以儲存多個大小和色彩深度，Vista 圖示通常是 ICO 格式包含 16 x 16、 32 x 32、 48 x 48，以及 256 x 256 影像大小。 若要在 Windows 檔案總管中正確顯示，ICO 檔案必須是儲存-向下鍵即可每個映像大小的 24 位元和 8 位元的色彩深度。

- **XAML:** 設計介面和 Windows 的裝飾項。 XAML 圖示是支援縮放、 旋轉、 歸檔和透明度的向量為基礎的映像檔案。 他們目前不在 Visual Studio 中常見，但因為其彈性越來越受歡迎。

- **SVG**

- **24 位元 BMP:** Visual Studio 命令列。 全彩 RGB 影像格式，24 位元 BMP 是透明化的圖層會使用建立洋紅 （R = 255，G = 0，B = 255） 做為 knock 外透明度圖層的色彩索引鍵圖示慣例。 在 24 位元 BMP、 洋紅的所有表面會都顯示使用的背景色彩。

- **24 位元 GIF:** Visual Studio 命令列。 True-色彩 RGB 影像格式，支援透明度。 GIF 檔通常使用於精靈插圖和動畫 GIF。

### <a name="icon-construction"></a>圖示建構
 在 Visual Studio 中的最小圖示大小是 16 x 16。 最大在一般用法是 32 x 32。 請注意，不是用來填滿整個 16 x 16、 24 x 24 或 32 x 32 畫面，設計圖示時。 清晰且統一的圖示建構務必使用者辨識。 建立圖示時，請遵守下列各點。

- 圖示應該是清楚、 可理解的且一致。

- 最好的狀態通知項目做為單一的圖示，而非堆疊頂端的圖示的基底項目。 在某些內容中，UI 可能會要求要搭配基底的項目狀態項目。

- 專案圖示通常包含數種大小的.ico 檔案。 正在更新僅 16 x 16、 24 x 24 和 32x32 圖示。 大部分的 16 x 16] 和 [24x24 圖示會包含相同的項目。 32x32 圖示會包含更多詳細資料，包括適用時，才會進行專案語言類型。

- 32x32 圖示的基底的項目通常會有 2 像素的線條寬度。 1 或 2 像素的線條寬度可以用於詳細資料元素。 若要判斷這是更適合使用您的最佳判斷。

- 必須至少有 1 像素之間的間距 16 x 16 個項目和 24x24 圖示。 32x32 圖示，使用 2 個像素的間距項目以及修飾詞與基底項目。

  ![項目間距的圖示大小 16 x 16、 24 x 24 和 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404年 47_ElementSpacing")<br />16 x 16、 24 x 24 和 32x32，調整大小圖示的項目間距

#### <a name="color-and-accessibility"></a>色彩和協助工具
 Visual Studio 相容性的指導方針會需要在產品中的所有圖示，都將色彩和對比的協助工具需求。 這透過圖示反轉達成，當您在設計時，您應該留意它們在產品中將以程式設計方式反轉。

 如需有關如何在 Visual Studio 圖示中使用色彩的詳細資訊，請參閱[映像中使用色彩](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)。

## <a name="BKMK_UsingColorInImages"></a> 在 映像中使用色彩

### <a name="overview"></a>總覽
 在 Visual Studio 中的圖示為主要單色。 色彩保留來傳遞特定的資訊並不會進行裝飾。 色彩會在使用中：

- 表示動作

- 警示的狀態通知使用者

- 若要指定語言的關係

- IntelliSense 中的項目

### <a name="accessibility"></a>協助工具選項
 Visual Studio 相容性的指導方針會需要的所有圖示都簽入產品傳遞色彩和對比的協助工具需求。 色彩調色盤中的視覺化語言已經過測試，並符合這些需求。

#### <a name="color-inversion-for-dark-themes"></a>深色佈景主題色彩反轉
 若要讓圖示會出現在 Visual Studio 暗色調佈景主題正確比率，反轉會以程式設計方式套用。 本指南中的色彩已選擇部分，讓它們正確地反轉。 這個調色盤中，會限制您使用的色彩，或當反轉套用，您會收到未預期的結果。

 ![已反轉其色彩的圖示的範例](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405年 01_DarkThemeInversion")<br />已反轉其色彩的圖示的範例

### <a name="base-palette"></a>基礎調色盤
 所有的標準圖示會包含三個基底的色彩。 圖示會包含任何漸層，或延伸陰影，但有一或兩個 3D 工具圖示的例外狀況。

|使用量|名稱|值 （淺色佈景主題）|樣本|範例|
|-----------|----------|---------------------------|------------|-------------|
|暗色調背景 /|VS BG|424242 / 66,66,66|![樣本 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![基礎調色盤範例](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405年 02_BasePaletteExample")|
|前景/輕|VS FG|F0EFF1 / 240,239,241|![樣本 F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|外框|VS 出|F6F6F6 / 246,246,246|![樣本 F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 除了基底的色彩，每個圖示可包含一個額外的色彩，從擴充的調色盤。

### <a name="extended-palette"></a>擴充的調色盤

#### <a name="action-modifiers"></a>動作修飾詞
 下列四種色彩表示動作修飾詞所需動作的類型：

|使用量|名稱|值 （所有佈景主題）|樣本|
|-----------|----------|--------------------------|------------|
|正|VS 動作綠色|388A34 / 56,138,52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|負|VS 動作紅色|A1260D / 161,38,13|![樣本 A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|中性語言|VS 動作藍色|00539C / 0,83,156|![樣本 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|建立/新增|VS 動作橙色|C27D1A / 194,156,26|![樣本 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>範例
 綠色用於正向動作修飾詞，例如 「 Add 」，「 執行，」 「 播放 」 和 [驗證]。

|||||
|-|-|-|-|
|![執行圖示](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405年 03_ActionModifierRun")<br />執行|![執行查詢圖示](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405年 04_ExecuteQuery")<br />執行查詢|![播放所有步驟圖示](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405年 05_PlayAllSteps")<br />播放所有步驟|![加入控制項圖示](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405年 06_AddControl")<br />新增控制項|

 紅色用於負動作修飾詞，像 [刪除] 的 [停止]，[取消]，和 「 關閉 」。

|||||
|-|-|-|-|
|![刪除關聯性圖示](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405年 07_DeleteRelationship")<br />刪除關聯性|![刪除資料行圖示](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405年 08_DeleteColumn")<br />刪除欄|![停止查詢圖示](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405年 09_StopQuery")<br />停止查詢|![連接離線圖示](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405年 10_ConnectionOffline")<br />離線連接|

 藍色會套用至相關的動作，最常使用修飾詞表示為箭號，例如 「 開啟，""Next，""Previous，"「 匯入 」 和 「 匯出 」。

|||||
|-|-|-|-|
|![移至欄位圖示](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405年 11_GoToField")<br />移至欄位|![批次核取&#45;圖示](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405年 12_BatchedCheckIn")<br />批次簽入|![地址編輯器圖示](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405年 13_AddressEditor")<br />地址編輯器|![關聯編輯器圖示](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405年 14_AssociationEditor")<br />關聯編輯器|

 深色的金級主要用於 [新增] 修飾詞。

|||||
|-|-|-|-|
|![新的專案圖示](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405年 15_NewProject")<br />新增專案|![建立新的圖形圖示](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405年 16_CreateNewGraph")<br />建立新的圖表|![新的單元測試圖示](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405年 17_NewUnitTest")<br />新的單元測試|![新增清單項目圖示](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405年 18_NewListItem")<br />新清單項目|

#### <a name="special-cases"></a>特殊案例
 在特殊情況下，彩色的動作修飾詞可能是單獨使用為獨立的圖示。 用於圖示的色彩會反映的圖示相關聯的動作。 這種使用僅限於一小部分的圖示，包括：

||||||
|-|-|-|-|-|
|![執行圖示](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405年 03_ActionModifierRun")<br />執行|![停止圖示](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405年 19_Stop")<br />停止|![刪除圖示](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405年 20_Delete")<br />刪除|![儲存圖示](../../extensibility/ux-guidelines/media/0405-21_save.png "0405年 21_Save")<br />儲存|![向後巡覽圖示](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405年 22_NavigateBack")<br />向後巡覽|

### <a name="code-hierarchy-palette"></a>程式碼階層架構調色盤

#### <a name="folder"></a>資料夾

|使用量|名稱|值 （所有佈景主題）|樣本|範例|
|-----------|----------|--------------------------|------------|-------------|
|資料夾|資料夾|DCB67A / 220,182,122|![樣本 DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![資料夾色彩圖示](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405年 23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio 語言
 每個一般的 語言 或 Visual Studio 中提供的平台都有相關聯的色彩。 在基底的圖示，或上會出現在複合圖示的右上角的語言修飾詞，則會使用這些色彩。

|使用量|名稱|值 （所有佈景主題）|樣本|
|-----------|----------|--------------------------|------------|
|ASP，HTML，WPF|ASP HTML WPF 藍色|0095D7 / 0,149,215|![Swatch 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP 紫|9B4F96 / 155,79,150|![樣本 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS 綠色 （VS 動作綠色）|388A34 / 56,138,52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS 紅色|BD1E2D / 189,30,45|![樣本 BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS 紫|672878 / 103,40,120|![樣本 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS 橙色|F16421 / 241,100,33|![樣本 F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB 藍色 （VS 動作藍色）|00539C / 0,83,156|![樣本 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS 橙色|E04C06 / 224,76,6|![樣本 E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY 綠色|879636 / 135,150,54|![樣本 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>語言修飾詞具有圖示的範例

|||||||
|-|-|-|-|-|-|
|![Visual Basic 圖示](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405年 25_VB")<br />VB|![C&#35;圖示](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405年 26_CSharp")<br />C#|![C&#43; &#43;圖示](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405年 27_CPlusPlus")<br />C++|![F&#35;圖示](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405年 28_FSharp")<br />F#|![JavaScript 圖示](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405年 29_JavaScript")<br />JavaScript|![Python 圖示](../../extensibility/ux-guidelines/media/0405-30_python.png "0405年 30_Python")<br />Python|
|![HTML 圖示](../../extensibility/ux-guidelines/media/0405-31_html.png "0405年 31_HTML")<br />HTML|![WPF 圖示](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405年 32_WPF")<br />WPF|![ASP 圖示](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405年 33_ASP")<br />ASP|![CSS 圖示](../../extensibility/ux-guidelines/media/0405-34_css.png "0405年 34_CSS")<br />CSS|![TypeScript 圖示](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405年 35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 IntelliSense 圖示使用獨佔的調色盤。 若要協助使用者快速區分不同的項目 [IntelliSense] 快顯清單中，會使用這些色彩。

|使用量|名稱|值 （所有佈景主題）|樣本|
|-----------|----------|--------------------------|------------|
|事件類別|VS 動作橙色|C27D1A / 194,125,26|![樣本 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|擴充方法，方法中，模組中委派|VS 動作紫|652 D 90 / 101,45,144|![樣本 652d90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|欄位、 列舉項目、 巨集、 結構、 等位的實值型別，運算子，介面|VS 動作藍色|00539C / 0,83,156|![樣本 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|VS 動作綠色|388A34 / 56,138,52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|常數，例外狀況、 列舉項目、 地圖、 地圖項目、 命名空間中，範本中，類型定義|背景 (VS BG)|424242 / 66,66,66|![樣本 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>IntelliSense 圖示的範例

||||||
|-|-|-|-|-|
|![IntelliSense 類別圖示](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405年 36_IntelliSenseClass")<br />類別|![IntelliSense 私用事件圖示](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405年 37_IntelliSensePrivateEvent")<br />私用事件|![IntelliSense 委派圖示](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405年 38_IntelliSenseDelegate")<br />Delegate - 委派|![IntelliSense 方法 friend 圖示](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405年 39_IntelliSenseMethodFriend")<br />方法 Friend|![欄位圖示](../../extensibility/ux-guidelines/media/0405-40_field.png "0405年 40_Field")<br />欄位|
|![IntelliSense 受保護的列舉項目圖示](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405年 41_IntelliSenseProtectedEnumItem")<br />受保護的列舉項目|![IntelliSense 物件圖示](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405年 42_IntelliSenseObject")<br />Object|![IntelliSense 範本圖示](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405年 43_IntelliSenseTemplate")<br />範本|![IntelliSense 例外狀況捷徑圖示](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405年 44_IntelliSenseExceptionShortcut")<br />例外狀況快顯||

### <a name="notifications"></a>通知
 在 Visual Studio 中的通知用來指出狀態。 [通知] 調色盤會使用下列四種色彩，以及黑或白前景填滿選項，定義具有下列狀態層級的通知。

|使用量|名稱|值 （所有佈景主題）|樣本|
|-----------|----------|--------------------------|------------|
|狀態： 中性|通知藍色 （與藍色）|1BA1E2 / 27,161,226|![樣本 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|狀態： 正數|通知綠色 （VS 綠色）|339933 / 51,153,51|![樣本 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|狀態： 負數|通知 Red （VS 紅色）|E51400 / 229,20,0|![樣本 E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|狀態： 警告|通知黃色 （VS 橘色）|FFCC00 / 255,204,0|![樣本 FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|前景填滿|通知黑色 （黑色）|000000 / 0,0,0|![樣本&#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|前景填滿|通知技術 （白皮書）|FFFFFF / 255,255,255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>通知圖示的範例

|||||
|-|-|-|-|
|![警示圖示](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405年 45_Alert")<br />警示|![警告圖示](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405年 48_Warning")<br />警告|![完成圖示](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405年 46_Complete")<br />完成|![停止圖示](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405年 47_Stop")<br />停止|

### <a name="visual-studio-online"></a>Visual Studio Online
 一般情況下，Visual Studio Online 包含裝載在瀏覽器的功能。 在不同的環境中的色彩而有所不同，但樣式會保持相同。

|群組|使用量|名稱|值 （所有佈景主題）|樣本|
|-----------|-----------|----------|--------------------------|------------|
|TFS|背景|TFSO BG|656565/ 101, 101, 101|![樣本 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|外框|OUT TFSO|FFFFFF / 255，255，255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|背景|白皮書|FFFFFF / 255，255，255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|摩納哥|背景|白皮書|FFFFFF / 255，255，255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|背景|白皮書|FFFFFF / 255，255，255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|一般|F12 Grey_Primary|555555 / 85, 85, 85|![樣本 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|暫留|F12 Blue_Hover|2279BF / 34,121,191|![樣本 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|已停用|F12 LtGrey_Disabled|ABABAC / 171,171,172|![樣本 ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|暫留時背景|將滑鼠移至 bg|D9EBF7 / 217,235,247|![Swatch D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|已按下的背景|已按下的 bg|B2D7F0 / 178,215,240|![Swatch B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|外框|VS 出|F6F6F6 / 246,246,246|![樣本 F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|資訊|資訊|00BCF2 / 0,188,242|![樣本 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|警告|警告|F28300 / 242,131,0|![樣本 F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|錯誤 / 負數|Error_Negative|E81123 / 232,17,35|![樣本 E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|啟動 / 正數|Start_Positive|009E49 / 0,158,73|![樣本 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|符號類型|符號類型|9B4F96 / 155,79,150|![樣本 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|事件標記|事件標記|A51F00 / 165,31,0|![樣本 A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|使用者標記|使用者標記|F16220 / 241,98,32|![樣本 F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Visual Studio Online 圖示的範例

|TFS Online||||
|----------------|-|-|-|
|![TFS Online 小組圖示](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405年 49_TFSOnlineTeam")<br />Online 小組|![TFS 資訊圖示](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405年 50_TFSInformation")<br />資訊|![TFS 記錄圖示](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405年 51_TFSHistory")<br />歷程|![TFS 分支圖示](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405年 52_TFSBranch")<br />分支|

|Napa||||
|----------|-|-|-|
|![Napa 內容圖示](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405年 53_NapaContent")<br />內容|![Napa 辦公室郵件圖示](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405年 54_NapaOfficeMail")<br />Office 郵件|![Napa SharePoint 圖示](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405年 55_NapaSharePoint")<br />SharePoint|![Napa 工作窗格圖示](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405年 56_NapaTaskPane")<br />工作窗格|

|摩納哥||||
|------------|-|-|-|
|![Monaco 檔案圖示](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405年 57_MonacoFiles")<br />檔案|![Monaco Git 圖示](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405年 58_MonacoGit")<br />Git|![Monaco 搜尋圖示](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405年 59_MonacoSearch")<br />搜尋|![Monaco 文字圖示](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405年 60_MonacoText")<br />文字|

|F12|||
|---------|-|-|
|![F12 美化程式碼圖示](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405年 61_F12PrettyCode")<br />美化程式碼|![F12 警告圖示](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405年 62_F12Warning")<br />警告|![F12 模擬圖示](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405年 63_F12Emulate")<br />模擬|