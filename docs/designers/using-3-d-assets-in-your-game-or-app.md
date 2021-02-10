---
title: 在遊戲或應用程式中使用 3D 資產
description: 瞭解如何使用 Visual Studio 來處理3D 資產，並將其納入組建中。 Visual Studio 針對其產生的每個資產提供組建自訂。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18294a9a6b6a0b967748d6a00817e4194e4cc32f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948527"
---
# <a name="how-to-use-3d-assets-in-your-game-or-app"></a>作法：在遊戲或應用程式中使用 3D 資產

本文描述如何使用 Visual Studio 處理 3D 資產，並將它們包括在您的組建中。

在 Visual Studio 中使用工具建立 3D 資產之後，下一步是在您的應用程式中使用它們。 但是，您的資產必須先轉換為 DirectX 可以了解的格式，才能使用它們。 為了協助您轉換資產，Visual Studio 提供它可產生之每種資產類型的組建自訂。 若要在組建中包括資產，您只需要設定專案使用組建自訂、將資產加入至專案，以及設定資產使用正確的組建自訂。 之後，您可以將資產載入至應用程式，並建立和填寫 DirectX 資源來使用它們，就像在任何其他 DirectX 應用程式中一樣。

## <a name="configure-your-project"></a>設定您的專案

Visual Studio 必須先知道有關您要部署的資產類型，才能在建置時部署 3D 資產。 Visual Studio 已知道許多一般檔案類型；但是，因為只有特定類型的應用程式才能使用 3D 資產，所以 Visual Studio 不會假設專案會建置這些類型的檔案。 您可以告訴 Visual Studio 您的應用程式使用這些類型的資產，方法是使用針對每種資產類型提供的「組建自訂」，告訴 Visual Studio 如何以有用方式處理不同類型的檔案。 因為是根據個別專案來套用這些自訂，所以您只需要在專案中加入適當的自訂即可。

### <a name="to-add-the-build-customizations-to-your-project"></a>將組建自訂加入至專案

1. 在 [方案總管] 中，開啟專案的捷徑功能表，然後選擇 [組建相依性] > [組建自訂]。

   [Visual C++ 組建自訂檔] 對話方塊隨即出現。

2. 在 [可用的組建自訂檔] 下，選取對應至您要用於專案之資產類型的核取方塊，如下表所述：

    |資產類型|組建自訂名稱|
    |----------------| - |
    |紋理和影像|**ImageContentTask(.targets、.props)**|
    |3D 模型|**MeshContentTask(.targets、.props)**|
    |著色器|**ShaderGraphContentTask(.targets、.props)**|

3. 選擇 [確定]  按鈕。

## <a name="include-assets-in-your-build"></a>在組建中包括資產

現在，專案知道您要使用的不同類型 3D 資產，下一步是告訴它哪些檔案是 3D 資產，以及它們是哪些類型的資產。

### <a name="to-add-an-asset-to-your-build"></a>將資產加入至組建

1. 在方案總管中，於專案中，開啟資產的捷徑功能表，然後選擇 [屬性]。

   資產的 [屬性頁] 對話方塊隨即出現。

2. 請確定 [組態] 和 [平台] 屬性設定為您要套用變更的值。

3. 在 [組態屬性] 下，選擇 [一般]，然後在屬性格線的 [一般] 下，將 [項目類型] 屬性設定為適當的內容管線項目類型。 例如，針對影像或紋理檔，選擇 [影像內容管線]。

    > [!IMPORTANT]
    > Visual Studio 預設會假設應該使用 Visual Studio 內建的 **影像** 項目類型來分類多種類型的影像檔。 因此，您需要變更想要由影像內容管線處理之每個影像的 [項目類型] 屬性。 3D 模型和視覺著色器圖形的其他類型內容管線來源檔，預設為正確的 [項目類型]。

4. 選擇 [確定]  按鈕。

以下是三種內容管線項目類型與其相關聯的來源和輸出檔案類型。

|項目類型|原始程式檔類型|輸出檔案格式|
|---------------| - | - |
|**影像內容管線**|可移植網狀圖形 (*.png*) <br /><br /> JPEG (*.jpg*、*.jpeg*、*.jpe*、*.jfif*)<br /><br /> DirectDraw 表面 (*.dds*)<br /><br /> 圖形交換格式 (*.gif*) <br /><br /> 點陣圖 (*.bmp*、 *.dib*) <br /><br /> 標記的影像檔案格式 (*.tif*、 *tiff*) <br /><br /> Targa (*.tga*)|DirectDraw 介面 (*. dd*) |
|**網狀內容管線**|AutoDesk FBX 交換檔案 (*.fbx*)<br /><br /> Collada DAE 檔案 (*.dae*)<br /><br /> Wavefront OBJ 檔案 (*.obj*)|3D 網格檔 (*. cmo*) |
|**著色器內容管線**|視覺著色器圖形 (*.dgsl*)|已編譯的著色器輸出 (*.cso*)|

## <a name="configure-asset-content-pipeline-properties"></a>設定資產內容管線屬性

您可以設定每個資產檔案的內容管線屬性，以透過特定方式來建置它。

### <a name="to-configure-content-pipeline-properties"></a>設定內容管線屬性

1. 在方案總管中，於專案中，開啟資產檔案的捷徑功能表，然後選擇 [屬性]。

   資產的 [屬性頁] 對話方塊隨即出現。

2. 請確定 [組態] 和 [平台] 屬性設定為您要套用變更的值。

3. 在 [組態屬性] 下，選擇內容管線節點 (例如，針對紋理和影像資產選擇 [影像內容管線])，然後在屬性方格中，將屬性設定為適當的值。 例如，若要在建置時產生紋理資產的 MIP 對應，請將 [產生 Mips] 屬性設定為 [是]。

4. 選擇 [確定]  按鈕。

### <a name="image-content-pipeline-configuration"></a>影像內容管線組態

當您使用影像內容管線工具建置紋理資產時，可以使用各種方式壓縮紋理，以及指出是否應該在建置時產生 MIP 層級，還可以變更輸出檔案的名稱。

|屬性|描述|
|--------------|-----------------|
|**壓縮**|指定用於輸出檔案的壓縮類型。<br /><br /> 可用的選項包括：<br /><br /> -   **無壓縮**<br />-   **BC1_UNORM 壓縮**<br />-   **BC1_UNORM_SRGB 壓縮**<br />-   **BC2_UNORM 壓縮**<br />-   **BC2_UNORM_SRGB 壓縮**<br />-   **BC3_UNORM 壓縮**<br />-   **BC3_UNORM_SRGB 壓縮**<br />-   **BC4_UNORM 壓縮**<br />-   **BC4_SNORM 壓縮**<br />-   **BC5_UNORM 壓縮**<br />-   **BC5_SNORM 壓縮**<br />-   **BC6H_UF16 壓縮**<br />-   **BC6H_SF16 壓縮**<br />-   **BC7_UNORM 壓縮**<br />-   **BC7_UNORM_SRGB 壓縮**<br /><br /> 如需不同 DirectX 版本所支援壓縮格式的資訊，請參閱 [DXGI 程式設計指南](/windows/win32/direct3ddxgi/dx-graphics-dxgi-overviews)。|
|轉換成預乘的 Alpha 格式|[是] 在輸出檔案中將影像轉換成預乘的 Alpha 格式，否則為 [否]。 只會變更輸出檔案，來源影像並不會變更。|
|**產生 Mips**|[是] 在建置時產生完整 MIP 鏈結，並將它併入輸出檔案中；否則為 [否]。 如果為 [否]，而且原始程式檔已包含 MIP 對應鏈結，則輸出檔案會有 MIP 鏈結；否則，輸出檔案沒有 MIP 鏈結。|
|**內容輸出**|指定輸出檔案的名稱。 **重要事項：** 變更輸出檔案的副檔名並不會影響其檔案格式。|

### <a name="mesh-content-pipeline-configuration"></a>網狀內容管線組態

當您使用網狀內容管線工具建置網狀資產時，可以變更輸出檔案的名稱。

|屬性|描述|
|--------------|-----------------|
|**內容輸出**|指定輸出檔案的名稱。 **重要事項：** 變更輸出檔案的副檔名並不會影響其檔案格式。|

### <a name="shader-content-pipeline-configuration"></a>著色器內容管線組態

當您使用著色器內容管線工具建置著色器資產時，可以變更輸出檔案的名稱。

|屬性|描述|
|--------------|-----------------|
|**內容輸出**|指定輸出檔案的名稱。 **重要事項：** 變更輸出檔案的副檔名並不會影響其檔案格式。|

## <a name="load-and-use-3d-assets-at-run-time"></a>在執行階段載入並使用 3D 資產

### <a name="use-textures-and-images"></a>使用紋理和影像

Direct3D 提供用於建立紋理資源的函式。 在 Direct3D 11 中，D3DX11 公用程式庫提供其他直接從影像檔建立紋理資源和資源檢視的函式。 如需如何在 Direct3D 11 中建立紋理資源的詳細資訊，請參閱[紋理](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures)。 如需如何使用 D3DX11 程式庫從影像檔建立紋理資源或資源檢視的詳細資訊，請參閱[如何從檔案初始化紋理](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-how-to)。

### <a name="use-3d-models"></a>使用 3D 模型

Direct3D 11 未提供用於從 3D 模型建立資源的函式。 而是，您需要撰寫用來讀取 3D 模型檔案程式碼，並建立代表 3D 模型的端點和索引緩衝區，以及模型所需的任何資源 (例如，紋理或著色器)。

### <a name="use-shaders"></a>使用著色器

Direct3D 提供用於建立著色器資源，並將它們繫結至可程式化圖形管線的函式。 如需如何在 Direct3D 中建立著色器資源並將它繫結至管線的詳細資訊，請參閱 [HLSL 程式設計指南](/windows/win32/direct3dhlsl/dx-graphics-hlsl-pguide)。

在可程式化圖形管線中，管線的每個階段都必須將結果提供給管線的下一個階段，而該結果是使用下一個階段可了解的方式進行格式化。 因為著色器設計工具只能建立像素著色器，所以這表示此結果是取決於您的應用程式，以確保它所接收的資料為預期的格式。 數個可程式化著色器階段發生在像素著色器之前，並執行幾何轉換：端點著色器、輪廓著色器、網域著色器和幾何著色器。 不可程式化鑲嵌式階段也發生在像素著色器之前。 不管上述哪個階段是直接優先於像素著色器之前，都必須要提供下列格式的結果：

```hlsl
struct PixelShaderInput
{
    float4 pos : SV_POSITION;
    float4 diffuse : COLOR;
    float2 uv : TEXCOORD0;
    float3 worldNorm : TEXCOORD1;
    float3 worldPos : TEXCOORD2;
    float3 toEye : TEXCOORD3;
    float4 tangent : TEXCOORD4;
    float3 normal : TEXCOORD5;
};
```

根據您在著色器中使用的著色器設計工具節點，可能也需要提供其他資料，而這些資料的格式是根據這些定義：

```hlsl
Texture2D Texture1 : register( t0 );
Texture2D Texture2 : register( t1 );
Texture2D Texture3 : register( t2 );
Texture2D Texture4 : register( t3 );
Texture2D Texture5 : register( t4 );
Texture2D Texture6 : register( t5 );
Texture2D Texture7 : register( t6 );
Texture2D Texture8 : register( t7 );

TextureCube CubeTexture1 : register( t8 );
TextureCube CubeTexture2 : register( t9 );
TextureCube CubeTexture3 : register( t10 );
TextureCube CubeTexture4 : register( t11 );
TextureCube CubeTexture5 : register( t12 );
TextureCube CubeTexture6 : register( t13 );
TextureCube CubeTexture7 : register( t14 );
TextureCube CubeTexture8 : register( t15 );

SamplerState TexSampler : register( s0 );

cbuffer MaterialVars : register (b0)
{
    float4 MaterialAmbient;
    float4 MaterialDiffuse;
    float4 MaterialSpecular;
    float4 MaterialEmissive;
    float MaterialSpecularPower;
};

cbuffer LightVars : register (b1)
{
    float4 AmbientLight;
    float4 LightColor[4];
    float4 LightAttenuation[4];
    float3 LightDirection[4];
    float LightSpecularIntensity[4];
    uint IsPointLight[4];
    uint ActiveLights;
}

cbuffer ObjectVars : register(b2)
{
    float4x4 LocalToWorld4x4;
    float4x4 LocalToProjected4x4;
    float4x4 WorldToLocal4x4;
    float4x4 WorldToView4x4;
    float4x4 UVTransform4x4;
    float3 EyePosition;
};

cbuffer MiscVars : register(b3)
{
    float ViewportWidth;
    float ViewportHeight;
    float Time;
};
```

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[如何：匯出包含 mipmap 的材質](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|描述如何使用影像內容管線，匯出含有預先計算之 MIP 對應的紋理。|
|[如何：匯出包含預乘 Alpha 的材質](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|描述如何使用影像內容管線，匯出含有預乘的 Alpha 值的紋理。|
|[如何：匯出材質以搭配 Direct2D 或 JavaScript 應用程式使用](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|描述如何使用影像內容管線，匯出可用於 Direct2D 或 JavaScript 應用程式的紋理。|
|[使用3D 資產來打造遊戲和應用程式](../designers/working-with-3-d-assets-for-games-and-apps.md)|描述 Visual Studio 提供用於建立和管理 3D 資產 (包括紋理和影像)、3D 模型和著色器的編輯工具。|
|[如何：匯出著色器](../designers/how-to-export-a-shader.md)|描述如何從著色器設計工具匯出著色器。|
