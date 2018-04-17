---
title: 在 XAML 設計工具中插入控制項並修改其行為 | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: article
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- uwp
ms.openlocfilehash: 828b02daaed0b33bfa2f53cf16bee9b60be2f939
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>在 XAML 設計工具中插入控制項並修改其行為

控制項可讓使用者與應用程式互動。 您可以使用控制項來收集資訊並執行動作，例如製作物件動畫，或查詢資料來源。

## <a name="add-controls-to-the-artboard"></a>將控制項加入至畫板

您可以從 [資產]  面板中將控制項拖曳至 [畫板] 上，然後在 [屬性]  視窗中加以修改。

![Blend &#45; 資產 &#45; FlipView](../designers/media/blend_assetsflipview_xaml.png "blend_AssetsFlipView_XAML")

這些影片將示範如何使用一些較常見的控制項。

|控制項|觀看短片|
|-------------|-------------------------|
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png)|![播放圖示](../designers/media/bldadminconsoleinitialconfigicon.PNG) [新增控制項](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png)|![播放圖示](../designers/media/bldadminconsoleinitialconfigicon.PNG) [設計按鈕](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png)|![播放圖示](../designers/media/bldadminconsoleinitialconfigicon.PNG) [將影像新增至 TextBlock](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png)|![播放圖示](../designers/media/bldadminconsoleinitialconfigicon.PNG) [使用工具提示建置滑桿](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>讓控制項出現在影像、圖形或路徑上

 您可以將任何物件加入至控制項。

 ![Blend [Make Into Control] (變成控制項) 對話方塊](../designers/media/blend_makeintocontrol_xaml.png "blend_MakeIntoControl_XAML")

 例如，想像一下頁面中心有一個電視圖片。 您可以讓控制項出現在小型影像上，使其看起來像電視按鈕。 然後，使用者便可以按一下這些按鈕來變更頻道。

 這可能是因為按鈕現在是控制項的關係。 有了控制項，您就可以在使用者按一下按鈕時回應使用者互動。

 若要製作控制項，請選取某個物件。 然後在 [工具]  功能表上按一下 [製作控制項] 。

## <a name="make-controls-do-things"></a>讓控制項執行動作

 當使用者與控制項互動時，控制項可以執行動作。 例如，他們可以啟動動畫、更新資料來源或播放視訊。

 使用 *「觸發程序」*(trigger)、 *「行為」*(behavior) 及 *「事件」* (event)，讓控制項執行動作。

### <a name="triggers"></a>「觸發程序」

 *「觸發程序」* (trigger)會變更屬性或執行工作以回應事件或另一個屬性的變更。 例如，在使用者將滑鼠停留在按鈕上時可變更按鈕的色彩。

 ![「觸發程序」面板](../designers/media/custom_button_blend_propertytriggerinfo.png)

 **觀看短片︰**![播放圖示](../designers/media/bldadminconsoleinitialconfigicon.PNG) [新增屬性觸發程序](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger)。

### <a name="behaviors"></a>「行為」

 *「行為」* (behavior) 是可重複使用的程式碼封裝。 它能做的不僅僅是變更屬性， 還能執行像是查詢資料服務等動作。 Blend 隨附一小組的以上功能，但是您可以加入更多功能。 將行為拖曳至畫板中的任何物件上，然後設定屬性以自訂行為。

 ![[屬性] 面板中的 FluidMoveBehavior](../designers/media/b4_fluidmovebehaviorproperties_sample.png)

 **觀看短片︰**![播放圖示](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Blend 祕訣︰使用行為簡介第 1 部分](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904)。

### <a name="events"></a>事件

 如需最大的彈性，請處理 *「事件」*(event)。 您將必須撰寫一些程式碼。

 **觀看短片︰**![播放圖示](../designers/media/bldadminconsoleinitialconfigicon.PNG) [新增滑鼠事件](https://www.youtube.com/watch?v=2PMxAlb-x_E)。