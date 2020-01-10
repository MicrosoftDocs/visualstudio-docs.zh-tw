---
title: 捲軸地圖模式和捲軸模式
ms.date: 09/25/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22436c221813ec4c3701d208fc74a96b403fff9c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591394"
---
# <a name="how-to-customize-the-scroll-bar"></a>如何：自訂捲軸

當您遇到長的程式碼檔案時，可能很難追蹤所有項目在檔案中的位置。 您可以自訂程式碼編輯器的捲軸，以獲得程式碼目前狀況的概觀。

## <a name="annotations"></a>標註

您可以選擇捲軸是否要顯示程式碼變更、中斷點、書籤、錯誤與插入號位置等註釋。

   1. 選擇 [工具] > [選項] > [文字編輯器] > [所有語言] > [捲軸]，以開啟 [捲軸] 選項頁面。

   2. 選取 [在垂直捲軸上顯示註釋]，然後選取想要看到的註釋。 可用的註釋：

      - 變更
      - 標記
      - 錯誤
      - 插入號位置

      > [!TIP]
      > [顯示標記] 選項包含中斷點與書籤。

開啟大型程式碼檔案來試用看看，並取代一些在檔案中數個位置出現的文字。 捲軸會顯示出您改動過的內容，因此如果您改掉了不該更動的東西，可以將變更還原。

以下是在搜尋字串之後，捲軸呈現的外觀。 請注意，字串的所有執行個體都出現在捲軸中。

![搜尋字串之後的 Visual Studio 捲軸](../ide/media/enhancedscrollbarsearch.png)

以下是取代字串所有出現處之後的捲軸外觀。 捲軸中的紅色標記顯示文字取代發生錯誤的位置。

![取代字串發生錯誤後的 Visual Studio 捲軸](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>顯示模式

捲軸有兩種模式：捲軸模式和地圖模式。

### <a name="bar-mode"></a>捲軸模式

*捲軸模式*會在捲軸上顯示註釋指標。 在捲軸上按一下會向上或向下捲動頁面，但不會跳至檔案中的該位置。

### <a name="map-mode"></a>地圖模式

在「地圖模式」中，當您在捲軸上按一下某個位置時，游標會跳至檔案中的該位置，而不是只向上或向下捲動頁面。 程式碼的縮圖顯示在捲軸上。 您可以在 [原始檔概觀] 中選擇值，以變更地圖欄的的寬度。 若要在您將指標停在地圖上時顯示大型程式碼預覽，請選擇 [顯示預覽工具提示] 選項。 摺疊的區域會以不同的陰影呈現，並且在您按兩下時展開。

> [!TIP]
> 若要在地圖模式中關閉縮圖程式碼檢視，您可以將 [原始檔檢視] 設定為 [關閉]。 如果已選取 [顯示預覽工具提示]，當您將指標暫留在捲軸上時，您仍然會看到該位置的程式碼預覽，且當您按一下時，游標仍然會跳至該位置。

下列影像顯示開啟地圖模式且寬度設定為 [中] 的搜尋範例：

![處於地圖模式中的 Visual Studio 捲軸](../ide/media/enhancedscrollbar.png)

下列影像顯示 [預覽工具提示] 選項：

![具有工具提示的 Visual Studio 捲軸](../ide/media/enhancedscrollbarsearchtooltip.png)

## <a name="see-also"></a>請參閱

- [程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md)
