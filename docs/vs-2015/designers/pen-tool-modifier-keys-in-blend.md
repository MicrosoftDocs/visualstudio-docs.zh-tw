---
title: Blend 中的畫筆工具輔助按鍵 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c3ab14c6-a320-46db-a6b3-7fd1ca261587
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fc4f5e798e5ae675a04e7df701d08210a83062d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185019"
---
# <a name="pen-tool-modifier-keys-in-blend"></a>Blend 中的畫筆工具輔助按鍵
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

下表列出當您使用**畫筆**工具 ![](../designers/media/d514358f-185a-412f-a55d-36633b25dc8a.png "d514358f-185a-412f-a55d-36633b25dc8a") 建立路徑時，可用於修改路徑的快速鍵。 您也可以使用 [畫筆]  工具，加入或移除現有路徑上的點，或結合兩個現有路徑。  
  
|若要執行這項操作|請執行|Pointer|  
|-----------------------|-------------|-------------|  
|建立直線線段的起點|按一下以建立新的點|![](../designers/media/0bfb1b71-80ac-4ad4-aed8-40e09f8b7ab8.png "0bfb1b71-80ac-4ad4-aed8-40e09f8b7ab8")<br /><br /> 畫筆指標|  
|建立曲線線段的起點|按一下以建立新的點，然後拖曳新點以調整正切函數控點，再鬆開滑鼠按鈕。|![](../designers/media/0bfb1b71-80ac-4ad4-aed8-40e09f8b7ab8.png "0bfb1b71-80ac-4ad4-aed8-40e09f8b7ab8")<br /><br /> 畫筆指標|  
|在沒有平滑限制的情況下調整最後一個正切函數，可讓您製作出尖角。|按一下以建立新的點，然後按 ALT|![](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png "317e5475-b70c-489f-9477-110a98639ade")<br /><br /> 畫筆調整指標|  
|分割最後一個正切函數，使正切函數的結束點分別作用，讓您製作出尖角。|按一下以建立新的點，然後按住 ALT 鍵並拖曳，再鬆開滑鼠按鈕|![](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png "317e5475-b70c-489f-9477-110a98639ade")<br /><br /> 畫筆調整指標|  
|將正切函數結束點繞著新的點移動 15 度角|按一下以建立新的點，然後按住 SHIFT+ALT 鍵並拖曳，再鬆開滑鼠按鈕|![](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png "317e5475-b70c-489f-9477-110a98639ade")<br /><br /> 畫筆調整指標|  
|在結束點將正切函數的長度縮短為零|按一下結束點|![](../designers/media/317e5475-b70c-489f-9477-110a98639ade.png "317e5475-b70c-489f-9477-110a98639ade")<br /><br /> 畫筆調整指標|  
|將新的點加入現有路徑|按一下路徑中您要加入新點的位置|![](../designers/media/b004ad5a-33a4-46ae-81c0-20be0d819332.png "b004ad5a-33a4-46ae-81c0-20be0d819332")<br /><br /> 畫筆插入指標|  
|從路徑移除某個點|將滑鼠指標停在現有的點上並按一下|![](../designers/media/08a64b78-f3df-4730-8169-c56b5631b071.png "08a64b78-f3df-4730-8169-c56b5631b071")<br /><br /> 畫筆刪除指標|  
|以尖角結束路徑|按一下起點|![](../designers/media/a12fd3b4-a553-4762-b01c-c35efa594362.png "a12fd3b4-a553-4762-b01c-c35efa594362")<br /><br /> 畫筆結束指標|  
|在角落以平滑曲線結束路徑|按一下起點並拖曳，以修改正切函數控點，然後鬆開滑鼠按鈕。|![](../designers/media/a12fd3b4-a553-4762-b01c-c35efa594362.png "a12fd3b4-a553-4762-b01c-c35efa594362")<br /><br /> 畫筆結束指標|  
|結合兩個路徑時建立尖角|選取兩個路徑，按一下 [畫筆]  工具，再按一下其中一個路徑的結束點，然後按一下另一個路徑的結束點|![](../designers/media/bd12dfa4-112e-4f37-9765-3479e6b69894.png "bd12dfa4-112e-4f37-9765-3479e6b69894")<br /><br /> 畫筆結合指標|  
|結合兩個路徑時建立平滑的角|選取兩個路徑，按一下 [畫筆]  工具，再按一下其中一個路徑的結束點，然後拖曳另一個路徑的結束點|![](../designers/media/bd12dfa4-112e-4f37-9765-3479e6b69894.png "bd12dfa4-112e-4f37-9765-3479e6b69894")<br /><br /> 畫筆結合指標|  
|建立新路徑|按住 CTRL 鍵，並按一下上一個路徑的外部，以停止將點加入上一個路徑，然後按一下或拖曳您想要開始新路徑的地方|![](../designers/media/69758176-5f53-465b-808c-f13fd1a0b3f2.png "69758176-5f53-465b-808c-f13fd1a0b3f2")<br /><br /> 畫筆開始指標|  
  
## <a name="see-also"></a>另請參閱  
 [鍵盤快速鍵和輔助按鍵](../designers/keyboard-shortcuts-and-modifier-keys-in-blend.md)   
 [畫板輔助按鍵](../designers/artboard-modifier-keys-in-blend.md)   
 [直接選取工具輔助按鍵](../designers/direct-selection-tool-modifier-keys-in-blend.md)   
 [繪製圖案與路徑](../designers/draw-shapes-and-paths.md)
