---
title: 16bpp 呈現目標格式變異 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b315c7ab9bb10d039e81ba26b1beb9c4447a205
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112373"
---
# <a name="16bpp-render-target-format-variant"></a>16bpp 呈現目標格式變異
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將所有呈現目標和背景緩衝區的像素格式設定為 DXGI_FORMAT_B5G6R5_UNORM。  
  
## <a name="interpretation"></a>解譯  
 呈現目標或背景緩衝區通常會使用 32bpp (每像素 32 位元數) 格式，例如 B8G8R8A8_UNORM。 32bpp 格式可能會耗用許多記憶體頻寬。 因為 B5G6R5_UNORM 格式是大小為 32bpp 格式一半的 16bpp 格式，所以使用它可以釋放記憶體頻寬的壓力，但會降低色彩逼真度。  
  
 如果此變異顯示大量的效能提高，則可能表示您的應用程式耗用太多記憶體頻寬。 尤其是分析的畫面格有大量過度繪製，或包含許多 Alpha 混色時，效能可能會明顯提高。  
  
 如果應用程式所呈現的場景類型不需要再現高逼真度色彩，也不需要呈現目標具有 Alpha 色板，而且經常不包含平滑漸層 (容易受色彩逼真度降低的級區成品所影響)，請考慮使用 16bpp 呈現目標格式，來減少記憶體頻寬使用量。  
  
 如果應用程式中所呈現的場景，需要再現高逼真度色彩或 Alpha 色板，或是經常使用平滑漸層，請考慮使用其他策略來減少記憶體頻寬使用量；例如，減少過度繪製或 Alpha 透明混色數量、減少畫面格緩衝區的維度，或透過啟用壓縮或減少維度，來修改紋理資源以耗用較少的記憶體頻寬。 像往常一樣，您需要考慮所有這些最佳化伴隨的影像品質取捨。  
  
 如果您的應用程式切換至 16bpp 背景緩衝區會有所助益，但它是您交換鏈結的一部分，所以需要採取額外的步驟，因為 DXGI_FORMAT_B5G6R5_UNORM 不是使用 `D3D11CreateDeviceAndSwapChain` 或 `IDXGIFactory::CreateSwapChain` 建立的交換鏈結所支援的背景緩衝區格式。 您需要改成使用 `CreateTexture2D` 建立 B5G6R5_UNORM 格式呈現目標，並改向該呈現目標呈現。 接著，在交換鏈結上呼叫 Present 之前，請先使用呈現目標做為來源紋理來繪製整個螢幕的四分之一，以將呈現目標複製到交換鏈結背景緩衝區。 雖然這個額外步驟會耗用一些記憶體頻寬，但是大部分的呈現作業會耗用較少的頻寬，因為它們會影響 16bpp 呈現目標；如果這樣節省下來的頻寬，多於將呈現目標複製至交換鏈結背景緩衝區所耗用的頻寬，則會改善呈現效能。  
  
 透過使用 16bpp 畫面格緩衝區格式，可以讓使用並排呈現技術的 GPU 架構大幅提升效能，因為畫面格緩衝區的較大部分可能會放入每個並排的本機畫面格緩衝區快取。 並排的呈現架構有時出現在行動電話話筒和平板電腦的 GPU 中；它們很少出現在此範圍之外。  
  
## <a name="remarks"></a>備註  
 每次呼叫可建立呈現目標的 `ID3D11Device::CreateTexture2D` 時，都會將呈現目標格式重設為 DXGI_FORMAT_B5G6R5_UNORM。 特別是 pDesc 中所傳遞的 D3D11_TEXTURE2D_DESC 物件描述呈現目標時，會覆寫此格式；亦即：  
  
- BindFlags 成員已設定 D3D11_BIND_REDNER_TARGET 旗標。  
  
- BindFlags 成員已清除 D3D11_BIND_DEPTH_STENCIL 旗標。  
  
- Usage 成員設定為 D3D11_USAGE_DEFAULT。  
  
## <a name="restrictions-and-limitations"></a>限制  
 因為 B5G6R5 格式沒有 Alpha 色板，所以此變異不會保留 Alpha 內容。 如果您應用程式的呈現需要呈現目標中有 Alpha 色板，則不能只是切換至 B5G6R5 格式。  
  
## <a name="example"></a>範例  
 **16bpp 呈現目標格式**變體，即可重現建立使用呈現目標的`CreateTexture2D`使用如下的程式碼：  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
