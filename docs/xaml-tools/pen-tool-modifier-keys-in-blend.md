---
title: 畫筆工具輔助按鍵
titleSuffix: Blend for Visual Studio
description: 瞭解 Blend for Visual Studio 中的畫筆工具輔助按鍵，以在您使用畫筆工具建立路徑時存取用來修改路徑的命令。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c3ab14c6-a320-46db-a6b3-7fd1ca261587
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 233ee9e4583e893d38700088d54e4b0e5eacffb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846266"
---
# <a name="pen-tool-modifier-keys-in-blend-for-visual-studio"></a>Blend for Visual Studio 中的畫筆工具輔助按鍵

下表列出當您使用 [畫筆] 工具 ![[畫筆] 工具](../designers/media/d514358f-185a-412f-a55d-36633b25dc8a.png) 建立路徑時，可用於修改路徑的快速鍵。 您也可以使用 [畫筆] 工具，加入或移除現有路徑上的點，或結合兩個現有路徑。

|若要執行這項操作|執行方式|Pointer|
| - |-------------|-------------|
|建立直線線段的起點|按一下以建立新的點|![建立直線線段的起點](../designers/media/0bfb1b71-80ac-4ad4-aed8-40e09f8b7ab8.png)<br /><br /> 畫筆指標|
|建立曲線線段的起點|按一下以建立新的點，然後拖曳新點以調整正切函數控點，再鬆開滑鼠按鈕。|![建立曲線線段的起點](../designers/media/0bfb1b71-80ac-4ad4-aed8-40e09f8b7ab8.png)<br /><br /> 畫筆指標|
|在沒有平滑限制的情況下調整最後一個正切函數，可讓您製作出尖角。|按一下以建立新的點，然後按 **Alt** 鍵|![調整沒有平滑限制的最後一個正切函數](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png)<br /><br /> 畫筆調整指標|
|分割最後一個正切函數，使正切函數的結束點分別作用，讓您製作出尖角。|按一下以建立新的點，然後按住 **Alt** 鍵並拖曳，再鬆開滑鼠按鈕|![分割最後一個正切函數，使正切函數的結束點分別作用](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png)<br /><br /> 畫筆調整指標|
|將正切函數結束點繞著新的點移動 15 度角|按一下以建立新的點，然後按住 **Shift** + **Alt** 並拖曳，再放開滑鼠按鍵|![將正切函數結束點繞著新的點移動 15 度角](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png)<br /><br /> 畫筆調整指標|
|在結束點將正切函數的長度縮短為零|按一下結束點|![在結束點將正切函數的長度縮短為零](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png)<br /><br /> 畫筆調整指標|
|將新的點加入現有路徑|按一下路徑中您要加入新點的位置|![將新的點加入現有路徑](../designers/media/b004ad5a-33a4-46ae-81c0-20be0d819332.png)<br /><br /> 畫筆插入指標|
|從路徑移除某個點|將滑鼠指標停在現有的點上並按一下|![從路徑移除點](../designers/media/08a64b78-f3df-4730-8169-c56b5631b071.png)<br /><br /> 畫筆刪除指標|
|以尖角結束路徑|按一下起點|![以尖角結束路徑](../designers/media/a12fd3b4-a553-4762-b01c-c35efa594362.png)<br /><br /> 畫筆結束指標|
|在角落以平滑曲線結束路徑|按一下起點並拖曳，以修改正切函數控點，然後鬆開滑鼠按鈕。|![在角落以平滑曲線結束路徑](../designers/media/a12fd3b4-a553-4762-b01c-c35efa594362.png)<br /><br /> 畫筆結束指標|
|結合兩個路徑時建立尖角|選取兩個路徑，按一下 [畫筆] 工具，再按一下其中一個路徑的結束點，然後按一下另一個路徑的結束點|![結合兩個路徑時建立尖角](../designers/media/bd12dfa4-112e-4f37-9765-3479e6b69894.png)<br /><br /> 畫筆結合指標|
|結合兩個路徑時建立平滑的角|選取兩個路徑，按一下 [畫筆] 工具，再按一下其中一個路徑的結束點，然後拖曳另一個路徑的結束點|![結合兩個路徑時建立平滑的角](../designers/media/bd12dfa4-112e-4f37-9765-3479e6b69894.png)<br /><br /> 畫筆結合指標|
|建立新路徑|按住 **Ctrl** 鍵，並按一下上一個路徑的外部，以停止將點新增至上一個路徑，然後按一下或拖曳您想要開始新路徑的地方|![建立新路徑](../designers/media/69758176-5f53-465b-808c-f13fd1a0b3f2.png)<br /><br /> 畫筆開始指標|

## <a name="see-also"></a>另請參閱

- [畫板輔助按鍵](artboard-modifier-keys-in-blend.md)
- [直接選取工具輔助按鍵](direct-selection-tool-modifier-keys-in-blend.md)
- [繪製圖案與路徑](draw-shapes-and-paths.md)