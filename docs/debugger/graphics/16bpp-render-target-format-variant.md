---
title: 16bpp 呈現目標格式變異 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94775b717a3095d54d3fa52e3d2a5325dc3d21c5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075788"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bpp 轉譯目標格式變異
將所有呈現目標和背景緩衝區的像素格式設定為 DXGI_FORMAT_B5G6R5_UNORM。

## <a name="interpretation"></a>解譯
 呈現目標或背景緩衝區通常會使用 32 bpp （每像素 32 位元） 的格式，例如 B8G8R8A8_UNORM。 32 bpp 格式可能會耗用大量的記憶體頻寬。 因為 B5G6R5_UNORM 格式是 32 bpp 格式一半的大小以 16 bpp 格式，則使用它可以讓壓力的記憶體頻寬，但會降低的色彩逼真度。

 如果此變異顯示大量的效能提高，則可能表示您的應用程式耗用太多記憶體頻寬。 就能大幅提升效能，尤其是當分析的畫面格有大量過度繪製或 alpha 透明混色。

16-bpp 呈現目標格式可以減少記憶體使用量的頻外，當您的應用程式具有下列條件：
- 不需要高逼真度色彩。
- 不需要 alpha 色頻。
- Ofent 沒有平滑漸層 （也就是容易色彩逼真度降低條紋成品）。

其他策略來減少記憶體頻寬包括：
- 減少過度繪製或 alpha 透明混色數量。
- 減少畫面格緩衝區的維度。
- 減少紋理資源的維度。
- 降低的紋理資源的壓縮。

像往常一樣，您需要考慮所有這些最佳化伴隨的影像品質取捨。

屬於交換鏈結的應用程式將不支援 16 bpp 背景緩衝區格式 (DXGI_FORMAT_B5G6R5_UNORM)。 使用建立這些交換鏈結`D3D11CreateDeviceAndSwapChain`或`IDXGIFactory::CreateSwapChain`。 若要解決這項限制，請執行下列步驟：
1. 使用建立 B5G6R5_UNORM 格式呈現目標`CreateTexture2D`並轉譯為目標。
2. 複製到交換鏈結四分之一轉譯目標繪製使用呈現目標做為來源紋理的全螢幕四組數字。
3. 交換鏈結上呼叫 Present。

   如果這項策略可儲存更多的頻寬，非供將呈現目標複製到交換鏈結的四分之一，會改善呈現效能。

   使用並排的呈現技術的 GPU 架構可以使用 16 bpp 畫面格緩衝區格式，以查看效能優勢明顯。 這項改進是因為較大部份的畫面格緩衝區可容納每個並排的本機畫面格緩衝區快取中。 並排的呈現架構有時出現在行動電話話筒和平板電腦的 GPU 中；它們很少出現在此範圍之外。

## <a name="remarks"></a>備註
 每次呼叫可建立呈現目標的 `ID3D11Device::CreateTexture2D` 時，都會將呈現目標格式重設為 DXGI_FORMAT_B5G6R5_UNORM。 特別是 pDesc 中所傳遞的 D3D11_TEXTURE2D_DESC 物件描述呈現目標時，會覆寫此格式；亦即：

- BindFlags 成員已設定 D3D11_BIND_REDNER_TARGET 旗標。

- BindFlags 成員已清除 D3D11_BIND_DEPTH_STENCIL 旗標。

- Usage 成員設定為 D3D11_USAGE_DEFAULT。

## <a name="restrictions-and-limitations"></a>限制
 因為 B5G6R5 格式沒有 Alpha 色板，所以此變異不會保留 Alpha 內容。 如果您應用程式的呈現需要呈現目標中有 Alpha 色板，則不能只是切換至 B5G6R5 格式。

## <a name="example"></a>範例
 **16 bpp 呈現目標格式**變體，即可重現建立使用呈現目標的`CreateTexture2D`使用如下的程式碼：

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
