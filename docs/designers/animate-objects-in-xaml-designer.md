---
title: 在 XAML 設計工具中製作物件動畫
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: f6fbeceeb0c9943e561c5bd4e353551005be23a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960200"
---
# <a name="animate-objects-in-xaml-designer"></a>在 XAML 設計工具中製作物件動畫

您可以建立可移動物件或讓物件淡入和淡出的簡短動畫。

若要開始使用，請建立 *「分鏡腳本」*(storyboard)。 分鏡腳本包含一個或多個 *「時間軸」*(timeline)。 設定時間軸上的 *「主要畫面格」* (keyframe) 以標示屬性變更。 然後在執行動畫時，Blend 會在指定時段上插補屬性變更。 結果是平順地轉場。 您可以製作物件所屬任何屬性的動畫，包括非視覺屬性。

下列圖例顯示名為 [上移] 的分鏡腳本。 時間軸包含標示矩形 X 和 Y 位置的主要畫面格。 在這個動畫執行時，矩形會從一個位置順暢移動至另一個位置。

![在 XAML 設計工具中上移分鏡腳本](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png)

## <a name="see-also"></a>另請參閱

- [使用 Blend for Visual Studio 建立 UI](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)