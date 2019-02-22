---
title: 1x1 Viewport 大小變異 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ee3d083e7956cf2bd1eff1f09769ef6ec85c979
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983634"
---
# <a name="1x1-viewport-size-variant"></a>1x1 Viewport 大小變異
將所有呈現目標上的檢視區維度減少為 1x1 個像素。  
  
## <a name="interpretation"></a>解譯  
 較小的檢視區會減少您不必深淺程度不同的像素數目。 但是，您也可以在較小的檢視區不會減少您需要的頂點數目程序。 將檢視區維度設定為 1x1 個像素，可有效地去除您應用程式中的像素陰影。  
  
 如果此變異顯示大量的效能提高，則可能表示您的應用程式耗用太多的填滿率。 此外，您的解析度可能太高的目標平台，或您的應用程式可能花很長的時間陰影像素為單位，稍後會覆寫，也稱為*過度*。 較小的畫面格緩衝區或減少過度繪製量將可改善您的應用程式效能。  
  
## <a name="remarks"></a>備註  
 每次呼叫 `ID3D11DeviceContext::OMSetRenderTargets` 或 `ID3D11DeviceContext::RSSetViewports` 之後，都會將檢視區維度重設為 1x1 個像素。  
  
## <a name="example"></a>範例  
 下列程式碼，即可重現此變異：  
  
```cpp
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```
