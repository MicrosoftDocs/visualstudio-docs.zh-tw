---
title: 16bpp 呈現目標格式變異 |Microsoft Docs
description: 將每個圖元的16位套用 (bpp) 轉譯目標格式變異，方法是將所有呈現目標和背景緩衝區的像素格式設定為 DXGI_FORMAT_B5G6R5_UNORM。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6d0f43e2b004272b6882ff4a19e62fa99c998e53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874622"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bpp 轉譯目標格式變異
將所有呈現目標和背景緩衝區的像素格式設定為 DXGI_FORMAT_B5G6R5_UNORM。

## <a name="interpretation"></a>解讀
 轉譯目標或背景緩衝區通常會使用 32 bpp (32 位的每圖元) 格式，例如 B8G8R8A8_UNORM。 32-bpp 格式可能會耗用大量的記憶體頻寬。 因為 B5G6R5_UNORM 格式是 16 bpp 的格式，其大小為 32-bpp 格式的一半，所以使用它可以減輕記憶體頻寬的壓力，但會降低色彩精確度的成本。

 如果此變異顯示大量的效能提高，則可能表示您的應用程式耗用太多記憶體頻寬。 您可以大幅提升效能，特別是當分析的框架有大量的過度繪製或 Alpha 混合時。

當您的應用程式具有下列條件時，16 bpp 轉譯目標格式可以減少記憶體不足的使用方式：
- 不需要高精確度的色彩複製。
- 不需要 Alpha 通道。
- 通常不會有平滑的漸層 (很容易就能在低色彩精確度) 下使用等量構件。

減少記憶體頻寬的其他策略包括：
- 減少過度繪製或 Alpha 混合的數量。
- 減少框架緩衝區的維度。
- 減少材質資源的維度。
- 減少材質資源的壓縮。

像往常一樣，您需要考慮所有這些最佳化伴隨的影像品質取捨。

屬於交換鏈一部分的應用程式具有背景緩衝區格式 (DXGI_FORMAT_B5G6R5_UNORM 不支援 16 bpp 的) 。 這些交換鏈是使用或所 `D3D11CreateDeviceAndSwapChain` 建立 `IDXGIFactory::CreateSwapChain` 。 若要解決這項限制，請執行下列步驟：
1. 使用建立 B5G6R5_UNORM 格式轉譯目標 `CreateTexture2D` ，並將其轉譯為該目標。
2. 藉由繪製以轉譯目標作為來源材質的全螢幕四個，將轉譯目標複製到交換鏈背景緩衝區。
3. 呼叫存在於您的交換鏈上。

   如果這個策略節省的頻寬比將轉譯目標複製到交換鏈背景緩衝區所耗用的頻寬更多，則轉譯效能也會改善。

   使用磚呈現技術的 GPU 架構可以使用 16 bpp 框架緩衝區格式來查看明顯的效能優勢。 這項改善的原因是，框架緩衝區的較大部分可以容納在每個磚的本機框架緩衝區快取中。 並排的呈現架構有時出現在行動電話話筒和平板電腦的 GPU 中；它們很少出現在此範圍之外。

## <a name="remarks"></a>備註
 每次呼叫可建立呈現目標的 `ID3D11Device::CreateTexture2D` 時，都會將呈現目標格式重設為 DXGI_FORMAT_B5G6R5_UNORM。 特別是 pDesc 中所傳遞的 D3D11_TEXTURE2D_DESC 物件描述呈現目標時，會覆寫此格式；亦即：

- BindFlags 成員已設定 D3D11_BIND_REDNER_TARGET 旗標。

- BindFlags 成員已清除 D3D11_BIND_DEPTH_STENCIL 旗標。

- Usage 成員設定為 D3D11_USAGE_DEFAULT。

## <a name="restrictions-and-limitations"></a>限制事項
 因為 B5G6R5 格式沒有 Alpha 色板，所以此變異不會保留 Alpha 內容。 如果您應用程式的呈現需要呈現目標中有 Alpha 色板，則不能只是切換至 B5G6R5 格式。

## <a name="example"></a>範例
 使用與下列類似的程式碼，即可針對使用所建立的呈現目標，重現 **16 bpp 轉譯目標格式** 變異 `CreateTexture2D` ：

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
