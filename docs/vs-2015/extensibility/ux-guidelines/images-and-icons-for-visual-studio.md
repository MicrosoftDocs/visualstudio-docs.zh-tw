---
title: 影像與圖示
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 843829c56fcbd2f5c558d7c4a8b14a660a431eac
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302417"
---
# <a name="images-and-icons-for-visual-studio"></a>適用於 Visual Studio 的影像和圖示
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>視覺工作室中的圖像使用
 在創建圖稿之前，請考慮使用[Visual Studio 圖像庫中](https://www.microsoft.com/download/details.aspx?id=35825)的 1，000 多張圖片。

### <a name="types-of-images"></a>圖像類型

- **圖示**. 出現在命令、層次結構、範本等中的小圖像。 Visual Studio 中使用的預設圖示大小為 16x16 PNG。 影像服務生成的圖示會自動生成 XAML 格式，用於 HDPI 支援。

     **注：** 當圖像在功能表系統中使用時，不應為每個命令創建圖示。 請參閱[Visual Studio 的功能表和命令](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)，查看命令是否應獲得圖示。

- **縮略 圖。** 對話方塊的預覽區域（如"新專案"對話方塊）中使用的圖像。

- **對話方塊圖像。** 以描述性圖形或消息指示器顯示在對話方塊或嚮導中的圖像。 很少使用，且僅在必要時才用於說明一個困難的概念或引起使用者的注意（警報、警告）。

- **動畫圖像。** 用於進度指示器、狀態列和操作對話方塊。

- **游標。** 用於指示是否允許使用滑鼠操作、可能丟棄物件的位置等。

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>圖示設計

### <a name="overview"></a>概觀
 Visual Studio 使用現代風格的圖示，這些圖示具有乾淨的幾何形狀和 50/50 的正/負（淺色/暗數）平衡，並使用直接、可理解的隱喻。 關鍵圖示設計點圍繞清晰度、簡化和上下文。

- **清晰度：** 關注核心隱喻，賦予圖示其意義和個性。

- **簡化：** 將圖示減小到其核心含義 - 只需必要的元素即可將主題與無褶皺。

- **上下文：** 在概念開發過程中考慮圖示符號的所有方面，這在決定哪些元素構成圖示的核心隱喻時至關重要。

  使用圖示，有許多設計點需要避免：

- 除非適用，否則不要使用表示 UI 元素的圖示。 當 UI 元素既不常見、明顯也不唯一時，請選擇更抽象或符號化的方法。

- 不要過度使用文檔、資料夾、箭頭和放大鏡等常見元素。 僅當圖示的含義至關重要時，才使用這些元素。 例如，右側的放大鏡應僅指示搜索、流覽和查找。

- 儘管某些舊圖示元素保持透視的使用，但除非沒有透視，則不要創建具有透視的新圖示，除非該元素缺乏清晰度。

- 不要將太多資訊塞進圖示中。 一個簡單的圖像，可以很容易地識別或學習為可識別的符號比過於複雜的圖像更有用。 圖示無法講述整個故事。

### <a name="icon-creation"></a>圖示創建

#### <a name="concept-development"></a>概念開發
 Visual Studio 在其 UI 中具有多種圖示類型。 在開發過程中仔細考慮圖示類型。 不要對圖示元素使用不明確或不常見的 UI 物件。 在這些情況下，例如使用智慧標籤圖示，請選擇符號。 請注意，左側抽象標記的含義比右側模糊的基於 UI 的版本更明顯：

|||
|-|-|
|**正確使用符號圖像**|**符號圖像使用不正確**|
|![正確的智慧標籤圖示](../../extensibility/ux-guidelines/media/0404-01-smarttagcorrect.png "0404-01_SmartTagCorrect")|![不正確的智慧標籤圖示](../../extensibility/ux-guidelines/media/0404-02-smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 在某些情況下，標準、易於識別的 UI 元素對圖示工作良好。 添加視窗就是一個示例：

|||
|-|-|
|**圖示中更正 UI 元素**|**圖示中的 UI 元素不正確**|
|![正確的加入視窗圖示](../../extensibility/ux-guidelines/media/0404-03-addwindowcorrect.png "0404-03_AddWindowCorrect")|![不正確的加入視窗圖示](../../extensibility/ux-guidelines/media/0404-04-addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 不要將文檔用作基本元素，除非文檔對圖示的含義至關重要。 如果沒有 Add Document 上的文件項目（下圖），含義將丟失，而使用"刷新"時，文件項目就不必傳達含義。

|||
|-|-|
|**正確使用文檔圖示**|**文檔圖示使用不正確**|
|![正確的文件圖示](../../extensibility/ux-guidelines/media/0404-05-documenticoncorrect.png "0404-05_DocumentIconCorrect")|![不正確的文件圖示](../../extensibility/ux-guidelines/media/0404-06-documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 "show"的概念應該由最能說明顯示內容的圖示表示，例如使用"顯示所有檔"示例。 如有必要，可以使用鏡頭隱喻來指示"視圖"的概念，例如使用資源檢視示例。

|||
|-|-|
|**"顯示"**|**"查看"**|
|![顯示圖示](../../extensibility/ux-guidelines/media/0404-07-show.png "0404-07_Show")|![檢視圖示](../../extensibility/ux-guidelines/media/0404-08-view.png "0404-08_View")|

 右側的放大鏡圖示應僅表示搜索、查找和流覽。 帶有加號或減號的左側變體應僅表示放大/縮小。

|||
|-|-|
|**"搜索"**|**"縮放"**|
|![搜尋圖示](../../extensibility/ux-guidelines/media/0404-09-search.png "0404-09_Search")|![[縮放] 圖示](../../extensibility/ux-guidelines/media/0404-10-zoom.png "0404-10_Zoom")|

 在樹狀檢視中，不要同時使用資料夾圖示和修改器。 如果可用，則僅使用修改器。

|||
|-|-|
|**正確的樹狀檢視圖示**|**樹狀檢視圖示不正確**|
|![正確樹狀檢視圖示&#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11-treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![正確樹狀檢視圖示&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12-treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![樹狀檢視圖示&#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13-treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![不正確的樹狀檢視圖示&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14-treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>樣式詳細資訊

#### <a name="layout"></a>版面配置
 堆疊元素，如標準 16x16 圖示所示：

 ![16x16 圖示的版面配置堆疊](../../extensibility/ux-guidelines/media/0404-15-layoutstack.png "0404-15_LayoutStack")

 **16x16 圖示的版面配置堆疊**

 狀態通知元素更好地用作獨立圖示。 但是，在某些情況下，通知應堆疊在基本元素上，例如使用"任務完成"圖示：

 ![Visual Studio 中的獨立通知](../../extensibility/ux-guidelines/media/0404-16-standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")

 **獨立通知圖示**

 ![工作完成圖示](../../extensibility/ux-guidelines/media/0404-17-taskcomplete.png "0404-17_TaskComplete")

 **任務完成圖示**

 專案圖示通常是包含多個大小的 .ico 檔。 大多數 16x16 圖示包含相同的元素。 32x32 版本具有更多詳細資訊，包括專案類型（如果適用）。

 ![Visual Studio 中的專案圖示](../../extensibility/ux-guidelines/media/0404-18-iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")

 **VB Windows 控制庫專案圖示，16x16 和 32x32**

 將圖示居其圖元幀中居中。 如果無法這樣做，則將圖示對齊到框架的頂部和/或右側。

 ![圖示位於像素框架的中央](../../extensibility/ux-guidelines/media/0404-19-iconcentered.png "0404-19_IconCentered")

 **圖示位於像素框架的中央**

 ![圖示對齊像素框架的右上方](../../extensibility/ux-guidelines/media/0404-20-icontopright.png "0404-20_IconTopRight")

 **與框架右上角對齊的圖示**

 ![圖示位於像素框架的中央並靠上對齊](../../extensibility/ux-guidelines/media/0404-21-icontopalign.png "0404-21_IconTopAlign")

 **圖示居中並對齊到框架頂部**

 要實現理想的對齊和平衡，請避免用動作字形阻擋圖示的基本元素。 將字形放在基元素左上角附近。 添加附加元素時，請考慮圖示的對齊和平衡。

|||
|-|-|
|**正確的對齊和平衡**|**對齊和平衡不正確**|
|![正確的圖示平衡和對齊方式](../../extensibility/ux-guidelines/media/0404-22-alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![不正確的圖示平衡和對齊方式](../../extensibility/ux-guidelines/media/0404-23-alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 確保共用元素並在集中使用的圖示的大小同位。 請注意，在不正確的配對中，圓圈和箭頭大小過大且不匹配。

|||
|-|-|
|**正確的大小同位**|**大小同位不正確**|
|![正確的圖示大小和同位](../../extensibility/ux-guidelines/media/0404-24-sizeparitycorrect.png "0404-24_SizeParityCorrect")|![不正確的圖示大小和同位](../../extensibility/ux-guidelines/media/0404-25-sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 使用一致的線條和視覺權重。 使用並排比較評估要構建的圖示與其他圖示的比較情況。 切勿使用整個 16x16 幀，使用 15x15 或更小。 負對正（暗對光）比應為50/50。

|||
|-|-|
|**正確的負正比率**|**不正確的負正比率**|
|![&#40;1&#41;圖示的正確視覺權重](../../extensibility/ux-guidelines/media/0404-26-visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![圖示&#40;2&#41;的正確視覺權重](../../extensibility/ux-guidelines/media/0404-27-visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![&#40;3&#41;圖示的正確視覺權重](../../extensibility/ux-guidelines/media/0404-28-visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![不正確的圖示視覺加權](../../extensibility/ux-guidelines/media/0404-29-visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 使用簡單、可比較的形狀和互補的角度構建元素，而不會犧牲元素的完整性。 盡可能使用 45° 或 90° 角度。

 ![正確的圖示角度](../../extensibility/ux-guidelines/media/0404-30-iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>檢視方塊
 保持圖示清晰且易於理解。 僅在必要時使用透視和光源。 儘管應避免對圖示元素使用透視，但某些元素在沒有它的情況下是無法識別的。 在這種情況下，樣式化的透視圖傳達元素的清晰度。

 ![3&#45;點透視](../../extensibility/ux-guidelines/media/0404-31-3pointperspective.png "0404-31_3PointPerspective")

 **3 點透視圖**

 ![1&#45;點透視](../../extensibility/ux-guidelines/media/0404-32-1pointperspective.png "0404-32_1PointPerspective")

 **1 點透視圖**

 大多數元素應朝向或向右傾斜。

 ![圖示靠右對齊](../../extensibility/ux-guidelines/media/0404-33-angledright.png "0404-33_AngledRight")

 僅當向物件添加必要的清晰度時，才使用光源。

|||
|-|-|
|**正確的光源**|**光源不正確**|
|![正確的圖示光源](../../extensibility/ux-guidelines/media/0404-34-lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![不正確的圖示光源](../../extensibility/ux-guidelines/media/0404-35-lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 使用輪廓只是為了增強可讀性或更好地傳達隱喻。 負正（暗光）餘額應為 50/50。

|||
|-|-|
|**正確使用輪廓**|**不正確使用輪廓**|
|![正確的外框](../../extensibility/ux-guidelines/media/0404-36-outlinescorrect.png "0404-36_OutlinesCorrect")|![不正確的外框](../../extensibility/ux-guidelines/media/0404-37-outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>圖示類型
 **命令程式單圖示**由以下三個元素組成：一個基、一個修改器、一個操作或一個狀態。

 ![殼層和命令列圖示](../../extensibility/ux-guidelines/media/0404-38-shellicons.png "0404-38_ShellIcons")

 **外殼和命令列圖示的示例**

 **工具視窗命令列**圖示由以下元素中的三個組成：一個基、一個修改器、一個操作或一個狀態。

 ![工具視窗命令列圖示](../../extensibility/ux-guidelines/media/0404-39-toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")

 **工具視窗命令列圖示的示例**

 **樹狀檢視消除歧義圖示**由以下元素中的三個組成：一個基、一個修改器、一個操作或一個狀態。

 ![樹狀檢視消歧義器圖示](../../extensibility/ux-guidelines/media/0404-40-treeviewicons.png "0404-40_TreeViewIcons")

 **樹狀檢視消除歧義圖示的示例**

 **基於狀態的值分類**圖示存在以下狀態：活動、活動禁用和非活動禁用。

 ![基於分類值圖示的狀態&#45;](../../extensibility/ux-guidelines/media/0404-41-statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")

 **基於狀態的值分類圖示示例**

 **IntelliSense**圖示包含以下元素中的三個：一個基體、一個修改器和一個狀態。

 ![IntelliSense 圖示](../../extensibility/ux-guidelines/media/0404-42-intellisenseicons.png "0404-42_IntelliSenseIcons")

 **IntelliSense 圖示示例**

 **小型 （16x16） 專案**圖示不應具有兩個元素：一個基和一個修飾符。

 ![16x16 專案圖示 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-43-16x16project1.png "0404-43_16x16Project1") ![16x16 專案圖示 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44-16x16project2.png "0404-44_16x16Project2") ![16x16 專案圖示 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45-16x16project3.png "0404-45_16x16Project3")

 **小型 （16x16） 專案圖示示例**

 **大型 （32x32） 專案**圖示由以下元素中的四個組成：一個基體、一個到兩個修飾符和一個語言疊加。

 ![32x32 專案圖示](../../extensibility/ux-guidelines/media/0404-46-32x32project.png "0404-46_32x32Project")

 **大型 （32x32） 專案圖示示例**

### <a name="production-details"></a>生產詳細資訊
 所有新的 UI 元素都應使用 Windows 演示文稿基礎 （WPF） 創建，WPF 的所有新圖示應採用 32 位 PNG 格式。 24 位 PNG 是一種不支援透明度的舊版格式，因此不推薦用於圖示。

 將解析度保存在 96 DPI。

#### <a name="file-types"></a>檔案類型

- **32 位 PNG：** 圖示的首選格式。 可存儲單個柵格（圖元）圖像的無損資料壓縮檔案格式。 32 位 PNG 檔支援 Alpha 色板透明度、伽馬校正和隔行掃描。

- **32 位 BMP：** 用於非 WPF 控制項。 32 位 BMP 也稱為 XP 或高顏色，是 RGB/A 圖像格式，是具有 Alpha 色板透明度的真實彩色圖像。 Alpha 色板是在 Adobe Photoshop 中指定的一層透明度，然後作為附加（第四個）顏色通道保存在點陣圖中。 在圖稿製作期間，黑色背景將添加到所有 32 位 BMP 檔中，以提供有關色彩深度的快速視覺提示。 此黑色背景表示要在 UI 中遮罩的區域。

- **32 位 ICO：** 用於專案圖示和添加專案。 所有 ICO 檔案都是具有 Alpha 色板透明度 （RGB/A） 的 32 位真顏色。 由於 ICO 檔案可以存儲多種尺寸和色彩深度，Vista 圖示通常採用 ICO 格式，包含 16x16、32x32、48x48 和 256x256 圖像大小。 為了在 Windows 資源管理器中正確顯示，ICO 檔案必須為每個圖像大小保存為 24 位和 8 位色彩深度。

- **XAML：** 用於設計曲面和 Windows 裝飾器。 XAML 圖示是基於向量的影像檔，支援縮放、旋轉、歸檔和透明度。 它們在視覺工作室中並不常見，但由於它們的靈活性而越來越受歡迎。

- **SVG**

- **24 位 BMP：** 用於視覺化工作室命令列。 24 位 BMP 是一種真實彩色 RGB 圖像格式，它是一種圖示約定，它使用洋紅色 （R=255、G=0、 B=255） 作為仿冒透明度圖層的顏色鍵來創建透明度層。 在 24 位 BMP 中，所有洋紅色曲面都使用背景顏色顯示。

- **24 位 GIF：** 用於視覺化工作室命令列。 支援透明度的真彩色 RGB 圖像格式。 GIF 檔通常用於嚮導圖稿和 GIF 動畫。

### <a name="icon-construction"></a>圖示結構
 Visual Studio 中最小的圖示大小為 16x16。 最大的常用是32x32。 在設計圖示時，請注意不要填滿整個 16x16、24x24 或 32x32 幀。 清晰、均勻的圖示結構對於使用者識別至關重要。 構建圖示時，應遵守以下幾點。

- 圖示應該清晰、易懂且一致。

- 最好將狀態通知元素用作單個圖示，而不是將它們堆疊在圖示基礎元素之上。 在某些上下文中，UI 可能需要狀態元素與基元素配對。

- 專案圖示通常是包含多個大小的 .ico 檔。 僅更新 16x16、24x24 和 32x32 圖示。 大多數 16x16 和 24x24 圖示將包含相同的元素。 32x32 圖示包含更多詳細資訊，包括專案語言類型（如果適用）。

- 對於 32x32 圖示，基本元素通常具有 2 圖元的線粗。 1 圖元或 2 圖元的線粗可用於細節元素。 用你最好的判斷來確定哪個更合適。

- 元素之間至少有 1 圖元間距，用於 16x16 和 24x24 圖示。 對於 32x32 圖示，在元素之間以及修改器和基本元素之間使用 2 圖元間距。

  ![可容納 16x16、24x24 和 32x32 圖示的項目間距](../../extensibility/ux-guidelines/media/0404-47-elementspacing.png "0404-47_ElementSpacing")

  **大小為 16x16、24x24 和 32x32 的圖示的元素間距**

#### <a name="color-and-accessibility"></a>顏色和可訪問性
 Visual Studio 合規性準則要求產品中的所有圖示都通過顏色和對比度的協助工具要求。 這是通過圖示反轉實現的，當您正在設計時，您應該意識到它們將在產品中以程式設計方式反轉。

 有關在視覺工作室圖示中使用顏色的詳細資訊，請參閱[在圖像中使用顏色](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)。

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>在圖像中使用顏色

### <a name="overview"></a>概觀
 視覺工作室中的圖示主要是單色的。 顏色是保留以傳達特定資訊，永遠不會用於裝飾。 顏色使用：

- 指示操作

- 提醒使用者狀態通知

- 指定語言隸屬關係

- 區分 IntelliSense 中的專案

### <a name="accessibility"></a>Accessibility
 Visual Studio 合規性準則要求所有簽入產品的圖示都通過顏色和對比度的協助工具要求。 視覺語言調色板中的顏色已經過測試並滿足這些要求。

#### <a name="color-inversion-for-dark-themes"></a>深色主題的顏色反轉
 為了使圖示在 Visual Studio 黑暗主題中以正確的對比度顯示，以程式設計方式應用反轉。 本指南中的顏色部分被選中，以便它們正確反轉。 將顏色的使用限制為此調色板，否則在應用反轉時，您將獲得不可預知的結果。

 ![已對換色彩的圖示範例](../../extensibility/ux-guidelines/media/0405-01-darkthemeinversion.png "0405-01_DarkThemeInversion")

 **顏色反轉的圖示示例**

### <a name="base-palette"></a>基本調色板
 所有標準圖示包含三種基本顏色。 圖示不包含漸變或陰影，3D 工具圖示有一個或兩個例外。

|使用量|名稱|值（淺色主題）|樣本|範例|
|-----------|----------|---------------------------|------------|-------------|
|背景/黑暗|VS BG|424242 / 66,66,66|![樣本 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|![基礎調色盤範例](../../extensibility/ux-guidelines/media/0405-02-basepaletteexample.png "0405-02_BasePaletteExample")|
|前景/燈光|VS FG|F0EFF1 / 240，239，241|![樣本 F0EFF1](../../extensibility/ux-guidelines/media/0405-f0eff1.png "0405_F0EFF1")||
|外框|VS 出|F6F6F6 / 246，246，246|![樣本 F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")||

 除了基本顏色之外，每個圖示可能包含擴展調色板中的一個附加顏色。

### <a name="extended-palette"></a>擴展調色板

#### <a name="action-modifiers"></a>操作修改器
 以下四種顏色指示操作修改器所需的操作類型：

|使用量|名稱|值（所有主題）|樣本|
|-----------|----------|--------------------------|------------|
|Positive|VS 動作綠色|388A34 / 56，138，52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Neutral|VS 動作紅色|A1260D / 161，38，13|![樣本 A1260D](../../extensibility/ux-guidelines/media/0405-a1260d.png "0405_A1260D")|
|中性|VS 動作藍色|00539C / 0，83，156|![樣本 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|創建/新建|VS 動作橙色|C27D1A / 194，156，26|![樣本 C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>範例
 綠色用於積極動作修改符，如"添加"、"運行"、"播放"和"驗證"。

|||||
|-|-|-|-|
|![運行圖示](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun")**運行**|![執行查詢圖示](../../extensibility/ux-guidelines/media/0405-04-executequery.png "0405-04_ExecuteQuery")**執行查詢**|![播放所有步驟圖示](../../extensibility/ux-guidelines/media/0405-05-playallsteps.png "0405-05_PlayAllSteps")**"播放所有步驟"**|![添加控制項圖示](../../extensibility/ux-guidelines/media/0405-06-addcontrol.png "0405-06_AddControl")**添加控制項**|

 紅色用於否定動作修改器，如"刪除"、"停止"、"取消"和"關閉"。

|||||
|-|-|-|-|
|![刪除關係圖示](../../extensibility/ux-guidelines/media/0405-07-deleterelationship.png "0405-07_DeleteRelationship")**刪除關係**|![刪除列圖示](../../extensibility/ux-guidelines/media/0405-08-deletecolumn.png "0405-08_DeleteColumn")**刪除列**|![停止查詢圖示](../../extensibility/ux-guidelines/media/0405-09-stopquery.png "0405-09_StopQuery")**停止查詢**|![連接離線圖示](../../extensibility/ux-guidelines/media/0405-10-connectionoffline.png "0405-10_ConnectionOffline")**連接離線**|

 藍色應用於最常表示為箭頭的中性操作修改器，例如"打開"、"下一步"、"上一個"、"導入"和"匯出"。

|||||
|-|-|-|-|
|![轉到欄位圖示](../../extensibility/ux-guidelines/media/0405-11-gotofield.png "0405-11_GoToField")**轉到欄位**|![批次處理檢查&#45;在圖示](../../extensibility/ux-guidelines/media/0405-12-batchedcheckin.png "0405-12_BatchedCheckIn")**批次處理簽入**|![位址編輯器圖示](../../extensibility/ux-guidelines/media/0405-13-addresseditor.png "0405-13_AddressEditor")**位址編輯器**|![關聯編輯器圖示](../../extensibility/ux-guidelines/media/0405-14-associationeditor.png "0405-14_AssociationEditor")**關聯編輯器**|

 深色主要用於"新建"修改器。

|||||
|-|-|-|-|
|![新專案圖示](../../extensibility/ux-guidelines/media/0405-15-newproject.png "0405-15_NewProject")**新專案**|![創建新圖形圖示](../../extensibility/ux-guidelines/media/0405-16-createnewgraph.png "0405-16_CreateNewGraph")**創建新圖形**|![新單元測試圖示](../../extensibility/ux-guidelines/media/0405-17-newunittest.png "0405-17_NewUnitTest")**新單元測試**|![新建清單項圖示](../../extensibility/ux-guidelines/media/0405-18-newlistitem.png "0405-18_NewListItem")**"新建清單項"**|

#### <a name="special-cases"></a>特殊案例
 在特殊情況下，彩色動作修改器可以單獨用作獨立圖示。 用於圖示的顏色反映圖示關聯的操作。 此使用僅限於圖示的一小部分，包括：

||||||
|-|-|-|-|-|
|![運行圖示](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun")**運行**|![停止圖示](../../extensibility/ux-guidelines/media/0405-19-stop.png "0405-19_Stop")**停止**|![刪除圖示](../../extensibility/ux-guidelines/media/0405-20-delete.png "0405-20_Delete")**刪除**|![保存圖示](../../extensibility/ux-guidelines/media/0405-21-save.png "0405-21_Save")**保存**|![向後導航圖示](../../extensibility/ux-guidelines/media/0405-22-navigateback.png "0405-22_NavigateBack")**向後導航**|

### <a name="code-hierarchy-palette"></a>代碼層次結構調色板

#### <a name="folder"></a>資料夾

|使用量|名稱|值（所有主題）|樣本|範例|
|-----------|----------|--------------------------|------------|-------------|
|資料夾|資料夾|DCB67A / 220，182，122|![樣本 DCB67A](../../extensibility/ux-guidelines/media/0405-dcb67a.png "0405_DCB67A")|![資料夾色彩圖示](../../extensibility/ux-guidelines/media/0405-23-foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>視覺工作室語言
 Visual Studio 中提供的每個通用語言或平臺都有關聯的顏色。 這些顏色用於基本圖示，或出現在複合圖示右上角的語言修飾符上。

|使用量|名稱|值（所有主題）|樣本|
|-----------|----------|--------------------------|------------|
|ASP， HTML， WPF|ASP HTML WPF 藍色|0095D7 / 0，149，215|![樣本 0095D7](../../extensibility/ux-guidelines/media/0405-0096d7.png "0405_0096D7")|
|C++|CPP 紫色|9B4F96 / 155，79，150|![樣本 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|C#|CS 綠色 （VS 動作綠色）|388A34 / 56，138，52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|CSS|CSS 紅色|BD1E2D / 189，30，45|![樣本 BD1E2D](../../extensibility/ux-guidelines/media/0405-bd1e2d.png "0405_BD1E2D")|
|F#|FS 紫色|672878 / 103,40,120|![樣本 672878](../../extensibility/ux-guidelines/media/0405-672878.png "0405_672878")|
|JavaScript|JS 橙色|F16421 / 241，100，33|![樣本 F16421](../../extensibility/ux-guidelines/media/0405-f16421.png "0405_F16421")|
|VB|VB 藍色 （VS 動作藍）|00539C / 0，83，156|![樣本 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|TypeScript|TS 橙色|E04C06 / 224，76，6|![樣本 E04C06](../../extensibility/ux-guidelines/media/0405-e04c06.png "0405_E04C06")|
|Python|PY 綠色|879636 / 135,150,54|![樣本 879636](../../extensibility/ux-guidelines/media/0405-879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>帶有語言修飾符的圖示示例

|||||||
|-|-|-|-|-|-|
|![視覺基本圖示](../../extensibility/ux-guidelines/media/0405-25-vb.png "0405-25_VB") **VB**|![C&#35;圖示](../../extensibility/ux-guidelines/media/0405-26-csharp.png "0405-26_CSharp") **C#**|![C&#43;&#43; 圖示](../../extensibility/ux-guidelines/media/0405-27-cplusplus.png "0405-27_CPlusPlus")**C++**|![F&#35;圖示](../../extensibility/ux-guidelines/media/0405-28-fsharp.png "0405-28_FSharp") **F#**|![JavaScript 圖示](../../extensibility/ux-guidelines/media/0405-29-javascript.png "0405-29_JavaScript") **JavaScript**|![Python 圖示](../../extensibility/ux-guidelines/media/0405-30-python.png "0405-30_Python") **Python**|
|![HTML 圖示](../../extensibility/ux-guidelines/media/0405-31-html.png "0405-31_HTML") **HTML**|![WPF 圖示](../../extensibility/ux-guidelines/media/0405-32-wpf.png "0405-32_WPF") **WPF**|![ASP 圖示](../../extensibility/ux-guidelines/media/0405-33-asp.png "0405-33_ASP") **ASP**|![CSS 圖示](../../extensibility/ux-guidelines/media/0405-34-css.png "0405-34_CSS") **CSS**|![類型腳本圖示](../../extensibility/ux-guidelines/media/0405-35-typescript.png "0405-35_TypeScript")**類型腳本**||

#### <a name="intellisense"></a>IntelliSense
 IntelliSense 圖示使用獨佔調色板。 這些顏色用於説明使用者快速區分 IntelliSense 快顯視窗中的不同項。

|使用量|名稱|值（所有主題）|樣本|
|-----------|----------|--------------------------|------------|
|類， 事件|VS 動作橙色|C27D1A / 194，125，26|![樣本 C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|
|擴充方法、方法、模組、委託|VS 動作紫色|652D90 / 101，45，144|![樣本 652D90](../../extensibility/ux-guidelines/media/0405-652d90.png "0405_652D90")|
|欄位， 枚舉項， 宏， 結構， 聯合數值型別， 運算子， 介面|VS 動作藍色|00539C / 0，83，156|![樣本 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Object|VS 動作綠色|388A34 / 56，138，52|![樣本 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|常量、 異常、 枚舉項、 映射、 地圖項、 命名空間、 範本、 類型定義|背景 （VS BG）|424242 / 66,66,66|![樣本 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>IntelliSense 圖示示例

||||||
|-|-|-|-|-|
|![IntelliSense 類圖示](../../extensibility/ux-guidelines/media/0405-36-intellisenseclass.png "0405-36_IntelliSenseClass")**類**|![IntelliSense 私人活動圖示](../../extensibility/ux-guidelines/media/0405-37-intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")**私人事件**|![IntelliSense 代表圖示](../../extensibility/ux-guidelines/media/0405-38-intellisensedelegate.png "0405-38_IntelliSenseDelegate")**委託**|![IntelliSense 方法好友圖示](../../extensibility/ux-guidelines/media/0405-39-intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")**方法 好友**|![欄位圖示](../../extensibility/ux-guidelines/media/0405-40-field.png "0405-40_Field")**欄位**|
|![IntelliSense 受保護的枚舉項圖示](../../extensibility/ux-guidelines/media/0405-41-intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")**受保護枚舉項**|![智慧感知物件圖示](../../extensibility/ux-guidelines/media/0405-42-intellisenseobject.png "0405-42_IntelliSenseObject")**物件**|![IntelliSense 範本圖示](../../extensibility/ux-guidelines/media/0405-43-intellisensetemplate.png "0405-43_IntelliSenseTemplate")**範本**|![IntelliSense 異常快捷方式圖示](../../extensibility/ux-guidelines/media/0405-44-intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")**異常快捷方式**||

### <a name="notifications"></a>通知
 視覺化工作室中的通知用於指示狀態。 通知調色板使用以下四種顏色以及黑色或白色前景填充選項來定義具有以下狀態級別的通知。

|使用量|名稱|值（所有主題）|樣本|
|-----------|----------|--------------------------|------------|
|狀態：中性|通知藍色 （VS 藍色）|1BA1E2 / 27，161，226|![樣本 1BA1E2](../../extensibility/ux-guidelines/media/0405-1ba1e2.png "0405_1BA1E2")|
|狀態： 正|通知綠色（VS 綠色）|339933 / 51,153,51|![樣本 339933](../../extensibility/ux-guidelines/media/0405-339933.png "0405_339933")|
|狀態： 負|通知紅色（VS 紅色）|E51400 / 229，20，0|![樣本 E51400](../../extensibility/ux-guidelines/media/0405-e51400.png "0405_E51400")|
|狀態：警告|通知黃色（VS 橙色）|FFCC00 / 255，204，0|![樣本 FFCC00](../../extensibility/ux-guidelines/media/0405-ffcc00.png "0405_FFCC00")|
|前景填充|通知黑色（黑色）|000000 / 0,0,0|![斯沃琪&#35;00000](../../extensibility/ux-guidelines/media/0405-000000.png "0405_000000")|
|前景填充|通知白色（白色）|FFFFFF / 255，255，255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>通知圖示示例

|||||
|-|-|-|-|
|![警報圖示](../../extensibility/ux-guidelines/media/0405-45-alert.png "0405-45_Alert")**警報**|![警告圖示](../../extensibility/ux-guidelines/media/0405-48-warning.png "0405-48_Warning")**警告**|![完成圖示](../../extensibility/ux-guidelines/media/0405-46-complete.png "0405-46_Complete")**完成**|![停止圖示](../../extensibility/ux-guidelines/media/0405-47-stop.png "0405-47_Stop")**停止**|

### <a name="visual-studio-online"></a>Visual Studio Online
 通常，視覺化工作室連線功能由託管在瀏覽器中的功能組成。 顏色在不同的環境中不同，但樣式保持不變。

|群組|使用量|名稱|值（所有主題）|樣本|
|-----------|-----------|----------|--------------------------|------------|
|TFS|背景|TFSO BG|656565/ 101, 101, 101|![樣本 656565](../../extensibility/ux-guidelines/media/0405-656565.png "0405_656565")|
|TFS|外框|TFSO 出|FFFFFF / 255， 255， 255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|納帕|背景|白色|FFFFFF / 255， 255， 255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|摩納哥|背景|白色|FFFFFF / 255， 255， 255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|背景|白色|FFFFFF / 255， 255， 255|![樣本 FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|正常|F12 Grey_Primary|555555 / 85, 85, 85|![樣本 555555](../../extensibility/ux-guidelines/media/0405-555555.png "0405_555555")|
|F12|暫留|F12 Blue_Hover|2279BF / 34，121，191|![樣本 2279BF](../../extensibility/ux-guidelines/media/0405-2279bf.png "0405_2279BF")|
|F12|已停用|F12 LtGrey_Disabled|阿巴巴奇 / 171，171，172|![樣本 ABABAC](../../extensibility/ux-guidelines/media/0405-ababac.png "0405_ABABAC")|
|F12|懸停背景|懸停 bg|D9EBF7 / 217，235，247|![樣本 D9EBF7](../../extensibility/ux-guidelines/media/0405-d9ebf7.png "0405_D9EBF7")|
|F12|按下的背景|按下 bg|B2D7F0 / 178，215，240|![樣本 B2D7F0](../../extensibility/ux-guidelines/media/0405-b2d7f0.png "0405_B2D7F0")|
|F12|外框|VS 出|F6F6F6 / 246，246，246|![樣本 F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")|
|F12|資訊|資訊|00BCF2 / 0，188，242|![樣本 00BCF2](../../extensibility/ux-guidelines/media/0405-00bcf2.png "0405_00BCF2")|
|F12|警告|警告|F28300 / 242，131，0|![樣本 F28300](../../extensibility/ux-guidelines/media/0405-f28300.png "0405_F28300")|
|F12|錯誤/負|Error_Negative|E81123 / 232，17，35|![樣本 E81123](../../extensibility/ux-guidelines/media/0405-e81123.png "0405_E81123")|
|F12|開始/正|Start_Positive|009E49 / 0，158，73|![樣本 009E49](../../extensibility/ux-guidelines/media/0405-009e49.png "0405_009E49")|
|F12|中斷類型|中斷類型|9B4F96 / 155，79，150|![樣本 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|F12|事件標記|事件標記|A51F00 / 165，31，0|![樣本 A51F00](../../extensibility/ux-guidelines/media/0405-a51f00.png "0405_A51F00")|
|F12|使用者標記|使用者標記|F16220 / 241，98，32|![樣本 F16220](../../extensibility/ux-guidelines/media/0405-f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>視覺工作室線上圖示示例

|TFS 線上||||
|----------------|-|-|-|
|![TFS 線上團隊圖示](../../extensibility/ux-guidelines/media/0405-49-tfsonlineteam.png "0405-49_TFSOnlineTeam")**線上團隊**|![TFS 資訊圖示](../../extensibility/ux-guidelines/media/0405-50-tfsinformation.png "0405-50_TFSInformation")**資訊**|![TFS 歷史記錄圖示](../../extensibility/ux-guidelines/media/0405-51-tfshistory.png "0405-51_TFSHistory")**歷史記錄**|![TFS 分支圖示](../../extensibility/ux-guidelines/media/0405-52-tfsbranch.png "0405-52_TFSBranch")**分支**|

|納帕||||
|----------|-|-|-|
|![納帕內容圖示](../../extensibility/ux-guidelines/media/0405-53-napacontent.png "0405-53_NapaContent")**內容**|![納帕辦公室郵件圖示](../../extensibility/ux-guidelines/media/0405-54-napaofficemail.png "0405-54_NapaOfficeMail")**辦公室郵件**|![納帕共用點圖示](../../extensibility/ux-guidelines/media/0405-55-napasharepoint.png "0405-55_NapaSharePoint")**共用點**|![納帕工作窗格圖示](../../extensibility/ux-guidelines/media/0405-56-napataskpane.png "0405-56_NapaTaskPane")**工作窗格**|

|摩納哥||||
|------------|-|-|-|
|![摩納哥 檔 圖示](../../extensibility/ux-guidelines/media/0405-57-monacofiles.png "0405-57_MonacoFiles")**檔**|![摩納哥 Git 圖示](../../extensibility/ux-guidelines/media/0405-58-monacogit.png "0405-58_MonacoGit") **Git**|![摩納哥搜索圖示](../../extensibility/ux-guidelines/media/0405-59-monacosearch.png "0405-59_MonacoSearch")**搜索**|![摩納哥 文本 圖示](../../extensibility/ux-guidelines/media/0405-60-monacotext.png "0405-60_MonacoText")**文本**|

|F12||||
|---------|-|-|-|
|![F12 漂亮的代碼圖示](../../extensibility/ux-guidelines/media/0405-61-f12prettycode.png "0405-61_F12PrettyCode")**漂亮的代碼**|![F12 警告圖示](../../extensibility/ux-guidelines/media/0405-62-f12warning.png "0405-62_F12Warning")**警告**|![F12 類比圖示](../../extensibility/ux-guidelines/media/0405-63-f12emulate.png "0405-63_F12Emulate")**類比**|
