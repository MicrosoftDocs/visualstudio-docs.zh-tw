---
title: 篩選節點 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2789676505588c2041abfd876a228fc456ee3607
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487779"
---
# <a name="filter-nodes"></a>篩選節點
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[篩選節點](https://docs.microsoft.com/visualstudio/designers/filter-nodes)。  
  
在著色器設計工具中，篩選節點會將色彩或材質範例等輸入轉換為象徵性的色彩值。 這些象徵性的色彩值通常會在進行非相片品質的轉譯時使用，或當成其他視覺效果中的元件使用。  
  
## <a name="filter-node-reference"></a>篩選節點參考  
  
|節點|詳細資料|屬性|  
|----------|-------------|----------------|  
|**模糊**|使用高斯函數，使材質中的像素變得模糊。<br /><br /> 您可以用此來減少材質中的色彩詳細資料或雜訊。<br /><br /> **輸入：**<br /><br /> `UV`: `float2`<br /> 要測試的材質座標。<br /><br /> **輸出：**<br /><br /> `Output`: `float4`<br /> 模糊效果的色彩值。|**材質**<br /> 與模糊期間使用之取樣器產生關聯的材質暫存器。|  
|**反滲透**|減少指定色彩中的色彩量。<br /><br /> 當移除色彩時，色彩值會相當接近灰階。<br /><br /> **輸入：**<br /><br /> `RGB`: `float3`<br /> 要去色的色彩。<br /><br /> `Percent`: `float`<br /> 若要移除的色彩百分比，以 [0, 1] 範圍內的標準化數值表示。<br /><br /> **輸出：**<br /><br /> `Output`: `float3`<br /> 已去色的色彩。|**明亮度**<br /> 提供給紅色、綠色和藍色色彩元件的加權。|  
|**邊緣偵測**|使用 Canny 邊緣偵測器偵測到材質中的邊緣。 邊緣像素會輸出為白色，而非邊緣像素會輸出為黑色。<br /><br /> 您可以用這個來識別材質中的邊緣，以便使用其他效果來處理邊緣像素。<br /><br /> **輸入：**<br /><br /> `UV`: `float2`<br /> 要測試的材質座標。<br /><br /> **輸出：**<br /><br /> `Output`: `float4`<br /> 如果材質位在邊緣，為白色，否則為黑色。|**材質**<br /> 與邊緣偵測期間所用之取樣器產生關聯的材質暫存器。|  
|**銳利化**|將材質銳利化。<br /><br /> 您可以用此來強調材質中的詳細資料。<br /><br /> **輸入：**<br /><br /> `UV`: `float2`<br /> 要測試的材質座標。<br /><br /> **輸出：**<br /><br /> `Output`: `float4`<br /> 模糊效果的色彩值。|**材質**<br /> 與銳利化期間使用之取樣器產生關聯的材質暫存器。|



