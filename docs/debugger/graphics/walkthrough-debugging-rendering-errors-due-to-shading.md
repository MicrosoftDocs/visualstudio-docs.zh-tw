---
title: 逐步解說：由於陰影而偵測轉譯錯誤 |Microsoft Docs
description: 遵循尋找著色器 bug 的調查。 它會顯示使用 Visual Studio 圖形診斷，包括圖形圖元歷程記錄和 HLSL 偵錯工具。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 491a2c5ab0bcb923d9999bd55249150d33a650ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891861"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>逐步解說：對因著色而產生的顯示錯誤進行偵錯
本逐步解說示範如何使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 圖形診斷來調查因為著色器錯誤而不正確著色的物件。

 本逐步解說示範如何：

- 檢查圖形記錄文件來識別顯示問題的像素。

- 使用 [圖形像素歷史記錄]  視窗更仔細地檢查像素狀態。

- 使用 [HLSL 偵錯工具]  來檢查像素和端點著色器。

## <a name="scenario"></a>狀況
 物件著色不正確通常是因為端點著色器將不正確或不完整的資訊傳遞給像素著色器。

 在此案例中，您最近將物件新增至您的應用程式。 您也加入了新的頂點和圖元著色器，以轉換物件並為其提供獨特的外觀。 但在測試期間執行應用程式時，該物件卻呈現為純黑色。 透過使用圖形診斷，您可擷取圖形記錄問題，以偵錯應用程式。 此問題在應用程式中看起來像這樣的影像：

 ![此物件是以不正確的色彩來呈現。](media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")

## <a name="investigation"></a>調查
 透過使用圖形診斷工具，您可以載入圖形記錄文件，以檢查測試期間所擷取的畫面格。

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>檢查圖形記錄中的畫面格

1. 在中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，載入圖形記錄檔，其框架會顯示遺漏的模型。 新的 [圖形記錄檔] 視窗隨即出現在中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 此視窗的上半部是所選取畫面格的轉譯目標輸出。 下半部是 [畫面格清單] ，其以縮圖顯示每個擷取的畫面格。

2. 在 [ **畫面格清單**] 中，選取物件沒有正確外觀的畫面格。 轉譯目標會更新以反映選取的畫面格。 在此案例中，圖形記錄檔視窗看起來像這樣的影像：

    ![Visual Studio 中的圖形記錄文件。](media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")

   選取示範問題的畫面格之後，即可使用 [圖形像素歷史記錄]  視窗進行診斷。 [圖形像素歷史記錄]  視窗會依時間先後順序顯示可能影響特定像素及其著色器的基本圖形，以及這些基本圖形對轉譯目標的影響。

#### <a name="to-examine-a-pixel"></a>檢查像素

1. 開啟 [圖形像素歷史記錄]  視窗。 在 [圖形診斷]  工具列上，選擇 [像素歷史記錄] 。

2. 選取要檢查的像素。 在圖形記錄文件視窗中，從著色不正確的物件選取其中一個像素：

    ![選取像素時會顯示關於其歷史記錄的資訊。](media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")

    [圖形像素歷史記錄]  視窗隨即更新，以反映選取的像素。 在此情節中，[圖形像素歷史記錄]  視窗如下所示：

    ![像素歷史記錄顯示一個 DrawIndexed 事件。](media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")

    請注意，圖元著色器的結果是完全不透明的黑色 (0、0、0、1) ，而且 **輸出合併** 會將這個圖元著色器與 **先前** 的圖元色彩結合， **因此結果** 也是完全不透明的黑色。

   在您檢查著色不正確的像素，而發現像素著色器輸出不是所需的色彩之後，您可以使用 HLSL 偵錯工具來檢查像素著色器，並查明物件的色彩發生什麼狀況。 您可以使用 HLSL 偵錯工具在執行時檢查 HLSL 變數狀態、逐步執行 HLSL 程式碼，以及設定能協助您診斷問題的中斷點。

#### <a name="to-examine-the-pixel-shader"></a>檢查像素著色器

1. 開始偵錯像素著色器。 在 [圖形像素歷史記錄]  視窗中，於物件基本圖形下方的 [像素著色器] 旁，選擇 [開始偵錯]  按鈕。

2. 在此情節中，由於像素著色器才從端點著色器傳遞色彩，因此很容易觀察到像素著色器不是問題的來源。

3. 將指標放在 `input.color`上。 請注意，其值是完全不透明的黑色 (0, 0, 0, 1)。

    !["input" 的 "color" 成員是黑色。](media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")

    在此情節中，根據檢查結果所示，色彩不正確可能是因為端點著色器並未向像素著色器的作業提供正確的色彩資訊所致。

   在您判斷端點著色器可能未提供正確資訊給像素著色器之後，下一個步驟就是檢查端點著色器。

#### <a name="to-examine-the-vertex-shader"></a>檢查端點著色器

1. 開始偵錯端點著色器。 在 [圖形像素歷史記錄]  視窗中，於物件基本圖形下方的 [端點著色器] 旁，選擇 [開始偵錯]  按鈕。

2. 找出端點著色器的輸出結構，這是像素著色器的輸入。 在此情節中，此結構的名稱是 `output`。 檢查端點著色器程式碼並發現 `color` 結構的 `output` 成員已明確設定為完全不透明的黑色，這可能是因為某人的偵錯工作所造成。

3. 確認絕不會從輸入結構複製 color 成員。 由於在傳回 `output` 結構之前，`output.color` 的值已設定為完全不透明的黑色，因此建議您確定 `output` 的值在上一行未正確初始化。 查看 `output.color` 的值時，逐步執行端點著色器程式碼，直到您到達將 `output.color`設定為黑色的程式碼行。 請注意， `output.color` 的值在設定為黑色之前尚未初始化。 這會確認應修改將 `output.color` 設定為黑色的程式碼行，而不是予以刪除。

    !["output.color" 的值是黑色。](media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")

   在您判斷轉譯問題的原因是端點著色器未提供正確色彩值給像素著色器之後，您可以使用這項資訊來修正問題。 在此情節中，若要修正問題，請變更端點著色器中的下列程式碼

```hlsl
output.color = float3(0.0f, 0.0f, 0.0f);
```

 to

```hlsl
output.color = input.color;
```

 此程式碼才從物件的頂點傳遞未修改的端點色彩，更複雜的端點著色器可以在傳遞前修改色彩。 修正過的端點著色器程式碼應該會與以下相似：

 ![修正過的端點著色器程式碼。](media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")

 修正程式碼之後，請重新建置並再次執行應用程式，以確認轉譯問題已解決。

 ![此物件是以正確的色彩來呈現。](media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")
