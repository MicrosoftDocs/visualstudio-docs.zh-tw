---
title: 1x1 的區大小變異 |Microsoft Docs
description: 套用1x1 的區大小變異，以將所有呈現目標上的視口維度縮減為1x1 圖元。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dc96decdc8e61e1d8c1f5b60195d7644222dbd51
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874596"
---
# <a name="1x1-viewport-size-variant"></a>1x1 Viewport 大小變異
將所有呈現目標上的檢視區維度減少為 1x1 個像素。

## <a name="interpretation"></a>解讀
 較小的視口可減少您必須加上網底的圖元數。 但較小的區不會減少您必須處理的頂點數目。 將檢視區維度設定為 1x1 個像素，可有效地去除您應用程式中的像素陰影。

 如果此變異顯示大量的效能提升，可能表示您的應用程式耗用太多填滿率。 此外，您的解析度對目標平臺而言可能太高，或您的應用程式可能會花很長的時間陰影圖元（稍後會予以覆寫），也就是 *過度繪製*。 較小的框架緩衝區或減少過度繪製數量，將可改善應用程式的效能。

## <a name="remarks"></a>備註
 每次呼叫 `ID3D11DeviceContext::OMSetRenderTargets` 或 `ID3D11DeviceContext::RSSetViewports` 之後，都會將檢視區維度重設為 1x1 個像素。

## <a name="example"></a>範例
 您可以使用下列程式碼重現此變異：

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
