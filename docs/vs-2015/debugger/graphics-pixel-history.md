---
title: 圖形像素歷史記錄 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b37dab129c5eb19825746177cb30a5e20493399
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490706"
---
# <a name="graphics-pixel-history"></a>圖形像素歷史記錄
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[圖形像素歷史記錄](https://docs.microsoft.com/visualstudio/debugger/graphics/graphics-pixel-history)。  
  
Visual Studio 圖形診斷工具中的 [圖形像素歷史記錄] 視窗可幫助您了解在遊戲或應用程式的畫面格期間，Direct3D 事件對特定像素有何影響。  
  
 這是 [像素歷史記錄] 視窗：  
  
 ![包含在其歷程記錄中的三個 Direct3D 事件的像素。](../debugger/media/gfx-diag-demo-pixel-history-orientation.png "gfx_diag_demo_pixel_history_orientation")  
  
## <a name="understanding-the-pixel-history-window"></a>了解 [像素歷史記錄] 視窗  
 使用 [像素歷史記錄]，即可分析在畫面格期間，Direct3D 事件對轉譯目標的特定像素有何影響。 您可以找出特定 Direct3D 事件的呈現問題，即使後續事件 (或相同事件中的後續基本項目) 繼續變更像素的最終色彩值也一樣。 例如，像素的呈現可能不正確，然後被另一個半透明的像素遮住，導致其色彩在畫面格緩衝區中混合在一起。 如果您只有呈現目標的最後內容可以引導您，這種問題會很難診斷。  
  
 [像素歷史記錄] 視窗會顯示所選取畫面格整個過程的完整像素歷史記錄。 **最終畫面格緩衝區**在視窗頂端會顯示寫入畫面格緩衝區結尾的框架，以及其他資訊等的框架，其來自其螢幕像素的色彩座標。 這個區域也包含**呈現 Alpha**核取方塊。 選取此核取方塊時，**最終畫面格緩衝區**色彩和中繼色彩值上方都會顯示具有透明度棋盤式圖樣。 如果清除此核取方塊，則會忽略色彩值的 Alpha 色板。  
  
 視窗的下半部會顯示有機會影響像素色彩，並搭配**初始**並**最終**虛擬事件，以代表的初始和最終色彩值在 畫面格緩衝區中像素。 初始色彩值是由變更像素色彩的第一個事件 (通常是 `Clear` 事件) 決定。 像素的記錄中一定會有這兩個虛擬事件，即使沒有受到其他任何事件影響也一樣。 當其他事件有機會影響像素時，會顯示它們之間**初始**並**最終**事件。 事件可以展開，以顯示其詳細資料。 針對這種清除呈現目標的簡單事件，事件的效果只是色彩值。 像繪製呼叫這種比較複雜的事件，就會產生一或多個可能影響像素色彩的基本項目。  
  
 事件繪製的基本項目可以從其基本類型和索引，以及物件的基本項目總數來識別。 比方說，這類識別項**三角形 (1456)，共 (6214)** 基本類型對應至 1456th 的三角形 6214 個三角形組成之物件中的表示。 每個基本識別項的左邊都會有一個圖示，摘要說明該基本項目對像素的效果。 影響像素色彩的基本項目會以填滿結果色彩的圓角矩形來表示。 被排除對像素色彩有影響的基本項目，則會以指出像素被排除原因的圖示來表示。 一節會說明這些圖示[基本項目排除](../debugger/graphics-pixel-history.md#exclusion)本文稍後。  
  
 您可以展開每個基本項目來檢查像素著色器輸出如何與現有的像素色彩合併，而產生結果色彩。 從這裡您也可以檢查或偵錯與基本項目相關聯的像素著色器程式碼，而且您可以進一步展開頂點著色器節點，以檢查頂點著色器輸入。  
  
###  <a name="exclusion"></a> 基本項目排除  
 如果基本項目被排除會影響像素色彩，被排除的原因有很多。 每個原因會以下表中所描述的圖示來表示：  
  
|圖示|排除的原因|  
|----------|--------------------------|  
|![深度測試失敗圖示。](../debugger/media/vsg-hist-icon-failed-depth.png "vsg_hist_icon_failed_depth")|像素因為深度測試失敗而被排除。|  
|![剪式測試失敗圖示。](../debugger/media/vsg-hist-icon-failed-scissor.png "vsg_hist_icon_failed_scissor")|像素因為剪式測試失敗而被排除。|  
|![樣板測試失敗圖示。](../debugger/media/vsg-hist-icon-failed-stencil.png "vsg_hist_icon_failed_stencil")|像素因為樣板測試失敗而被排除。|  
  
### <a name="draw-call-exclusion"></a>繪製呼叫排除  
 如果繪製呼叫中的所有基本項目都因為測試失敗而被排除會影響呈現目標，則該繪製呼叫無法展開，而且旁邊會顯示對應至排除原因的圖示。 繪製呼叫排除的原因類似基本項目排除的原因，而且它們的圖示也很類似。  
  
### <a name="viewing-and-debugging-shader-code"></a>檢視及偵錯著色器程式碼  
 您可以檢查和偵錯頂點、輪廓、網域、幾何和像素著色器的程式碼，方法是使用與著色器相關聯之基本項目下方的控制項。  
  
##### <a name="to-view-a-shaders-source-code"></a>檢視著色器的原始程式碼  
  
1.  在 [**圖形像素歷史記錄**] 視窗中，找出之著色器對應的繪製呼叫您要檢查，並將其展開。  
  
2.  在您剛剛展開的繪製呼叫下，選取可示範您感興趣問題的基本項目，並將其展開。  
  
3.  在您感興趣的基本，遵循著色器標題連結 — 比方說，請遵循此連結**頂點著色器 obj:30**以檢視頂點著色器原始程式碼。  
  
    > [!TIP]
    >  物件編號**obj:30**，識別此著色器，在整個圖形分析器介面這類物件資料表和管線階段視窗。  
  
##### <a name="to-debug-a-shader"></a>偵錯著色器  
  
1.  在 [**圖形像素歷史記錄**] 視窗中，找出之著色器對應的繪製呼叫您要檢查，並將其展開。  
  
2.  然後，在您剛剛展開的繪製呼叫下，選取可示範您感興趣問題的基本項目，並將其展開。  
  
3.  在您感興趣的基本，選擇**開始偵錯**。 這個 HLSL 偵錯工具進入點預設為對應基本項目的第一個著色器引動過程，也就是著色器所處理的第一個像素或頂點。 只有一個與基本項目相關聯的像素，但線條和三角形有多個頂點著色器引動過程。  
  
     若要偵錯特定頂點的頂點著色器引動過程中，展開 VertexShader 標題連結，並找出您感興趣的頂點，然後選擇**開始偵錯**旁邊。  
  
### <a name="links-to-graphics-objects"></a>圖形物件連結  
 若要了解像素歷史記錄中的圖形事件，您可能需要發生事件時的裝置狀態相關資訊，或是事件參考之 Direct3D 物件的相關資訊。 中的像素歷史記錄，每個事件**圖形像素歷史記錄**提供的連結，然後目前裝置狀態和相關物件。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 遺漏的物件，因為裝置狀態](../debugger/walkthrough-missing-objects-due-to-device-state.md)   
 [逐步解說：偵錯因著色而產生的顯示錯誤](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)



