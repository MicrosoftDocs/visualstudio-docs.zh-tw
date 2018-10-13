---
title: 公用程式節點 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff732221-b731-424c-ad5b-82ef5f21dff5
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d85735c5fb355163f2003a27a96675ed097d66e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174417"
---
# <a name="utility-nodes"></a>公用程式節點
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在著色器設計工具中，公用程式節點代表常見且實用，卻不完全適合其他類別的著色器計算。 有些公用程式節點執行簡單的作業，例如將向量附加在一起，或有條件地選擇結果，還有其他執行複雜作業的節點，例如根據常用的光源模型計算光源比重。  
  
## <a name="utility-node-reference"></a>公用程式節點參考  
  
|節點|詳細資料|屬性|  
|----------|-------------|----------------|  
|**附加向量**|將指定的輸入附加在一起，建立一個向量。<br /><br /> **輸入：**<br /><br /> `Vector`：`float`、`float2` 或 `float3`<br /> 要附加到的值。<br /><br /> `Value to Append`: `float`<br /> 要附加的值。<br /><br /> **輸出：**<br /><br /> `Output`：`float2`、`float3` 或 `float4`，取決於輸入類型 `Vector`<br /> 新的向量。|無|  
|**菲涅耳**|使用指定的曲面法線入計算菲涅耳降低值。<br /><br /> 菲涅耳降低值表示目前像素的曲面法線與檢視向量有多一致。 當向量對齊時，函式的結果為 0; 結果會因為向量變得較不類似而增加，並在向量成直角時達到其最大值。 您可以根據目前像素方向與觀景窗之間的關聯性，使用這個對外表進行或多或少的效果。<br /><br /> **輸入：**<br /><br /> `Surface Normal`: `float3`<br /> 目前像素的曲面法線，定義於目前像素的正切函數空間。 如同在法線對應中一樣，您可以用此來擾亂明顯的曲面法線。<br /><br /> **輸出：**<br /><br /> `Output`: `float`<br /> 目前像素的反射率。|**指數**<br /> 用來計算菲涅耳降低值的指數。|  
|**If**|每個元件都有條件地選擇三個可能結果之一。 條件是由其他兩個指定輸入之間的關聯性來定義。<br /><br /> 對於結果的每個元件，會根據前兩個輸入的對應元件之間的關聯性，選擇三個可能結果之一的對應元件。<br /><br /> **輸入：**<br /><br /> `X`：`float`、`float2`、`float3` 或 `float4`<br /> 要比較的左邊值。<br /><br /> `Y`：和輸入 `X` 的類型相同<br /> 要比較的右邊值。<br /><br /> `X > Y`：和輸入 `X` 的類型相同<br /> 當 `X` 大於 `Y` 時要選擇的值。<br /><br /> `X = Y`：和輸入 `X` 的類型相同<br /> 當 `X` 等於 `Y` 時要選擇的值。<br /><br /> `X < Y`：和輸入 `X` 的類型相同<br /> 當 `X` 小於 `Y` 時要選擇的值。<br /><br /> **輸出：**<br /><br /> `Output`: `float3`<br /> 根據元件選擇的結果。|無|  
|**Lambert**|使用指定的曲面法線，根據 Lambert 光源模型計算目前像素的色彩。<br /><br /> 色彩是直接光源之下，環境色彩和擴散光源比重的總和。 環境色彩接近間接光源的總計比重，但看起來單調又晦暗，而且沒有其他光源的協助。 擴散光源有助於將圖案和深度加入物件。<br /><br /> **輸入：**<br /><br /> `Surface Normal`: `float3`<br /> 目前像素的曲面法線，定義於目前像素的正切函數空間。 如同在法線對應中一樣，您可以用此來擾亂明顯的曲面法線。<br /><br /> `Diffuse Color`: `float3`<br /> 目前像素的擴散色彩，通常是「點色彩」。 如果未提供任何輸入，則預設值是白色。<br /><br /> **輸出：**<br /><br /> `Output`: `float3`<br /> 目前像素的擴散色彩。|無|  
|**遮罩向量**|為指定向量的元件加上遮罩。<br /><br /> 您可以使用這個從色彩值中移除特定的色彩頻道，或者使特定元件不在後續計算中發揮作用。<br /><br /> **輸入：**<br /><br /> `Vector`: `float4`<br /> 要加上遮罩的向量。<br /><br /> **輸出：**<br /><br /> `Output`: `float4`<br /> 遮罩的向量。|**紅色 / X**<br /> **False** 表示遮住紅色 (x) 元件，否則為 **True**。<br /><br /> **綠色 / Y**<br /> **False** 表示遮住綠色 (y) 元件，否則為 **True**。<br /><br /> **藍色 / Z**<br /> **False** 表示遮住藍色 (z) 元件，否則為 **True**。<br /><br /> **Alpha / W**<br /> **False** 表示遮住 Alpha (w) 元件，否則為 **True**。|  
|**反射向量**|根據觀景窗位置計算正切空間中目前像素的反射向量。<br /><br /> 您可以用這個來計算反射、立方體貼圖座標和反射光源比重<br /><br /> **輸入：**<br /><br /> `Tangent Space Surface Normal`: `float3`<br /> 目前像素的曲面法線，定義於目前像素的正切函數空間。 如同在法線對應中一樣，您可以用此來擾亂明顯的曲面法線。<br /><br /> **輸出：**<br /><br /> `Output`: `float3`<br /> 反射向量。|無|  
|**反射**|使用指定的曲面法線，根據 Phong 光源模型計算反射光源比重。<br /><br /> 反射光源可為水、塑膠或金屬等物件提供閃亮、反光的外觀。<br /><br /> **輸入：**<br /><br /> `Surface Normal`: `float3`<br /> 目前像素的曲面法線，定義於目前像素的正切函數空間。 如同在法線對應中一樣，您可以用此來擾亂明顯的曲面法線。<br /><br /> **輸出：**<br /><br /> `Output`: `float3`<br /> 反射亮部的色彩比重。|無|



