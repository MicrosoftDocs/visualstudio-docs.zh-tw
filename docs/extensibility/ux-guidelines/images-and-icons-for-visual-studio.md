---
title: "影像和圖示的 Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 164a450ca346fe2bd7b267d951ce522d27f14160
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="images-and-icons-for-visual-studio"></a>影像和 Visual Studio 的圖示
##  <a name="BKMK_ImageUseInVisualStudio"></a>使用 Visual Studio 中的映像  
 在之前建立圖檔，請考慮進行 1000 + 中的映像使用[Visual Studio 影像庫](http://www.microsoft.com/en-my/download/details.aspx?id=35825)。  
  
### <a name="types-of-images"></a>類型的映像  
  
-   **圖示**。 會出現在命令、 階層、 範本和等等的小型影像。 使用 Visual Studio 中的預設圖示大小為 16 x 16 PNG。 圖示映像服務所產生的自動產生 HDPI 支援 XAML 的格式。  
  
     **注意：**功能表系統中使用映像，而您不應建立的每個命令的圖示。 請參閱[功能表和命令適用於 Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)以查看您的命令是否應該取得圖示。  
  
-   **縮圖。** 在對話方塊中，例如 [新增專案] 對話方塊的 [預覽] 區域中使用的影像。  
  
-   **對話方塊的影像。** 會出現在對話方塊或精靈，以描述性圖形或訊息指標的影像。 不常且困難的概念，或取得使用者注意 （警示，警告），必要時才使用。  
  
-   **動畫的影像。** 進度指標、 狀態列和對話方塊作業中使用。  
  
-   **資料指標。** 用來指出是否允許操作，使用的滑鼠，其中物件可能會中斷，依此類推。  
  
##  <a name="BKMK_IconDesign"></a>設計圖示  
  
### <a name="overview"></a>總覽  
 Visual Studio 會使用具有全新的幾何和正負數 （淡/濃） 50/50 平衡和使用直接、 容易了解象徵物的現代化樣式圖示。 重要圖示設計點清楚、 簡化主機，以及內容周圍的中心。  
  
-   **清晰度：**專注於核心比喻，其意義和責難提供圖示。  
  
-   **簡化：**減少其核心意義圖示-取得佈景主題，只需要的項目與任何 frills。  
  
-   **內容：**概念在開發期間，當您決定哪一個項目構成圖示的核心比喻時很重要，請考慮圖示角色的所有層面。  
  
 有圖示，有數個設計點，以避免：  
  
-   請勿使用代表 UI 項目，除了在適當時的圖示。 UI 項目是不常見，明顯，也不是唯一時，請選擇較抽象或符號的方法。  
  
-   不過度使用通用的項目，例如文件、 資料夾、 箭號和放大鏡。 這類項目圖示的意義必要時才使用。 例如，向右放大鏡應該指出只搜尋中，瀏覽和尋找。  
  
-   雖然某些傳統圖示項目會維持使用檢視方塊，請勿建立新圖示透視除非項目缺少沒有它的清晰度。  
  
-   不要 cram 太多資訊圖示。 簡單的映像可以輕鬆地辨識或做為可辨識符號學到更適合比過於複雜的映像。 圖示無法分辨整個本文。  
  
### <a name="icon-creation"></a>建立圖示  
  
#### <a name="concept-development"></a>概念開發  
 Visual Studio 在其 UI 中的各種不同的圖示類型。 在開發期間，請審慎考慮圖示類型。 請勿使用不明確或不常見的 UI 物件您圖示的項目。 選擇符號在這些情況下，例如使用智慧標籤圖示。 請注意，在左邊的抽象標記的意義更明顯比右邊微積分、 以 UI 為基礎的版本：  
  
|||  
|-|-|  
|**符號影像的正確用法**|**使用不正確的符號的影像**|  
|![正確的智慧標籤圖示](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404年 01_SmartTagCorrect")|![不正確的智慧標籤圖示](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404年 02_SmartTagIncorrect")|  
  
 有標準且易於識別 UI 項目適用於圖示所在的執行個體。 加入視窗是其中一個這類範例：  
  
|||  
|-|-|  
|**正確的圖示中的 UI 項目**|**不正確的圖示中的 UI 項目**|  
|![正確的加入視窗圖示](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404年 03_AddWindowCorrect")|![不正確的加入視窗圖示](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404年 04_AddWindowIncorrect")|  
  
 不使用文件做為基底的項目，除非務必要圖示的意義。 文件沒有意義 （如下） 加入文件上的項目會遺失，而重新整理文件項目並不需要傳達的意義。  
  
|||  
|-|-|  
|**正確使用文件圖示**|**使用不正確的文件圖示**|  
|![正確的文件圖示](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404年 05_DocumentIconCorrect")|![不正確的文件圖示](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404年 06_DocumentIconIncorrect")|  
  
 [顯示] 概念應該以最能說明所顯示的內容，例如與顯示所有檔案範例一樣的圖示。 功能濾鏡比喻可能用來指出如有必要的例如資源檢視的範例 「 檢視 」 的概念。  
  
|||  
|-|-|  
|**[顯示]**|**「 檢視 」**|  
|![顯示圖示](../../extensibility/ux-guidelines/media/0404-07_show.png "0404年 07_Show")|![檢視圖示](../../extensibility/ux-guidelines/media/0404-08_view.png "0404年 08_View")|  
  
 向右放大玻璃圖示應該代表只會搜尋、 尋找和瀏覽。 加號或減號向左 variant 應該代表只有放大/縮小。  
  
|||  
|-|-|  
|**「 搜尋 」**|**[縮放]**|  
|![搜尋圖示](../../extensibility/ux-guidelines/media/0404-09_search.png "0404年 09_Search")|![顯示比例 圖示](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404年 10_Zoom")|  
  
 在樹狀結構檢視中，請勿使用資料夾圖示和修飾詞。 可用時，使用的修飾詞。  
  
|||  
|-|-|  
|**正確的樹狀檢視圖示**|**不正確的樹狀檢視圖示**|  
|![正確的樹狀檢視圖示 &#40; 1 &#41;] (../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404年 11_TreeViewCorrect1") ![更正樹狀檢閱圖示 &#40; 2 &#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404年 12_TreeViewCorrect2")|![不正確的樹狀檢視圖示 &#40; 1 &#41;] (../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404年 13_TreeViewIncorrect1") ![不正確的樹狀檢視圖示 &#40; 2 &#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404年 14_TreeViewIncorrect2")|  
  
### <a name="style-details"></a>樣式詳細資料  
  
#### <a name="layout"></a>配置  
 堆疊項目為 16 x 16 的標準圖示所示：  
  
 ![16x16 圖示的版面配置堆疊](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404年 15_LayoutStack")<br />16x16 圖示的版面配置堆疊
  
 狀態通知元素是比較用做獨立圖示。 有的內容，不過，在其中通知應該在堆疊基底的項目，例如工作完成圖示：  
  
 ![Visual Studio 中的獨立通知](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404年 16_StandaloneNotificationIcons")<br />獨立通知圖示
  
 ![工作完成圖示](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404年 17_TaskComplete")<br />工作完成圖示
  
 專案圖示通常會包含多個大小的.ico 檔案。 大部分的 16x16 圖示會包含相同項目。 32 x 32 版本有更多詳細資料，包括專案類型時適用。  
  
 ![專案 Visual Studio 中的圖示](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404年 18_IconProjectThreeSizes")<br />VB Windows 控制項程式庫專案圖示，16 x 16 及 32 x 32 
  
 置中於像素框架內的圖示。 如果不可行，對齊圖示上方，及/或框架的權限。  
  
 ![圖示位於像素框架的中央](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404年 19_IconCentered")<br />圖示位於像素框架的中央
  
 ![圖示對齊像素框架的右上方](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404年 20_IconTopRight")<br />圖示靠上對齊框架的權限
  
 ![圖示位於中央且對齊，以像素框架的頂端](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404年 21_IconTopAlign")<br />圖示位於中央且對齊框架頂端
  
 若要達到最理想的對齊方式和平衡，避免阻礙的圖示與動作圖像的基底項目。 將放在最上方的圖像方基底的項目。 當加入其他項目，請考慮對齊和圖示的平衡。  
  
|||  
|-|-|  
|**正確對齊並平衡**|**不正確對齊和平衡**|  
|![更正的圖示平衡和對齊](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404年 22_AlignBalanceCorrect")|![不正確的圖示平衡和對齊方式](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404年 23_AlignBalanceIncorrect")|  
  
 請確定共用項目，以及用於在集合中的圖示大小同位檢查。 請注意，在不正確的配對，circle 和箭號會過大，而且不相符。  
  
|||  
|-|-|  
|**正確的大小同位檢查**|**大小不正確的同位檢查**|  
|![更正的圖示大小和同位檢查](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404年 24_SizeParityCorrect")|![不正確的圖示大小和同位](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404年 25_SizeParityIncorrect")|  
  
 使用一致的行和視覺加權。 評估如何您要建置的圖示與比較其他圖示使用並行的比較。 永遠不會使用整個 16 x 16 框架，請使用 15 x 15 或較小。 應該 50/50 負的正數 （暗色調-亮） 比例。  
  
|||  
|-|-|  
|**正確的負-正比例**|**不正確的負-正比率**|  
|![正確視覺比例的圖示 &#40; 1 &#41;] (../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404年 26_VisualWeightCorrect1")<br /><br /> ![正確視覺比例的圖示 &#40; 2 &#41;] (../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404年 27_VisualWeightCorrect2")<br /><br /> ![正確視覺比例的圖示 &#40; 3 &#41;] (../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404年 28_VisualWeightCorrect3")|![不正確的圖示視覺加權](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404年 29_VisualWeightIncorrect")|  
  
 使用簡單、 比較圖形和互補角度而不必犧牲項目整合建置您的項目。 請盡可能使用 45 度或 90 度的角度。  
  
 ![更正的圖示角度](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404年 30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>透視圖  
 請清除及可了解的圖示。 使用檢視方塊和光源只在必要時。 雖然應該避免使用檢視方塊圖示的項目上，但是某些項目都沒有它無法辨識。 在這種情況下，樣式化的檢視方塊進行通訊的項目清晰度。  
  
 ![3 點透視](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404年 31_3PointPerspective")<br />3 點透視圖
  
 ![1 點透視](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404年 32_1PointPerspective")<br />1 點透視圖
  
 大部分的項目應該面對或角度右邊：  
  
 ![圖示靠右對齊](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404年 33_AngledRight")  
  
 只需要明確加入物件中時，請使用光線的來源。  
  
|||  
|-|-|  
|**正確光線的來源**|**不正確光線的來源**|  
|![更正的圖示光源](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404年 34_LightSourcesCorrect")|![不正確的圖示光源](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404年 35_LightSourcesIncorrect")|  
  
 使用大綱，來提升可讀性，或進一步進行通訊的字眼。 負正 （暗色調亮） 平衡應該 50/50。  
  
|||  
|-|-|  
|**外框的正確用法**|**使用不正確的外框**|  
|![更正外框](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404年 36_OutlinesCorrect")|![不正確的外框](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404年 37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>圖示類型  
 **殼層和命令列**圖示包含超過三個下列項目： 一個基底、 一個修飾詞、 一個動作或一種狀態。  
  
 ![殼層和命令列圖示的範例](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404年 38_ShellIcons")<br />殼層和命令列圖示的範例
  
 **工具視窗命令列**圖示包含超過三個下列項目： 一個基底、 一個修飾詞、 一個動作或一種狀態。  
  
 ![工具視窗的範例命令列圖示](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404年 39_ToolWindowCommandBarIcons")<br />工具視窗命令列圖示的範例
  
 **樹狀檢視消歧義器**圖示包含超過三個下列項目： 一個基底、 一個修飾詞、 一個動作或一種狀態。  
  
 ![範例的樹狀檢視消歧義器圖示](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404年 40_TreeViewIcons")<br />範例的樹狀檢視消歧義器圖示
  
 **狀態為基礎的值分類**圖示存在處於下列狀態： 作用中、 已停用，作用中和非使用中已停用。  
  
 ![狀態為基礎的值分類圖示的範例](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404年 41_StateBasedTaxonomy")<br />狀態為基礎的值分類圖示的範例
  
 **IntelliSense**圖示包含超過三個下列項目： 一個基底、 一個修飾詞和一個狀態。  
  
 ![IntelliSense 圖示的範例](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404年 42_IntelliSenseIcons")<br />IntelliSense 圖示的範例
  
 **小型 (16 x 16) 專案**圖示應該有兩個以上的項目： 一個基底和一個修飾詞。  
  
 ![小型 (16 x 16) 的範例專案圖示](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404年 43_16x16Project1") ![16x16 專案圖示 &#40; 2 &#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404年 44_16x16Project2") ![16x16 專案圖示 &#40; 3 &#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404年 45_16x16Project3")<br />小型 (16 x 16) 的範例專案圖示
  
 **大型 (32x32) 專案**圖示包含不超過四個下列項目： 一個基底、 一到兩個修飾詞和重疊的一種語言。  
  
 ![大型 (32x32) 的範例專案圖示](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404年 46_32x32Project")<br />大型 (32x32) 的範例專案圖示
  
### <a name="production-details"></a>實際詳細資料  
 所有新的 UI 項目應該使用 Windows Presentation Foundation (WPF) 建立與 wpf 的所有新圖示應該是 32 位元 PNG 格式。 24 位元 PNG 是舊版的格式，不支援透明，因此不建議的圖示。  
  
 將儲存的解析度 96 dpi。  
  
#### <a name="file-types"></a>檔案類型  
  
-   **32 位元 PNG:**圖示的慣用的格式。 可以儲存 （像素） 的單一點陣影像不失真的資料壓縮檔案格式。 32 位元 PNG 檔案支援 alpha 色板透明度、 gamma 修正和交錯式。  
  
-   **32 位元 BMP:**非 WPF 控制項。 也稱為 XP 或高彩，32 位元 BMP 是 RGB/A 映像格式，具有 alpha 色板透明度 true 彩色影像。 Alpha 色板是圖層透明度，然後會儲存在其他 （第四個） 為點陣圖的 Adobe Photoshop 中指定的色彩頻道。 所有 32 位元 BMP 檔案，以提供有關色彩深度的快速視覺提示的作品實際執行期間，會加入在黑色背景。 這個黑色背景代表要在 UI 中的遮罩的區域。  
  
-   **32 位元 ICO:**專案圖示和加入項目。 所有的 ICO 檔案都是 32 位元，則為 true 色彩的 alpha 色板透明度 (RGB/A)。 因為 ICO 檔案可以儲存多個的大小和色彩深度，Vista 圖示通常是 ICO 格式包含 16 x 16、 32 x 32、 48 x 48 和 256 x 256 映像大小。 為了正確顯示在 Windows 檔案總管，ICO 檔案必須是儲存向每個映像大小的 24 位元和 8 位元色彩深度。  
  
-   **XAML:**設計介面和 Windows 裝飾項。 XAML 圖示是支援縮放、 旋轉、 歸檔和透明度向量為基礎的影像檔。 這些不常見 Visual Studio 中今天但因為其彈性越來越普遍。  
  
-   **SVG**  
  
-   **24 位元 BMP:** Visual Studio 命令列。 True 色彩 RGB 映像格式，24 位元 BMP。 使用洋紅色 （R = 255、 G = 0，B = 255） 建立圖層的透明度，破壞外透明度圖層的色彩索引鍵圖示慣例 在 24 位元 BMP、 所有洋紅色介面使用的背景色彩顯示。  
  
-   **24 位元 GIF:** Visual Studio 命令列。 True 色彩 RGB 映像格式，可支援透明度。 GIF 檔通常用於精靈作品和 GIF 動畫。  
  
### <a name="icon-construction"></a>圖示建構  
 Visual Studio 中的最小圖示大小為 16 x 16。 最大在一般用途是 32 x 32。 請注意，不是用來填滿整個 16x16、 24x24 或 32 x 32 框架，在設計圖示。 易於閱讀、 統一的圖示建構是重要的使用者辨識。 建置圖示時，請遵守下列各點。  
  
-   圖示應該是清楚、 容易了解，且一致。  
  
-   最好的狀態通知項目做為單一的圖示，而非堆疊頂端的圖示的基底項目。 在某些內容中，UI 可能需要與基底的項目配對的狀態項目。  
  
-   專案圖示通常包含數個大小的.ico 檔案。 正在更新只 16x16、 24x24 和 32x32 圖示。 大部分 16 x 16 到 24 x 24 圖示會包含相同項目。 32x32 圖示會包含更多詳細資料，包括專案語言類型時適用。  
  
-   32x32 圖示的基底的項目通常會有 2 像素線條寬度。 1 或 2 像素線條寬度可以用於詳細資料元素。 使用您最佳的判斷，來決定哪一個更適合。  
  
-   必須至少有 1 像素之間間距 16 x 16 個項目和 24x24 圖示。 32x32 圖示，使用 2 像素項目以及修飾詞與基底項目之間的間距。  
  
 ![項目間距的 16x16、 24x24 和 32x32 圖示的大小調整](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404年 47_ElementSpacing")<br />16x16、 24x24 和 32x32 圖示的項目間距的大小調整
  
#### <a name="color-and-accessibility"></a>色彩和協助工具  
 Visual Studio 相容性的指導方針會需要產品中的所有圖示都傳遞色彩和對比的協助工具需求。 這透過圖示逆轉達成，並在設計時應該注意它們將會反轉以程式設計方式在產品中。  
  
 如需有關使用 Visual Studio 圖示色彩的詳細資訊，請參閱[映像中使用色彩](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)。  
  
##  <a name="BKMK_UsingColorInImages"></a>使用映像中的色彩  
  
### <a name="overview"></a>總覽  
 在 Visual Studio 中的圖示是主要是單色。 保留色彩傳達的特定資訊並永遠不會為裝飾。 使用色彩：  
  
-   表示動作  
  
-   警示的狀態通知使用者  
  
-   若要指定語言的關係  
  
-   在 IntelliSense 中的項目  
  
### <a name="accessibility"></a>協助工具選項  
 Visual Studio 相容性的指導方針需要的所有圖示都簽入產品傳遞色彩和對比的協助工具需求。 視覺化語言調色盤中的色彩都已測試過，而且符合這些需求。  
  
#### <a name="color-inversion-for-dark-themes"></a>暗色調佈景主題的色彩反轉  
 為了讓具有正確的對比比例在 Visual Studio 暗色調佈景主題出現圖示，反轉會以程式設計的方式套用。 本指南中的色彩已選擇部分，讓它們正確地反轉。 這個調色盤，會限制您使用的色彩，或反轉套用時，您就會發生無法預期的結果。  
  
 ![已經反轉其色彩圖示的範例](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405年 01_DarkThemeInversion")<br />已經反轉其色彩圖示的範例
  
### <a name="base-palette"></a>基礎調色盤  
 所有標準的圖示會包含三種基底的色彩。 圖示會包含任何漸層或延伸陰影，以 3D 工具圖示的一個或兩個例外狀況。  
  
|使用量|名稱|值 （淺色佈景主題）|樣本|範例|  
|-----------|----------|---------------------------|------------|-------------|  
|暗色調背景 /|VS BG|424242 / 66,66,66|![樣本 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![基礎調色盤範例](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405年 02_BasePaletteExample")|  
|前景/輕|VS FG|F0EFF1 / 240,239,241|![樣本 F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|外框|VS 出|F6F6F6 / 246,246,246|![樣本 F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 除了基底的色彩，每個圖示可包含一種擴充調色盤中的其他色彩。  
  
### <a name="extended-palette"></a>擴充的調色盤  
  
#### <a name="action-modifiers"></a>動作修飾詞  
 下列四種色彩表示動作修飾詞所需的動作類型：  
  
|使用量|名稱|值 （所有主題）|樣本|  
|-----------|----------|--------------------------|------------|  
|正|VS 動作綠色|388A34 / 56,138,52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|負|VS 動作紅色|A1260D / 161,38,13|![樣本 A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|中性|VS 動作藍色|00539 C / 0,83,156|![樣本 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|建立/新增|VS 動作橙色|C27D1A / 194,156,26|![樣本 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>範例  
 綠色用於正向動作修飾詞，例如 「 新增 」，「 執行，"播放、 」 和 「 驗證 」。  
  
|||||  
|-|-|-|-|  
|![執行圖示](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405年 03_ActionModifierRun")<br />執行|![執行查詢圖示](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405年 04_ExecuteQuery")<br />執行查詢|![播放所有步驟圖示](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405年 05_PlayAllSteps")<br />播放所有步驟|![加入控制項圖示](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405年 06_AddControl")<br />加入控制項|  
  
 紅色用於負動作修改像是"Delete"的 [停止]，[取消] 和 [關閉]。  
  
|||||  
|-|-|-|-|  
|![刪除關聯性圖示](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405年 07_DeleteRelationship")<br />刪除關聯性|![刪除資料行圖示](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405年 08_DeleteColumn")<br />刪除欄|![停止查詢圖示](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405年 09_StopQuery")<br />停止查詢|![連接離線圖示](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405年 10_ConnectionOffline")<br />連接離線|  
  
 藍色適用於中性的動作，最常使用修飾詞表示為箭號，像是 「 開啟，"下一步，「 「 上一步 」，「 匯入 」 和 「 匯出 」。  
  
|||||  
|-|-|-|-|  
|![移至欄位圖示](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405年 11_GoToField")<br />請移至欄位|![批次檢查 &#45; 在圖示](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405年 12_BatchedCheckIn")<br />批次簽入|![地址編輯器圖示](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405年 13_AddressEditor")<br />地址編輯器|![關聯編輯器圖示](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405年 14_AssociationEditor")<br />關聯編輯器|  
  
 深色金級主要用於 「 新增 」 修飾詞。  
  
|||||  
|-|-|-|-|  
|![新的專案圖示](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405年 15_NewProject")<br />新增專案|![建立新的圖形圖示](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405年 16_CreateNewGraph")<br />建立新的圖表|![新的單元測試圖示](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405年 17_NewUnitTest")<br />新的單元測試|![新清單項目圖示](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405年 18_NewListItem")<br />新清單項目|  
  
#### <a name="special-cases"></a>特殊案例  
 在特殊情況下，彩色的動作修飾詞可能會單獨用為獨立的圖示。 用圖示的色彩會反映圖示相關聯的動作。 此使用方式會限制為一小部分的圖示，包括：  
  
||||||  
|-|-|-|-|-|  
|![執行圖示](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405年 03_ActionModifierRun")<br />執行|![停止圖示](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405年 19_Stop")<br />停止|![刪除圖示](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405年 20_Delete")<br />刪除|![儲存圖示](../../extensibility/ux-guidelines/media/0405-21_save.png "0405年 21_Save")<br />儲存|![向後巡覽圖示](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405年 22_NavigateBack")<br />往回導覽|  
  
### <a name="code-hierarchy-palette"></a>程式碼階層架構調色盤  
  
#### <a name="folder"></a>資料夾  
  
|使用量|名稱|值 （所有主題）|樣本|範例|  
|-----------|----------|--------------------------|------------|-------------|  
|資料夾|資料夾|DCB67A / 220,182,122|![樣本 DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![資料夾色彩圖示](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405年 23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Visual Studio 語言  
 每個一般的 語言 或 Visual Studio 中提供的平台有相關聯的色彩。 這些色彩使用基底的圖示，或出現在複合圖示右上角的語言修飾詞。  
  
|使用量|名稱|值 （所有主題）|樣本|  
|-----------|----------|--------------------------|------------|  
|ASP，HTML，WPF|ASP HTML WPF 藍色|0095D 7 / 0,149,215|![樣本 0095d7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|CPP 紫色|9B4F96 / 155,79,150|![樣本 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|CS 綠色 （VS 動作綠色）|388A34 / 56,138,52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|CSS 紅色|BD1E2D / 189,30,45|![樣本 BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|FS 紫色|672878 / 103,40,120|![樣本 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|JS 橙色|F16421 / 241,100,33|![樣本 F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|VB 藍色 （VS 動作藍色）|00539 C / 0,83,156|![樣本 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|TS 橙色|E04C06 / 224,76,6|![樣本 E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|PY 綠色|879636 / 135,150,54|![樣本 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>圖示與語言修飾詞的範例  
  
|||||||  
|-|-|-|-|-|-|  
|![Visual Basic 圖示](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405年 25_VB")<br />VB|![& #35。圖示](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405年 26_CSharp")<br />C#|![C# 43; &#43;圖示](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405年 27_CPlusPlus")<br />C++|![& #35。圖示](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405年 28_FSharp")<br />F#|![JavaScript 圖示](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405年 29_JavaScript")<br />JavaScript|![Python 圖示](../../extensibility/ux-guidelines/media/0405-30_python.png "0405年 30_Python")<br />Python|  
|![HTML 圖示](../../extensibility/ux-guidelines/media/0405-31_html.png "0405年 31_HTML")<br />HTML|![WPF 圖示](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405年 32_WPF")<br />WPF|![ASP 圖示](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405年 33_ASP")<br />ASP|![CSS 圖示](../../extensibility/ux-guidelines/media/0405-34_css.png "0405年 34_CSS")<br />CSS|![TypeScript 圖示](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405年 35_TypeScript")<br />TypeScript||  
  
#### <a name="intellisense"></a>IntelliSense  
 IntelliSense 圖示使用獨佔的調色盤。 這些色彩可協助使用者快速區分 IntelliSense 快顯清單中的不同項目。  
  
|使用量|名稱|值 （所有主題）|樣本|  
|-----------|----------|--------------------------|------------|  
|事件類別|VS 動作橙色|C27D1A / 194,125,26|![樣本 C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|擴充方法，方法中，模組中委派|VS 動作紫色|652 D 90 / 101,45,144|![樣本 652d90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|欄位、 列舉項目、 巨集、 結構、 等位的實值型別，運算子，介面|VS 動作藍色|00539 C / 0,83,156|![樣本 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Object|VS 動作綠色|388A34 / 56,138,52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|常數，例外狀況、 列舉項目、 地圖、 地圖項目、 命名空間中，範本中，類型定義|背景 (VS BG)|424242 / 66,66,66|![樣本 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>IntelliSense 圖示的範例  
  
||||||  
|-|-|-|-|-|  
|![IntelliSense 類別圖示](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405年 36_IntelliSenseClass")<br />類別|![IntelliSense 私用事件圖示](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405年 37_IntelliSensePrivateEvent")<br />私用事件|![IntelliSense 委派圖示](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405年 38_IntelliSenseDelegate")<br />Delegate - 委派|![IntelliSense 方法 friend 圖示](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405年 39_IntelliSenseMethodFriend")<br />方法 Friend|![欄位圖示](../../extensibility/ux-guidelines/media/0405-40_field.png "0405年 40_Field")<br />欄位|  
|![IntelliSense 受保護的列舉項目圖示](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405年 41_IntelliSenseProtectedEnumItem")<br />受保護的列舉項目|![IntelliSense 物件圖示](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405年 42_IntelliSenseObject")<br />Object|![IntelliSense 範本圖示](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405年 43_IntelliSenseTemplate")<br />範本|![IntelliSense 例外狀況捷徑圖示](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405年 44_IntelliSenseExceptionShortcut")<br />例外狀況捷徑||  
  
### <a name="notifications"></a>通知  
 在 Visual Studio 中的通知可用來表示狀態。 通知調色盤會使用下列四種色彩，以及黑色或白色前景填滿選項，定義下列狀態層級的通知。  
  
|使用量|名稱|值 （所有主題）|樣本|  
|-----------|----------|--------------------------|------------|  
|狀態： 中性|通知藍色 （與藍色）|1BA1E2 / 27,161,226|![樣本 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|狀態： 正數|通知綠色 （VS 綠色）|339933 / 51,153,51|![樣本 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|狀態： 負數|通知紅色 （VS 紅色）|E51400 / 229,20,0|![樣本 E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|狀態： 警告|通知黃色 （VS 橘色）|FFCC00 / 255,204,0|![樣本 FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|前景填滿|通知黑色 （黑色）|000000 / 0,0,0|![樣本 &#35; 000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|前景填滿|通知白色 （白色）|FFFFFF / 255,255,255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>通知圖示的範例  
  
|||||  
|-|-|-|-|  
|![警示圖示](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405年 45_Alert")<br />警示|![警告圖示](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405年 48_Warning")<br />警告|![完成圖示](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405年 46_Complete")<br />完成|![停止圖示](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405年 47_Stop")<br />停止|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 一般情況下，Visual Studio Online 包含裝載在瀏覽器的功能。 在不同的環境中的色彩而有所不同，但樣式會保持相同。  
  
|群組|使用量|名稱|值 （所有主題）|樣本|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|背景|TFSO BG|656565/ 101, 101, 101|![樣本 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|外框|TFSO 出|FFFFFF / 255，255，255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|背景|白色|FFFFFF / 255，255，255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Monaco|背景|白色|FFFFFF / 255，255，255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|背景|白色|FFFFFF / 255，255，255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|一般|F12 Grey_Primary|555555 / 85, 85, 85|![樣本 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|暫留|F12 Blue_Hover|2279BF / 34,121,191|![樣本 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|已停用|F12 LtGrey_Disabled|ABABAC / 171,171,172|![樣本 ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|將滑鼠停留背景|將滑鼠停留 bg|D9EBF7 / 217,235,247|![樣本 D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|已按下的背景|已按下的 bg|B2D7F0 / 178,215,240|![樣本 B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|外框|VS 出|F6F6F6 / 246,246,246|![樣本 F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|資訊|資訊|00BCF2 / 0,188,242|![樣本 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|警告|警告|F28300 / 242,131,0|![樣本 F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|錯誤 / 負數|Error_Negative|E81123 / 232,17,35|![樣本 E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|啟動 / 正數|Start_Positive|009E49 / 0,158,73|![樣本 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|中斷類型|中斷類型|9B4F96 / 155,79,150|![樣本 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|事件標記|事件標記|A51F00 / 165,31,0|![樣本 A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|使用者標記|使用者標記|F16220 / 241,98,32|![樣本 F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Visual Studio Online 圖示的範例  
  
|TFS Online||||  
|----------------|-|-|-|  
|![TFS Online 小組圖示](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405年 49_TFSOnlineTeam")<br />Online 團隊|![TFS 資訊圖示](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405年 50_TFSInformation")<br />資訊|![TFS 記錄圖示](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405年 51_TFSHistory")<br />歷程|![TFS 分支圖示](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405年 52_TFSBranch")<br />分支|  
  
|Napa||||  
|----------|-|-|-|  
|![Napa 內容圖示](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405年 53_NapaContent")<br />內容|![Napa 辦公室郵件圖示](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405年 54_NapaOfficeMail")<br />Office 郵件|![Napa SharePoint 圖示](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405年 55_NapaSharePoint")<br />SharePoint|![Napa 工作窗格圖示](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405年 56_NapaTaskPane")<br />工作窗格|  
  
|Monaco||||  
|------------|-|-|-|  
|![Monaco 檔案圖示](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405年 57_MonacoFiles")<br />檔案|![Monaco Git 圖示](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405年 58_MonacoGit")<br />Git|![Monaco 搜尋圖示](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405年 59_MonacoSearch")<br />搜尋|![Monaco 文字圖示](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405年 60_MonacoText")<br />Text|  
  
|F12|||  
|---------|-|-|  
|![F12 美化程式碼圖示](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405年 61_F12PrettyCode")<br />美化程式碼|![F12 警告圖示](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405年 62_F12Warning")<br />警告|![F12 模擬圖示](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405年 63_F12Emulate")<br />模擬|