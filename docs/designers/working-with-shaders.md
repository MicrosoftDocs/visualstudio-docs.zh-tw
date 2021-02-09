---
title: 使用著色器
description: 瞭解如何使用 Visual Studio 中以圖形為基礎的著色器設計工具來設計自訂著色器效果。 您可以在 DirectX 型遊戲或應用程式中使用著色器。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bff5aee4337a464498fc4ac027eb05b2da912b61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844888"
---
# <a name="work-with-shaders"></a>使用著色器

您可以使用 Visual Studio 中以圖形為基礎的「著色器設計工具」來設計自訂著色器效果。 您可以在 DirectX 型遊戲或應用程式中使用這些著色器。

## <a name="shaders"></a>著色器

「著色器」是一個可執行圖形計算 (例如頂點轉換或像素著色) 的電腦程式，並且通常是在圖形處理器 (GPU) 而不是 CPU 上執行。 由於傳統、固定功能圖形管線的大多數階段現在都是由著色器程式執行，因此您可以使用它們來建立專門因應您應用程式需求的管線。

最常見的著色器類型包括「頂點著色器」和「像素著色器」，前者可在無法程式化的圖形硬體中，執行個別頂點計算及取代固定功能的轉換和照明電路系統；後者可在無法程式化的圖形硬體中，執行決定像素色彩的個別像素計算，以及取代固定功能的色彩結合器電路系統。 現代化圖形硬體讓更多類型的著色器都能夠執行 — 適用於圖形計算的「輪廓著色器」、「網域著色器」和「幾何著色器」，以及適用於非圖形運算的「計算著色器」。 這些階段中甚至沒有任何一個階段可在無法程式化的圖形硬體中使用。 起初，著色器是使用類似組件的語言建立的，這類語言提供與資料平行 (SIMD) 和以圖形為中心 (內積) 的指示。 現在，著色器通常是使用像 HLSL (高階著色器語言) 這類高階、類似 C 的語言建立的。

您可以使用「著色器設計工具」，而不透過輸入和編譯程式碼，以互動方式建立像素著色器。 在「著色器設計工具」中，著色器是由一些節點及節點間的連線所定義，這些節點代表資料和作業，而節點間的連線則代表資料值流程和透過著色器的中繼結果。 透過使用此方法及「著色器設計工具」中的即時預覽，您可以更容易以視覺方式呈現著色器的執行，並透過實驗「探索」有趣的著色器變化。

## <a name="dgsl-documents"></a>DGSL 文件

「著色器設計工具」會以「有向圖形著色器語言」(DGSL) 格式儲存著色器，這是一種以「有向圖形標記語言」(DGML) 為基礎的 XML 格式。 您可以在「模型編輯器」中將 DGSL 著色器直接套用至 3D 模型。 不過，您必須先將 DGSL 著色器以 DirectX 了解的格式 (例如 HLSL) 匯出，然後才能在您的應用程式中使用該著色器。

由於 DGSL 與 DGML 相容，因此您可以使用專為分析 DGML 文件而設計的工具來分析您的 DGSL 著色器。 如需有關 DGML 的資訊，請參閱[了解有向圖形標記語言 (DGML)](../modeling/customize-code-maps-by-editing-the-dgml-files.md)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[著色器設計工具](../designers/shader-designer.md)|描述如何使用 Visual Studio 著色器設計工具，搭配著色器一起運作。|
|[著色器設計工具節點](../designers/shader-designer-nodes.md)|探討您可用來達成圖形效果的「著色器設計工具」節點類型。|
|[著色器設計工具範例](../designers/how-to-create-a-basic-color-shader.md)|提供示範如何使用「著色器設計工具」來達成常見圖形效果的主題連結。|
