---
title: 在 XAML 設計工具中製作物件動畫
titleSuffix: Blend for Visual Studio
description: 瞭解如何在 Blend for Visual Studio 中建立動畫，方法是使用包含時間軸和主要畫面格的分鏡腳本，以動畫顯示 XAML 設計工具中的物件。
ms.custom: SEO-VS-2020
ms.date: 07/31/2019
ms.topic: how-to
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 162ed3ddb7e8f71a14c9dd8415500cc845316e82
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889248"
---
# <a name="animate-objects-in-xaml-designer"></a>在 XAML 設計工具中製作物件動畫

Blend for Visual Studio 可讓您輕鬆建立簡短的動畫，例如移動物件或讓物件淡入和淡出。

若要建立動畫，您需要一個「分鏡腳本」。 分鏡腳本包含一個或多個 *「時間軸」*(timeline)。 設定時間軸上的 *「主要畫面格」* (keyframe) 以標示屬性變更。 然後，當您執行動畫時，Blend for Visual Studio 就會在指定的時段期間插入屬性變更。 結果是平順地轉場。 您可以製作物件所屬任何屬性的動畫，包括非視覺屬性。

下列影像顯示一個名為 **Storyboard1** 的分鏡腳本。 時間軸包含標示矩形 X 和 Y 位置的主要畫面格。 在這個動畫執行時，矩形會從一個位置順暢移動至另一個位置。

![Blend for Visual Studio 中動畫的分鏡腳本](media/storyboard-timeline.png)

## <a name="create-an-animation"></a>建立動畫

1. 若要建立分鏡腳本，請選取 [物件與時間軸] 視窗中的 [分鏡腳本選項]，然後選取 [新增]。

   ![在 Blend for Visual Studio 中新增分鏡腳本](media/new-storyboard.png)

2. 在 [建立分鏡腳本資源]  對話方塊中，輸入分鏡腳本的名稱。

3. 從 [設計] 檢視中的 [資產] 面板，將矩形新增至頁面的左下方。

   ![「XAML 設計工具」之 [資產] 面板中的矩形](media/add-rectangle.PNG)

4. 在 [物件與時間軸] 視窗中，將黃色時間指標移至 [3] 秒。

   ![時間軸中的時間指標](media/timeline-indicator.PNG)

5. 在頁面的 [設計] 檢視中，將矩形拖曳到頁面的右側。

6. 按 [播放] 以觀看矩形從頁面的左側移到右側。

在不同的時間點對矩形進行其他變更。 例如，您可以在 [屬性] 視窗中變更填滿色彩或翻轉方向。

## <a name="see-also"></a>另請參閱

- [使用 Blend for Visual Studio 建立 UI](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
