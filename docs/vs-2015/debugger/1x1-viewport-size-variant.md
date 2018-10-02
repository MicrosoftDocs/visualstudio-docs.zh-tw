---
title: 1x1 Viewport 大小變異 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c0052a2d59dbcef1d7ea32eab789ab955750f3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500519"
---
# <a name="1x1-viewport-size-variant"></a>1x1 Viewport 大小變異
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[1x1 檢視區大小變異](https://docs.microsoft.com/visualstudio/debugger/graphics/1x1-viewport-size-variant)。  
  
將所有呈現目標上的檢視區維度減少為 1x1 個像素。  
  
## <a name="interpretation"></a>解譯  
 較小的檢視區會減少必須著色的像素數目，但是不會減少必須處理的端點數目。 將檢視區維度設定為 1x1 個像素，可有效地去除您應用程式中的像素陰影。  
  
 如果此變異顯示大量的效能提高，則可能表示您的應用程式耗用太多填充率。 這可能表示您為目標平台選擇的解析度太高，或者您的應用程式花費大量時間為稍後要覆寫 (過度繪製) 的像素加上陰影。 此結果表示減少畫面格緩衝區的大小，或減少過度繪製量將可改善您應用程式的效能。  
  
## <a name="remarks"></a>備註  
 每次呼叫 `ID3D11DeviceContext::OMSetRenderTargets` 或 `ID3D11DeviceContext::RSSetViewports` 之後，都會將檢視區維度重設為 1x1 個像素。  
  
## <a name="example"></a>範例  
 使用與下列類似的程式碼，即可重現此變異：  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```



