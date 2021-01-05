---
title: BC 紋理壓縮變異 |Microsoft Docs
description: 使用 BC 紋理壓縮變異來允許區塊壓縮 (BC) 具有 B8G8R8X8、B8G8R8A8 或 R8G8B8A8 變化的像素格式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e767268073f896de590386854a0d2c9ce2803073
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726445"
---
# <a name="bc-texture-compression-variant"></a>BC 紋理壓縮變異
在具有 B8G8R8X8、B8G8R8A8 或 R8G8B8A8 像素格式變異的紋理上啟用區塊壓縮。

## <a name="interpretation"></a>解讀
 區塊壓縮格式 (如 BC1、BC2 和 BC3) 佔用的記憶體遠低於未壓縮的影像格式，因此耗用極少的記憶體頻寬。 與使用每像素 32 位元數的未壓縮格式相較之下，BC1 (過去稱為 DXT1) 可達到 8:1 壓縮，而 BC3 (過去稱為 DXT5) 可達到 4:1。 BC1 與 BC3 之間的差異是 BC1 不支援 Alpha 色板，而 BC3 支援區塊壓縮 Alpha 色板。 雖然具有高壓縮率，但是一般紋理只會降低極少的影像品質。 不過，特定類型的紋理 (例如，在小區域內有大量色彩變化的紋理) 的區塊壓縮，可能會有無法接受的結果。

 如果您的紋理適合進行區塊壓縮，而且不需要有完美的色彩逼真度，請考慮使用區塊壓縮格式來減少記憶體使用量，而且會耗用較少的頻寬。

## <a name="remarks"></a>備註
 在每次呼叫可建立來源紋理的 `ID3DDevice::CreateTexture2D` 時，使用區塊壓縮格式，即可壓縮紋理。 特別是在下列情況下，會壓縮紋理：

- `D3D11_TEXTURE2D_DESC` 中所傳遞的 `pDesc` 物件描述未變更的著色器資源；亦即：

  - BindFlags 成員只設定 D3D11_BIND_SHADER_RESOURCE 旗標。

  - Usage 成員設定為 D3D11_USAGE_DEFAULT 或 D3D11_USAGE_IMMUTABLE。

  - CPUAccessFlags 成員設定為 0 (無 CPU 存取)。

  - SamplerDesc 成員的 Count 成員設定為 1 (無多重取樣消除鋸齒 (MSAA))。

- 會將初始資料提供給 `CreateTexture2D` 呼叫。

  以下是支援的來源格式和其區塊壓縮格式。

|原始格式 (來源)|壓縮格式 (目標)|
|------------------------------|------------------------------|
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (過去稱為 DXT1)|
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (過去稱為 DXT5)|
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|

 如果未列出您紋理的格式，則不會修改紋理。

## <a name="restrictions-and-limitations"></a>限制事項
 有時，使用 B8G8R8A8 或 R8G8B8A8 影像格式變化所建立的紋理，沒有確實使用 Alpha 色板，但是變異沒有方法知道是否有使用它。 為了在使用 Alpha 色板時維護正確性，變異一律會將這些格式編碼為效率較低的 BC3 格式。 您可以透過此變異，協助圖形畫面格分析更了解您應用程式的潛在呈現效能，方法是在未使用 Alpha 色板時，使用 B8G8R8X8 影像格式變化，讓變異可以使用效率較高的 BC1 格式。

## <a name="example"></a>範例
 此變異會先在執行階段對紋理進行區塊壓縮，再呼叫 `CreateTexture2D`。 建議您不要對實際執行程式碼使用此方式，因為未壓縮的紋理會耗用較多的磁碟空間，而且因為額外步驟可能會大幅增加應用程式中的載入時間，畢竟區塊壓縮需要大量計算資源來進行編碼。 建議您改用屬於您組建管線的影像編輯器或影像處理器，來離線壓縮紋理。 這些方式會減少磁碟空間需求、去除應用程式中的執行階段額外負荷，以及提供更多的處理時間，讓您可以保留最佳影像品質。

## <a name="see-also"></a>請參閱
- [半/季材質維度變異](half-quarter-texture-dimensions-variant.md)