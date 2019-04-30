---
title: 原始檔控制外掛程式架構 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ff9c73ebbe976df7c3d25304280e743cad0423c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908514"
---
# <a name="source-control-plug-in-architecture"></a>原始檔控制外掛程式架構
您可以加入至原始檔控制支援[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由實作和附加的原始檔控制外掛程式的整合式的開發環境 (IDE)。 IDE 會連接到原始檔控制外掛程式，透過定義完善的原始檔控制外掛程式 API。 IDE 會提供工具列和功能表命令所組成的使用者介面 (UI)，以顯示原始檔控制系統的版本控制功能。 原始檔控制外掛程式會實作原始檔控制功能。

## <a name="source-control-plug-in-resources"></a>原始檔控制外掛程式資源
 原始檔控制外掛程式提供可協助建立並連線到應用程式版本設定資源[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。 原始檔控制外掛程式含有 API 規格，必須實作原始檔控制外掛程式，讓它可以整合到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。 它也包含程式碼範例 (以C++) 實作的基本架構的原始檔控制外掛程式示範實作必要的功能與原始檔控制外掛程式 API 相容。

 原始檔控制外掛程式 API 規格可讓您使用您選擇的任何原始檔控制系統，如果您建立一組必要根據原始檔控制外掛程式 API 所實作的函式的原始檔控制 DLL。

## <a name="components"></a>元件
 在圖表中的原始檔控制配接器套件是轉譯到原始檔控制外掛程式所支援的函式呼叫的原始檔控制作業的使用者要求的 ide 的元件。 此動作，IDE 和原始檔控制外掛程式必須有一個有效的對話方塊，其中的 IDE 和外掛程式之間來回傳遞資訊。 進行這個對話，都必須使用相同的語言。 這份文件中所述的原始檔控制外掛程式 API 是此交換的常用的詞彙。

 ![原始檔控制架構圖表](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")顯示互動 VS 和原始檔控制外掛程式架構圖

 架構圖表所示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]shell 中，標示為 VS shell，在圖表中，裝載使用者的工作專案和相關聯的元件，例如 [編輯器] 和方案總管。 原始檔控制配接器套件會處理 IDE 與原始檔控制外掛程式之間的互動。 原始檔控制配接器套件會提供它自己的原始檔控制 UI。 它是使用者互動才能起始，並定義的原始檔控制作業範圍的最上層 UI。

 原始檔控制外掛程式可以有它自己的 UI，如圖所示，可能會包含兩個部分。 標示為 「 廠商 UI 」 的方塊代表您，作為原始檔控制外掛程式建立者，提供的自訂使用者介面項目。 當使用者叫用的進階的原始檔控制作業，這些會顯示直接由原始檔控制外掛程式。 標記為 「 協助程式 UI 」 的方塊是一份原始檔控制外掛程式 UI 功能，以間接方式叫用透過 IDE。 原始檔控制外掛程式會將 UI 相關的訊息傳遞至 IDE 中透過 IDE 所提供的特殊回呼函式。 協助程式 UI 有助於更緊密的整合和 IDE (通常透過使用的**進階**按鈕)，並提供更一致的使用者體驗。

 原始檔控制外掛程式不能變更[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層，因此，原始檔控制配接器套件或來源控制 IDE 所提供的 UI。 它必須使透過使用者參與的整合式體驗的各種原始檔控制外掛程式 API 函式實作所提供的彈性最大的使用。 原始檔控制外掛程式 API 文件的參考章節包含一些進階原始檔控制外掛程式功能的資訊。 若要利用這些功能，原始檔控制外掛程式必須在初始化期間，宣告其進階的功能，可在 IDE，而且必須實作每項功能的特定進階函式。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)
- [字彙](../../extensibility/source-control-plug-in-glossary.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)