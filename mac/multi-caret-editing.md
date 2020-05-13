---
title: 多重游標編輯
description: 在 Mac 的 Visual Studio 中編輯代碼時，在多個位置插入文本。
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451444"
---
# <a name="multi-caret-editing"></a>多重游標編輯

多卡子編輯允許您在一次添加_n_個插入點數。 在多卡多模式下，您可以通過滑鼠按一下或鍵盤命令向文檔添加其他支援。 主護符由紅色游標表示，而輔助護符以淺藍色表示。 可通過`ESC`鍵禁用多卡編輯模式。

## <a name="enabling-multi-caret-editing"></a>啟用多卡編輯

### <a name="keyboard"></a>鍵盤

您可以通過鍵盤以多種方式啟用多卡接模式。 下表提供了可用於輸入特定多卡編輯模式的鍵盤快速鍵：

| 熱鍵  | 動作                        | 
|---------| ------------------------------|
|  ⌥⇧.   | 插入下一個匹配的 care    | 
|  ⌥⇧;   | 在所有匹配時插入卡子 | 
|  ⌥⇧,   | 刪除上次護理             | 
|  ⌥⇧/   | 向下移動最後一個護理          | 

調用命令時，這些行為中的每一個都定位到 care 的當前位置。 例如，如果 caret 位於單詞"name"的開頭，並且調用"在所有匹配時插入 caret"（;)當前文檔中"name"一詞的每個實例都將在單詞的開頭插入一個插入的插入器。 同樣，如果調用命令"插入下一個匹配的 caret"（*），則一個貼子將放置在單詞"name"的下一個實例中。 此命令可以多次調用。

![多卡式鍵盤](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>滑鼠/觸控板

通過使用游標，您可以為多個游標自由選擇特定的插入點。 當鍵盤快速鍵綁定到匹配字串時，您可以使用游標在文檔中的任意位置手動插入一個插入器。 設置圖子後，每個內容都將與您在鍵盤上鍵入的鍵條目相呼應。

要使用滑鼠插入多個插入，必須按住 *並按一下要輸入的插入器的位置。 只要持有 +鍵，您就會處於插入模式。 如果在錯誤的位置插入一個 care，則可以通過繼續按住 * 並再次按一下同一區域來刪除該 care。 一旦你有所有的卡子位於你想的地方，停止按 # 鍵並開始鍵入。 以下 GIF 演示了選擇一組插入點以及刪除錯誤設置的點。

![多卡式滑鼠](media/multi-caret-mouse.gif)

## <a name="see-also"></a>另請參閱

- [快速動作 (Windows 上的 Visual Studio)](/visualstudio/ide/quick-actions)
- [重構程式碼 (Windows 上的 Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
