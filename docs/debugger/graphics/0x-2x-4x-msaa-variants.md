---
title: 0x-2x-4x MSAA Variant |Microsoft Docs
description: 瞭解如何使用0x、2x 或 4x MSAA 變異，覆寫所有呈現目標和交換鏈上的多重取樣消除鋸齒 (MSAA) 設定。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d4de52fb135e465e7adc938bb29c571bfcc1973
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726549"
---
# <a name="0x2x4x-msaa-variants"></a>0x/2x/4x MSAA 變異
覆寫所有呈現目標和交換鏈結上的多重取樣消除鋸齒 (MSAA) 設定。

## <a name="interpretation"></a>解讀
 多重取樣消除鋸齒會增加視覺品質，方式是在每個像素中取得多個位置的樣本；MSAA 層級愈大，採用的樣本就愈多，而且如果沒有 MSAA，則只會從像素中心取得一個樣本。 如果在應用程式中啟用 MSAA，則在呈現效能上通常會有適度但顯著的成本，但是在特定工作量下，或在特定 GPU 上，幾乎沒有任何影響。

 如果您的應用程式已啟用 MSAA，則較少的 MSAA 變異指出現有且較高層級 MSAA 所造成的相對效能成本。 特別是 0x MSAA 變異指出應用程式在沒有 MSAA 之情況下的相對效能。

 如果應用程式尚未啟用 MSAA，則 2x MSAA 和 4x MSAA 變異指出在應用程式中啟用它們的相對效能成本。 當成本為可接受的低水平時，請考慮啟用 MSAA 以增強應用程式的影像品質。

> [!NOTE]
> 您的硬體可能未完全支援所有格式的 MSAA。 如果其中任何變異遇到無法克服的硬體限制，則其在效能摘要表格中的資料行會空白，並會產生一則錯誤訊息。

## <a name="remarks"></a>備註
 這些變異會覆寫建立呈現目標的 `ID3DDevice::CreateTexture2D` 呼叫上的樣本計數和樣本品質引數。 特別是在下列情況下，會覆寫這些參數：

- `D3D11_TEXTURE2D_DESC` 中所傳遞的 `pDesc` 物件描述呈現目標；亦即：

  - BindFlags 成員已設定 D3D11_BIND_TARGET 旗標或 D3D11_BIND_DEPTH_STENCIL 旗標。

  - Usage 成員設定為 D3D11_USAGE_DEFAULT。

  - CPUAccessFlags 成員設定為 0。

  - MipLevels 成員設定為 1。

- 裝置針對要求的呈現目標格式 (D3D11_TEXTURE2D_DESC::Format 成員)，支援要求的樣本計數 (0、2 或 4) 和樣本品質 (0) (由 `ID3D11Device::CheckMultisampleQualityLevels` 決定)。

  如果 D3D11_TEXTURE2D_DESC::BindFlags 成員已設定 D3D_BIND_SHADER_RESOURCE 或 D3D11_BIND_UNORDERED_ACCESS 旗標，則會建立兩個版本的紋理；第一個版本已清除這些用做轉譯目標的旗標，而另一個版本是非 MSAA 紋理，它完整保留這些旗標作為第一個版本的解析緩衝區。 這是必要的，因為使用 MSAA 紋理做為著色器資源，或進行未排序存取都不可能會有效；例如，處理它的著色器會產生不正確的結果，原因是它需要非 MSAA 紋理。 如果變數已建立次要非 MSAA 紋理，則只要從裝置內容取消設定 MSAA 呈現目標，就會將其內容解析為非 MSAA 紋理。 同樣地，只要 MSAA 呈現目標應該繫結為著色器資源，或用於未排序存取檢視時，就會改為繫結解析的非 MSAA 紋理。

  這些變異也會覆寫使用 `IDXGIFactory::CreateSwapChain`、`IDXGIFactory2::CreateSwapChainForHwnd`、`IDXGIFactory2::CreateSwapChainForCoreWindow`、`IDXGIFactory2::CreateSwapChainForComposition` 和 `ID3D11CreateDeviceAndSwapChain` 所建立的所有交換鏈結上的 MSAA 設定。

  這些變更的實際影響在於，會完成對 MSAA 呈現目標的所有呈現，但是，如果應用程式使用其中一個呈現目標，或交換鏈結緩衝區做為著色器資源檢視，或未排序存取檢視，則會從呈現目標的已解析非 MSAA 複本中取樣資料。

## <a name="restrictions-and-limitations"></a>限制事項
 在 Direct3D11 中，MSAA 紋理的限制多於非 MSAA 紋理。 例如，您不可以在 MSAA 紋理上呼叫 `ID3D11DeviceContext::UpdateSubresource`，而且在下列情況呼叫 `ID3D11DeviceContext::CopySubresourceRegion` 會失敗：來源資源與目的地資源的樣本計數和樣本品質不符時；這種情況可能發生在此變異覆寫某個資源的 MSAA 設定，但未覆寫另一個資源的 MSAA 設定。

 播放偵測到這類衝突時，會盡力複寫想要的行為，但是可能無法精確地符合其結果。 雖然因誤解這些變異的影響而影響其效能的情況並不常見，但還是可能發生 (例如，像素著色器中的流量控制是由紋理的精確內容所決定時)，因為所複寫之紋理的內容可能不同。

## <a name="example-1"></a>範例 1
 使用與下面類似的程式碼，即可針對使用 `ID3D11Device::CreateTexture2D` 所建立的呈現目標，重現這些變異：

```cpp
D3D11_TEXTURE2D_DESC target_description;
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
target_description.SampleDesc.Quality = 0;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```

## <a name="example-2"></a>範例 2
 或者，針對使用 IDXGISwapChain::CreateSwapChain 或 D3D11CreateDeviceAndSwapChain 所建立的交換鏈結，使用與下面類似的程式碼：

```cpp
DXGI_SWAP_CHAIN_DESC chain_description;
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
chain_description.SampleDesc.Quality = 0;

// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.
```
