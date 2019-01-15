---
title: 在 XAML 設計工具中插入控制項並修改其行為
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: c50e0dd1884a588c95cd4baa4c544d67a85989b8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911477"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>在 XAML 設計工具中插入控制項並修改其行為

控制項可讓使用者與應用程式互動。 您可以使用控制項來收集資訊並執行動作，例如製作物件動畫，或查詢資料來源。

## <a name="add-controls-to-the-artboard"></a>將控制項加入至畫板

您可以從 [資產]  面板中將控制項拖曳至 [畫板] 上，然後在 [屬性]  視窗中加以修改。

![Blend [資產] 索引標籤控制項](../designers/media/blend_assetsflipview_xaml.png)

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>讓控制項出現在影像、圖形或路徑上

您可以將任何物件加入至控制項。

![Blend [變成控制項] 對話方塊](../designers/media/blend_makeintocontrol_xaml.png)

例如，想像一下頁面中心有一個電視圖片。 您可以讓控制項出現在小型影像上，使其看起來像電視按鈕。 然後，使用者便可以按一下這些按鈕來變更頻道。

這可能是因為按鈕現在是控制項的關係。 有了控制項，您就可以在使用者按一下按鈕時回應使用者互動。

若要製作控制項，請選取某個物件。 然後在 [工具]  功能表上按一下 [製作控制項] 。

## <a name="make-controls-do-things"></a>讓控制項執行動作

當使用者與控制項互動時，控制項可以執行動作。 例如，他們可以啟動動畫、更新資料來源或播放影片。

使用 *「觸發程序」*(trigger)、 *「行為」*(behavior) 及 *「事件」* (event)，讓控制項執行動作。

### <a name="triggers"></a>「觸發程序」

*「觸發程序」* (trigger)會變更屬性或執行工作以回應事件或另一個屬性的變更。 例如，在使用者將滑鼠停留在按鈕上時可變更按鈕的色彩。

![觸發程序面板](../designers/media/custom_button_blend_propertytriggerinfo.png)

### <a name="behaviors"></a>「行為」

*「行為」* (behavior) 是可重複使用的程式碼封裝。 它能做的不僅僅是變更屬性， 還能執行像是查詢資料服務等動作。 Blend 隨附一小組的行為，但是您可以新增更多功能。 將行為拖曳至畫板中的任何物件上，然後設定屬性以自訂行為。

![[屬性] 面板中的 FluidMoveBehavior](../designers/media/b4_fluidmovebehaviorproperties_sample.png)

**觀看影片：**![播放圖示](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Blend tips:Intro to using behaviors Part 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904) (Blend 祕訣：使用行為簡介第 1 部分)。

### <a name="events"></a>事件

如需最大的彈性，請處理 *「事件」*(event)。 您將必須撰寫一些程式碼。