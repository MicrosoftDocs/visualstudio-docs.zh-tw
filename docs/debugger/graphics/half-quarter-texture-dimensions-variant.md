---
title: Half-Quarter 材質維度變異數 |Microsoft Docs
description: 如果較小的紋理顯示較大的效能提升，則建議使用 GPU 材質快取的記憶體頻寬壓力或效率不佳。 請考慮讓紋理大小變小。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd3cc5d5517818934a20c9064e718cf65f9d3a65
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995144"
---
# <a name="halfquarter-texture-dimensions-variant"></a>半/四分之一紋理維度變異
減少非呈現目標的紋理上的紋理維度。

## <a name="interpretation"></a>解譯
 較少的紋理會佔用較少的記憶體，因此會耗用較小的記憶體頻寬，並減少 GPU 紋理快取的壓力。 不過，細節較少可能會導致影像品質下降，特別是在 3-D 場景中靠近檢視或放大檢視時。

 如果此變異顯示大量的效能提高，可能表示您的應用程式耗用太多記憶體頻寬，或是無效率地使用紋理快取，或兩者皆是。 也可能表示紋理所佔用的 GPU 記憶體高於可用的 GPU 記憶體，這樣會造成將紋理分頁至系統記憶體。

 如果您的應用程式耗用太多記憶體頻寬，或無效率地使用紋理快取，請考慮減少紋理的大小，但只限於在您考慮過為適當的紋理啟用 MIP 對應之後。 與較小的紋理一樣，MIP 對應過的紋理會耗用較少的記憶體頻寬 (雖然會佔用較多的 GPU 記憶體)，並增加快取使用量，但是不會減少紋理細節。 只要增加的記憶體使用量，不會造成將紋理分頁至系統記憶體，都建議使用 MIP 對應。

 如果紋理所佔用的 GPU 記憶體高於可用的 GPU 記憶體，請考慮減少紋理的大小，但只限於在您考慮過壓縮適當的紋理之後。 與較小的紋理一樣，壓縮過的紋理會佔用較少的記憶體，並減少分頁至系統記憶體的需求，但也會降低其色彩逼真度。 雖然壓縮不適用於所有紋理 (視其內容而定，例如，在小區域內有顯著色彩變化的紋理)，但是適用於大部分的紋理，而且壓縮可保留的整體影像品質優於減少其大小。

## <a name="remarks"></a>備註
 每次呼叫可建立來源紋理的 `ID3D11Device::CreateTexture2D` 時，紋理維度都會減少。 特別是 `pDesc` 中所傳遞的 D3D11_TEXTURE2D_DESC 物件描述呈現所使用的紋理時，紋理維度會減少；亦即：

- BindFlags 成員只設定 D3D11_BIND_SHADER_RESOURCE 旗標。

- MiscFlags 成員未設定 D3D11_RESOURCE_MISC_TILE_POOL 旗標或 D3D11_RESOURCE_MISC_TILED 旗標 (不會調整並排資源的大小)。

- 紋理格式可支援做為呈現目標 (由 D3D11_FORMAT_SUPPORT_RENDER_TARGET 所決定)，而這是減少紋理大小的必要條件。 也支援 BC1、BC2 和 BC3 格式，即使這些格式不支援做為呈現目標。

  如果是由應用程式提供初始資料，則此變異會先將紋理資料縮放為適當的大小，再建立紋理。 如果是以區塊壓縮格式 (例如 BC1、BC2 或 BC3) 提供初始資料，則會先將它解碼、縮放並重新編碼，再用來建立較小的紋理 (區塊壓縮的特性即意味著，額外的解碼-縮放-編碼流程，幾乎一律會導致影像品質低於從先前未曾編碼過，但已縮放過的紋理版本產生的區塊壓縮紋理)。

  如果啟用紋理的 MIP 對應，則變異也會據此減少 MIP 層級數目 (縮放為一半大小時會少一個層級，縮放為四分之一大小時則會少兩個層級)。

## <a name="example"></a>範例
 在呼叫之前，此變異會在執行時間調整紋理的大小 `CreateTexture2D` 。 建議您不要對實際執行程式碼使用此方式，因為完整大小的紋理會耗用較多的磁碟空間，而且因為額外步驟可能會增加應用程式中的載入時間，特別是針對壓縮過的紋理，畢竟這類紋理需要大量計算資源來進行編碼。 建議您改用屬於您組建管線的影像編輯器或影像處理器，來離線調整紋理大小。 這些方式會減少磁碟空間需求，並去除應用程式中的執行階段額外負荷，以及提供更多的處理時間，讓您可以在壓縮紋理時保留最佳影像品質。

## <a name="see-also"></a>另請參閱
- [Mip-map 產生變異](mip-map-generation-variant.md)
- [BC 紋理壓縮變異](bc-texture-compression-variant.md)