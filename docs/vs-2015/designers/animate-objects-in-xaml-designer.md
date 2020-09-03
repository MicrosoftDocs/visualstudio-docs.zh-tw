---
title: 在 XAML 設計工具中製作物件動畫 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ea2fdf1f47385a9be26fa65a93b9104b2d864079
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658015"
---
# <a name="animate-objects-in-xaml-designer"></a>在 XAML 設計工具中製作物件動畫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以建立可移動物件或讓物件淡入和淡出的簡短動畫。

 若要開始使用，請建立 *「分鏡腳本」*(storyboard)。 分鏡腳本包含一個或多個 *「時間軸」*(timeline)。 設定時間軸上的 *「主要畫面格」* (keyframe) 以標示屬性變更。 然後在執行動畫時，Blend 會在指定時段上插補屬性變更。 結果是平順地轉場。 您可以製作物件所屬任何屬性的動畫，包括非視覺屬性。

 下列圖例顯示名為 [上移] **** 的分鏡腳本。 時間軸包含標示矩形 X 和 Y 位置的主要畫面格。 在這個動畫執行時，矩形會從一個位置順暢移動至另一個位置。

 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")

 觀賞這些影片，了解如何建立動畫。

|觀看短片：|了解如何：|
|--------------------------|-------------------|
|![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG ">bldadminconsoleinitialconfigicon")[建立時程表](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|建立時間軸，並使用時間軸中的物件。|
|![設定已安裝的功能新增主要](../designers/media/bldadminconsoleinitialconfigicon.PNG ">bldadminconsoleinitialconfigicon")畫面格 [並重複動畫](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|加入主要畫面格，並設定每個主要畫面格的屬性。 然後，執行動畫並觀賞物件在動畫之間順暢地轉場。|
|![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG ">bldadminconsoleinitialconfigicon")[新增互動的事件觸發程式](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|在發生事件時啟動動畫。 例如，載入視窗時啟動動畫。|
|![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG ">bldadminconsoleinitialconfigicon")[動畫色彩](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|使用動畫來變更物件的色彩。|
|![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG ">bldadminconsoleinitialconfigicon")[建立和修改移動路徑](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|沿著路徑製作物件動畫。|
|![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG ">bldadminconsoleinitialconfigicon")[簡化](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)主要畫面格|讓即將開始 (*「加速」*(easing in) 或即將結束 (*「減速」*(easing out) 的動畫加速或變慢。|
|![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG ">bldadminconsoleinitialconfigicon")[動畫按鈕](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|建立在使用者指向按鈕時會出現在上面的有趣效果。|
|![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.PNG ">bldadminconsoleinitialconfigicon")[建立動畫並使用緩時](https://www.youtube.com/watch?v=mAJXYrwxGYo)|製作會在使用者按下計算機影像的按鈕時出現的動畫效果。|

## <a name="see-also"></a>另請參閱
 [使用 Blend for Visual Studio 建立 UI](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
