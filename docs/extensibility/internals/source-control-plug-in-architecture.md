---
title: 原始檔控制外掛程式架構 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f06f023a46fc9bc417e9630613a716f8dd448d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723438"
---
# <a name="source-control-plug-in-architecture"></a>原始檔控制外掛程式架構
您可以藉由執行和附加原始檔控制外掛程式，將原始檔控制支援加入 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的整合式開發環境（IDE）。 IDE 會透過妥善定義的原始檔控制外掛程式 API，連接到原始檔控制外掛程式。 IDE 藉由提供由工具列和功能表命令所組成的使用者介面（UI），來公開原始檔控制系統的版本控制功能。 原始檔控制外掛程式會執行原始檔控制功能。

## <a name="source-control-plug-in-resources"></a>原始檔控制外掛程式資源
 原始檔控制外掛程式提供的資源可協助您建立版本控制應用程式，並將其連接至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。 原始檔控制外掛程式包含必須由原始檔控制外掛程式執行的 API 規格，使其可以整合至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 中。 它也包含程式碼範例（以C++撰寫），其會執行基本架構原始檔控制外掛程式，示範符合原始檔控制外掛程式 API 的重要功能。

 如果您使用符合原始檔控制外掛程式 API 的必要函數集來建立原始檔控制 DLL，則原始檔控制外掛程式 API 規格可讓您運用所選的任何原始檔控制系統。

## <a name="components"></a>元件
 圖表中的原始檔控制介面卡套件是 IDE 的元件，可將使用者對原始檔控制作業的要求轉譯為原始檔控制外掛程式所支援的函式呼叫。 為了達到此目的，IDE 和原始檔控制外掛程式必須擁有有效的對話方塊，以便在 IDE 和外掛程式之間來回傳遞資訊。 若要讓此對話方塊進行，兩者都必須使用相同的語言。 本檔中所述的原始檔控制外掛程式 API 是此交換的常見詞彙。

 ![原始程式碼控制架構圖表](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")顯示 VS 與原始檔控制外掛程式之間互動的架構圖

 如架構圖所示，在圖表中標記為 VS shell 的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell，會裝載使用者的工作專案和相關聯的元件，例如編輯器和方案總管。 原始檔控制介面卡封裝會處理 IDE 與原始檔控制外掛程式之間的互動。 原始檔控制介面卡套件提供自己的原始檔控制 UI。 這是使用者與互動的最上層 UI，可起始和定義原始檔控制作業的範圍。

 原始檔控制外掛程式可以有自己的 UI，其中可能包含兩個部分，如圖所示。 標示為「廠商 UI」的方塊代表自訂使用者介面元素，您可以在原始檔控制外掛程式建立者中提供。 當使用者叫用先進的原始檔控制作業時，原始檔控制外掛程式會直接顯示這些功能。 標示為「協助程式 UI」的方塊是一組可透過 IDE 間接叫用的原始檔控制外掛程式 UI 功能。 原始檔控制外掛程式會透過 IDE 所提供的特殊回呼函式，將 UI 相關訊息傳遞至 IDE。 協助程式 UI 可讓您更順暢地與 IDE 整合（通常是透過使用 [ **Advanced** ] 按鈕），因而提供更一致的使用者體驗。

 原始檔控制外掛程式無法對 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell 進行變更，因此無法對 IDE 所提供的原始檔控制介面卡封裝或原始檔控制 UI 進行變更。 它必須透過執行各種原始檔控制外掛程式 API 函式所提供的最大彈性，這些功能有助於終端使用者的整合體驗。 原始檔控制外掛程式 API 檔的參考章節包含一些先進的原始檔控制外掛程式功能的資訊。 若要利用這些功能，原始檔控制外掛程式必須在初始化期間，將其先進的功能宣告到 IDE，而且必須針對每項功能執行特定的 advanced 函數。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)
- [字彙](../../extensibility/source-control-plug-in-glossary.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)