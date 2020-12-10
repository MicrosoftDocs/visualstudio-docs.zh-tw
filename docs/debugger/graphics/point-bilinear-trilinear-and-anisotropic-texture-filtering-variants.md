---
title: 點/雙線性/三線性/非等材質篩選變數
description: 如果點、雙線性、三線性或非等向性紋理篩選變異的效能成本很重要，您可以考慮其使用是否值得成本。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c38869b4c8daa4cb4433f9f6a64afcc7398c9a9c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996080"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>點、雙線性、三線性和各向異性紋理篩選變異
覆寫適當的紋理取樣器上的篩選模式。

## <a name="interpretation"></a>解譯
 不同的紋理取樣方法具有不同的效能成本和影像品質。 若要增加成本 (以及增加視覺品質)，篩選模式為：

1. 點篩選 (花費最少，視覺品質最差)

2. 雙線性篩選

3. 三線性篩選

4. 非等向性篩選 (花費最多，視覺品質最佳)

   如果每個變異的效能成本很大，或因較密集的篩選模式而增加，您可以衡量其成本與其增加的影像品質。 基於您的評量，您可能會接受額外的效能成本以增加視覺品質，也可能會接受較差的視覺品質以達到較高的畫面播放速率，或回收您可能以其他方式使用的效能。

   如果您發現不論篩選模式為何，效能成本都很少或十分穩定 (例如，您設為目標的 GPU 有足夠的著色器產出和記憶體頻寬時)，請考慮使用非等向性篩選，來達到您應用程式中的最佳影像品質。

## <a name="remarks"></a>備註
 這些變異會覆寫 `ID3D11DeviceContext::PSSetSamplers` 呼叫上的取樣器狀態，而在此呼叫中，應用程式所提供之取樣器的篩選模式為下列其中一項：

- `D3D11_FILTER_MIN_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`

- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`

- `D3D11_FILTER_ANISOTROPIC`

  在 **點紋理篩選** 變異中，應用程式所提供的篩選模式會取代為 `D3D11_FILTER_MIN_MAG_MIP_POINT`；在 **雙線性紋理篩選** 變異中，則會取代為 `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`；而在 **三線性紋理篩選** 變異中，則會取代為 `D3D11_FILTER_MIN_MAG_MIP_LINEAR`。

  在 **非等向性紋理篩選** 變異中，應用程式所提供的篩選模式會取代為 `D3D11_FILTER_ANISOTROPIC`，而且「最大非等向性」會設定為 16。

## <a name="restrictions-and-limitations"></a>限制事項
 在 Direct3D 中，功能層級 9.1 會指定最大非等向性為 2x。 因為 **非等向性紋理篩選** 變異嘗試以獨佔方式使用 16x 非等向性，所以在功能層級 9.1 裝置上執行畫面格分析時，播放會失敗。 受此限制影響的現代裝置包括 ARM Surface RT 和 Surface 2 Windows 平板電腦。 還是可以在一些電腦上發現的較舊型 GPU 也是會受到影響，但是它們已被廣泛地視為過時，且漸漸地不常見。

## <a name="example-1"></a>範例 1
 使用與下列類似的程式碼，即可重現 **點紋理篩選** 變異：

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-2"></a>範例 2
 使用與下列類似的程式碼，即可重現 **雙線性紋理篩選** 變異：

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-3"></a>範例 3
 使用與下列類似的程式碼，即可重現 **三線性紋理篩選** 變異：

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-4"></a>範例 4
 使用與下列類似的程式碼，即可重現 **非等向性紋理篩選** 變異：

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;
sampler_description.MaxAnisotropy = 16;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```
