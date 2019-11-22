---
title: 使用 3D 資產來打造遊戲和應用程式 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9cc4f8038906de89afd86fd666fbb011e974362d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298090"
---
# <a name="working-with-3-d-assets-for-games-and-apps"></a>使用 3D 資產來打造遊戲和應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本文件所描述的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 工具，可用來建立或修改 DirectX 遊戲和應用程式的 3D 模型、紋理和著色器。

## <a name="directx-app-development-in-visual-studio"></a>Visual Studio 中的 DirectX 應用程式開發
 DirectX 應用程式通常會結合程式設計邏輯、DirectX API 和高階著色語言 (HLSL) 程式，以及音訊和 3D 視覺效果資產，以呈現豐富的互動式多媒體體驗。[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 所包含的工具可用來使用影像和紋理、3D 模型以及著色器，而且不需要離開 IDE 就能使用另一個工具。 Visual Studio 工具特別適用於建立「預留位置」資產，而您可以先使用這些資產來測試程式碼或建置原型，再委任生產環境就緒的資產，以及當您偵錯您的應用程式時檢查和修改生產環境就緒的資產。

 以下是有關可在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中使用之資產類型的詳細資訊。

### <a name="images-and-textures"></a>影像和紋理
 影像和紋理提供遊戲及應用程式中的色彩與視覺效果詳細資料。 在 3D 圖形中，紋理具有各種格式、類型和幾何形狀來支援不同的用途。 例如，法線貼圖提供更詳細 3D 模型光源的個別像素曲面法線，而立方體貼圖會在所有方向提供紋理作為 Sky-Boxing、反射和球面紋理對應等用途。 紋理可以提供 MIP 對應以支援有效的轉譯成不同的詳細程度，而且可支援不同的色頻和色彩順序。 紋理可以用各種壓縮格式加以儲存，能夠佔用很少的圖形專用記憶體，並且更有效率地協助 GPU 存取紋理。

 您可以使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 影像編輯器來處理許多常見類型和格式的影像和紋理。

### <a name="3-d-models"></a>立體模型
 3D 模型會在遊戲和應用程式中建立空間和圖形。 模型最少會將 3D 空間點 (稱為「頂點」) 的位置與索引資料一起編碼，以定義代表模型圖形的線條或三角形。 其他資料可以與這些頂點建立關聯；例如，色彩資訊、標準向量或應用程式特定屬性。 每個模型也可以定義整個物件屬性；例如，使用哪一個著色器來計算物件介面的外觀，或要套用的紋理。

 您可以使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 模型編輯器來處理數種常見格式的 3D 模型。

### <a name="shaders"></a>著色器
 著色器是可在圖形處理單元 (GPU) 上執行的小型網域特定程式。 著色器判斷如何將 3D 模型轉換成螢幕上圖形，以及這些圖形中每個像素的著色方式。 建立著色器並將它套用至遊戲或應用程式中的物件，即可提供物件獨特的外觀。

 您可以使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 著色器設計工具 (即圖形式著色器設計工具) 來建立自訂視覺效果，而不需要知道 HLSL 程式設計。

> [!NOTE]
> 如需如何開始 DirectX 程式設計的詳細資訊，請參閱 [DirectX](https://go.microsoft.com/fwlink/p/?LinkId=224633)。 如需如何偵錯 DirectX 應用程式的詳細資訊，請參閱[圖形診斷 (偵錯 DirectX 圖形)](../debugger/visual-studio-graphics-diagnostics.md)。

## <a name="directx-version-compatibility"></a>DirectX 版本相容性
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 使用 DirectX 來轉譯 2D 和 3D 資產。 您可以選取 DirectX 11 轉譯器或 Windows Advanced Rasterization Platform (WARP) 軟體轉譯器。 DirectX 11 轉譯器對 DirectX 11 和 DirectX 10 GPU 提供高效能硬體加速呈現轉譯。 WARP 轉譯器有助於確定您的資產適用於各種不同的電腦，包含未配備現代化圖形硬體的電腦，以及具有整合式圖形硬體的電腦。 如需 WARP 的詳細資訊，請參閱 [Windows Advanced Rasterization Platform (WARP) 指南](https://go.microsoft.com/fwlink/p/?LinkId=224634)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[使用紋理和影像](../designers/working-with-textures-and-images.md)|描述如何使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 來使用影像和紋理。|
|[使用 3D 模型](../designers/working-with-3-d-models.md)|描述如何使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 來使用 3D 模型。|
|[使用著色器](../designers/working-with-shaders.md)|描述如何使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 著色器設計工具來建立和修改自訂著色器效果。|
|[在遊戲或應用程式中使用 3D 資產](../designers/using-3-d-assets-in-your-game-or-app.md)|描述如何在遊戲或應用程式中使用資產，而資產是使用影像編輯器、模型編輯器或著色器設計工具所建立。|
