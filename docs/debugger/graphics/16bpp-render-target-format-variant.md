---
title: 16bpp Render Target Format Variant | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a63261a4ef8a6304bec8c2bdde1d9ec9113405e
ms.sourcegitcommit: 8530d15aa72fe058ee3a3b4714c36b8638f8b494
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188584"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bpp Render Target Format Variant
將所有呈現目標和背景緩衝區的像素格式設定為 DXGI_FORMAT_B5G6R5_UNORM。

## <a name="interpretation"></a>解譯
 A render target or back buffer typically uses a 32 bpp (32 bits per pixel) format such as B8G8R8A8_UNORM. 32-bpp formats can consume a large amount of memory bandwidth. Because the B5G6R5_UNORM format is a 16-bpp format that's half the size of 32-bpp formats, using it can relieve pressure on memory bandwidth, but at the cost of reduced color fidelity.

 如果此變異顯示大量的效能提高，則可能表示您的應用程式耗用太多記憶體頻寬。 You can gain significant performance improvement, especially when the profiled frame had a significant amount of overdraw or alpha-blending.

A 16-bpp render target format can reduce memory band with usage when your application has the following conditions:
- Doesn't require high-fidelity color reproduction.
- Doesn't require an alpha channel.
- Doesn't often have smooth gradients (which are susceptible to banding artifacts under reduced color fidelity).

Other strategies to reduce memory bandwidth include:
- Reduce the amount of overdraw or alpha-blending.
- Reduce the dimensions of the frame buffer.
- Reduce dimensions of texture resources.
- Reduce compressions of texture resources.

像往常一樣，您需要考慮所有這些最佳化伴隨的影像品質取捨。

Applications that are a part of a swap chain have a back buffer format (DXGI_FORMAT_B5G6R5_UNORM) that doesn't support 16 bpp. These swap chains are created by using `D3D11CreateDeviceAndSwapChain` or `IDXGIFactory::CreateSwapChain`. To work around this limitation, do the following steps:
1. Create a B5G6R5_UNORM format render target by using `CreateTexture2D` and render to that target.
2. Copy the render target onto the swap-chain backbuffer by drawing a full-screen quad with the render target as your source texture.
3. Call Present on your swap chain.

   If this strategy saves more bandwidth than is consumed by copying the render target to the swap-chain backbuffer, then rendering performance is improved.

   GPU architectures that use tiled rendering techniques can see significant performance benefits by using a 16 bpp frame buffer format. This improvement is because a larger portion of the frame buffer can fit in each tile's local frame buffer cache. 並排的呈現架構有時出現在行動電話話筒和平板電腦的 GPU 中；它們很少出現在此範圍之外。

## <a name="remarks"></a>備註
 每次呼叫可建立呈現目標的 `ID3D11Device::CreateTexture2D` 時，都會將呈現目標格式重設為 DXGI_FORMAT_B5G6R5_UNORM。 特別是 pDesc 中所傳遞的 D3D11_TEXTURE2D_DESC 物件描述呈現目標時，會覆寫此格式；亦即：

- BindFlags 成員已設定 D3D11_BIND_REDNER_TARGET 旗標。

- BindFlags 成員已清除 D3D11_BIND_DEPTH_STENCIL 旗標。

- Usage 成員設定為 D3D11_USAGE_DEFAULT。

## <a name="restrictions-and-limitations"></a>限制
 因為 B5G6R5 格式沒有 Alpha 色板，所以此變異不會保留 Alpha 內容。 如果您應用程式的呈現需要呈現目標中有 Alpha 色板，則不能只是切換至 B5G6R5 格式。

## <a name="example"></a>範例
 The **16 bpp Render Target Format** variant can be reproduced for render targets created by using `CreateTexture2D` by using code like this:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
