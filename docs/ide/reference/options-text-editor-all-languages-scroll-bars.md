---
title: 選項、文字編輯器、所有語言、捲軸
ms.date: 10/25/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Scroll_Bars
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 881f995dc8f4c675691f7eaa63d26acefd4b3d01
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876782"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>選項、文字編輯器、所有語言、捲軸
這個對話方塊可讓您變更程式碼編輯器捲軸的預設行為。 若要顯示這些選項，請從 [工具] 功能表選取 [選項]。 在 [文字編輯器] 資料夾內，展開 [所有語言] 子資料夾，然後選擇 [捲軸]。

> [!CAUTION]
> 此頁面會設定所有開發語言的預設選項。 重設此對話方塊中的選項，會將所有語言中的 [捲軸] 選項重設為此處所選選項。 若只要變更單一語言的文字編輯器選項，請展開該語言的子資料夾，然後選取其選項頁面。

## <a name="show-horizontal-scroll-bar"></a>顯示水平捲軸

選取時，會顯示水平捲軸；您可以左右捲動來檢視位於編輯器檢視區域外的項目。 如果未顯示水平捲軸，您可以使用方向鍵捲動。

## <a name="show-vertical-scroll-bar"></a>顯示垂直捲軸

選取時，會顯示垂直捲軸；您可以上下捲動來檢視位於編輯器檢視區域外的項目。 如果未顯示垂直捲軸，您可以使用 Page Up、Page Down 鍵和方向鍵來捲動。

## <a name="display"></a>顯示

### <a name="show-annotations-over-vertical-scroll-bar"></a>在垂直捲軸上顯示註釋

選取垂直捲軸是否會顯示下列註釋：

- 已變更
- 標記
- 錯誤
- 插入號位置

> [!TIP]
> [顯示標記] 選項包含中斷點與書籤。

開啟大型程式碼檔案來試用看看，並取代一些在檔案中數個位置出現的文字。 捲軸會顯示出您改動過的內容，因此如果您改掉了不該更動的東西，可以將變更還原。

## <a name="behavior"></a>行為

捲軸有兩種模式：捲軸模式和地圖模式。

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>垂直捲軸使用捲軸模式

*捲軸模式*會在捲軸上顯示註釋指標。 在捲軸上按一下會向上或向下捲動頁面，但不會跳至檔案中的該位置。

### <a name="use-map-mode-for-vertical-scroll-bar"></a>垂直捲軸使用地圖模式

在「地圖模式」中，當您在捲軸上按一下某個位置時，游標會跳至檔案中的該位置，而不是只向上或向下捲動頁面。 程式碼的縮圖顯示在捲軸上。 您可以在 [原始檔概觀] 中選擇值，以變更地圖欄的的寬度。 若要在您將指標停在地圖上時顯示大型程式碼預覽，請選擇 [顯示預覽工具提示] 選項。 摺疊的區域會以不同的陰影呈現，並且在您按兩下時展開。

> [!TIP]
> 若要在地圖模式中關閉縮圖程式碼檢視，您可以將 [原始檔檢視] 設定為 [關閉]。 如果已選取 [顯示預覽工具提示]，當您將指標暫留在捲軸上時，您仍然會看到該位置的程式碼預覽，且當您按一下時，游標仍然會跳至該位置。

## <a name="see-also"></a>另請參閱

- [如何：自訂捲軸](../how-to-track-your-code-by-customizing-the-scrollbar.md)