---
title: 多重游標編輯
description: 在 Visual Studio for Mac 中編輯程式碼時，在多個位置插入文字。
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451444"
---
# <a name="multi-caret-editing"></a>多重游標編輯

多重插入號編輯可讓您一次加入_n_個插入點。 在多重插入號模式中，您可以透過滑鼠按一下或透過鍵盤命令，將其他插入號新增至您的檔。 主要插入號是以紅色游標表示，而次要插入號則以淺藍色的色彩呈現。 您可以透過 `ESC` 鍵停用多個插入號編輯模式。

## <a name="enabling-multi-caret-editing"></a>啟用多重游標編輯

### <a name="keyboard"></a>鍵盤

您可以透過鍵盤以數種方式啟用多重插入號模式。 下表提供可用來輸入多個插入點編輯之特定模式的鍵盤快速鍵：

| 熱鍵  | 動作                        | 
|---------| ------------------------------|
|  ⌥⇧。   | 插入下一個相符的插入號    | 
|  ⌥⇧;   | 在所有相符的位置插入插入號 | 
|  ⌥⇧，   | 移除最後一個插入號             | 
|  ⌥⇧/   | 向下移動上一個插入號          | 

當您叫用命令時，這些行為都會錨定到插入號的目前位置。 例如，如果插入號是在 "name" 一字的開頭，而且您叫用「插入插入號的所有相符」（⌥⇧;)在目前檔中，單字 "name" 的每個實例都會在單字開頭插入一個插入號。 同樣地，如果您叫用命令「插入下一個相符的插入號」（⌥⇧），則插入號將會放在 "name" 這個字的下一個實例。 可以多次叫用此命令。

![多插入號鍵盤](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>滑鼠/觸控板

藉由使用您的游標，您可以為多個插入號釋放選取特定的插入點。 當鍵盤快速鍵系結至相符的字串時，您可以使用游標在檔中的任何位置手動插入插入點。 設定插入號之後，每個都會回應您在鍵盤上輸入的按鍵專案。

若要使用滑鼠插入多個插入號，您必須按住則是⌘⌥，然後按一下您想要輸入插入號的位置。 只要保留則是⌘⌥索引鍵，您就會處於插入模式。 如果您在不正確的位置插入插入號，可以繼續保留則是⌘⌥，然後再按一下相同的區域，以移除插入號。 當您的所有插入號都位於您想要的位置之後，請停止按下則是⌘⌥鍵並開始輸入。 下列 GIF 示範如何選取一組插入點，以及移除錯誤設定的點。

![多插入號滑鼠](media/multi-caret-mouse.gif)

## <a name="see-also"></a>請參閱

- [快速動作 (Windows 上的 Visual Studio)](/visualstudio/ide/quick-actions)
- [重構程式碼 (Windows 上的 Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
