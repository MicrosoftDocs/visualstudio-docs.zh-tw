---
title: 多重游標編輯
description: 在 Visual Studio for Mac 中編輯程式碼時，在多個位置插入文字。
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451444"
---
# <a name="multi-caret-editing"></a>多重游標編輯

多重插入點編輯可讓您一次新增 _n_ 個插入點數目。 處於多重插入號模式時，您可以透過滑鼠點擊或透過鍵盤命令，將其他游標新增至您的檔。 主要插入號是以紅色游標表示，而次要游標則以淺藍色色彩表示。 您可以透過金鑰停用多重插入號編輯模式 `ESC` 。

## <a name="enabling-multi-caret-editing"></a>啟用多重插入點編輯

### <a name="keyboard"></a>鍵盤

您可以透過鍵盤以數種方式啟用多重插入號模式。 下表提供可用來輸入多個插入式編輯之特定模式的鍵盤快速鍵：

| 熱鍵  | 動作                        | 
|---------| ------------------------------|
|  ⌥⇧.   | 插入下一個相符的插入號    | 
|  ⌥⇧;   | 在所有相符的位置插入游標 | 
|  ⌥⇧,   | 移除最後一個插入號             | 
|  ⌥⇧/   | 將最後一個插入號下移          | 

當您叫用命令時，這些行為都會錨定到插入號的目前位置。 例如，如果插入號是在 "name" 一字的開頭，而您叫用 [在所有相符的字元插入游標] (⌥⇧; ) 您目前檔中的每個 "name" 一字的實例都會在單字開頭插入插入號。 同樣地，如果您叫用 [插入下一個相符的插入號] 命令 (⌥ ) ⇧]，則會將插入號放在 "name" 這個字的下一個實例。 您可以多次叫用此命令。

![多個插入號鍵盤](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>滑鼠/觸控板

藉由使用游標，您可以為多個游標釋放選取特定的插入點。 當鍵盤快速鍵系結至相符的字串時，您可以手動將插入點插入檔中包含游標的位置。 設定游標之後，每個都將會回應您在鍵盤上輸入的按鍵專案。

若要使用滑鼠插入多個游標，您必須按住⌘⌥，然後按一下您想要輸入游標的位置。 只要保留了⌘⌥金鑰，您就會處於插入模式。 如果您在不正確的位置插入插入號，則可以繼續保留⌘⌥並在相同區域中按一下，以移除插入號。 當您將所有游標放在您想要的位置之後，請停止按下⌘⌥鍵，然後開始輸入。 下列 GIF 示範如何選取一組插入點，以及移除錯誤的設定點。

![多點插入滑鼠](media/multi-caret-mouse.gif)

## <a name="see-also"></a>另請參閱

- [快速動作 (Windows 上的 Visual Studio)](/visualstudio/ide/quick-actions)
- [重構程式碼 (Windows 上的 Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
