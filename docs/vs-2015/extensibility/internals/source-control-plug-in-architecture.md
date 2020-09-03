---
title: 原始檔控制外掛程式架構 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 370f88ce4d8fc372ce31e1e85e88d5379f4e1ba5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183392"
---
# <a name="source-control-plug-in-architecture"></a>原始檔控制外掛程式架構
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您可以藉由執行和附加原始檔控制外掛程式，將原始檔控制支援新增至 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 整合式開發環境 (IDE) 。 IDE 會透過定義完善的原始檔控制外掛程式 API 連接到原始檔控制外掛程式。 IDE 藉由提供使用者介面 (UI) ，其中包含工具列和功能表命令，以公開原始檔控制系統的版本控制功能。 原始檔控制外掛程式會執行原始檔控制功能。  
  
## <a name="source-control-plug-in-resources"></a>原始檔控制外掛程式資源  
 原始檔控制外掛程式提供的資源可協助您建立版本控制應用程式，並將其連接到 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE。 原始檔控制外掛程式包含的 API 規格必須由原始檔控制外掛程式所執行，才能整合到 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 中。 它也包含以 c + +) 撰寫的程式碼範例，此 (範例會執行基本架構原始檔控制外掛程式，以示範符合原始檔控制外掛程式 API 規範的基本函式的執行。  
  
 如果您建立原始檔控制 DLL，並根據原始檔控制外掛程式 API 來執行所需的函式集合，則原始檔控制外掛程式 API 規格可讓您利用您選擇的任何原始檔控制系統。  
  
## <a name="components"></a>元件  
 圖中的原始檔控制介面卡封裝是 IDE 的元件，會將使用者對原始檔控制作業的要求轉譯為原始檔控制外掛程式所支援的函式呼叫。 若要這樣做，IDE 和原始檔控制外掛程式必須具有可在 IDE 與外掛程式之間來回傳遞資訊的有效對話。 若要讓此對話發生，兩者都必須使用相同的語言。 本檔中概述的原始檔控制外掛程式 API 是此交換的常見詞彙。  
  
 ![原始程式碼控制架構圖表](../../extensibility/internals/media/vs-sccsdk-plug-in-arch.gif "vs_sccsdk_plug_in_arch")  
顯示 VS 和原始檔控制外掛程式之間互動的架構圖表  
  
 如架構圖所示，在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 圖表中標示為 VS shell 的 shell 會裝載使用者的工作專案和相關聯的元件，例如編輯器和方案總管。 原始檔控制介面卡封裝會處理 IDE 與原始檔控制外掛程式之間的互動。 原始檔控制介面卡套件會提供自己的原始檔控制 UI。 它是使用者與之互動的最上層 UI，以便起始和定義原始檔控制作業的範圍。  
  
 原始檔控制外掛程式可以有自己的 UI，其中可能包含兩個部分，如圖所示。 標示為「廠商 UI」的方塊表示自訂使用者介面元素，您可以做為原始檔控制外掛程式建立者提供。 當使用者叫用 advanced 原始檔控制作業時，原始檔控制外掛程式會直接顯示這些控制項。 標示為「Helper UI」的方塊是一組透過 IDE 間接叫用的原始檔控制外掛程式 UI 功能。 原始檔控制外掛程式會透過 IDE 所提供的特殊回呼函式，將 UI 相關訊息傳遞至 IDE。 協助程式 UI 可讓您更順暢地整合 IDE (通常會透過使用 [ **Advanced** ] 按鈕) ，因此可提供更一致的終端使用者體驗。  
  
 原始檔控制外掛程式無法對 shell 進行變更，因此無法變更 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 至 IDE 所提供的原始檔控制介面卡封裝或原始檔控制 UI。 它必須充分利用透過執行各種原始檔控制外掛程式 API 函式所提供的彈性，以提供給使用者的整合式體驗。 原始檔控制外掛程式 API 檔的參考區段包含一些 advanced Source control 外掛程式功能的資訊。 若要利用這些功能，原始檔控制外掛程式必須在初始化期間將其先進的功能宣告為 IDE，而且必須針對每個功能執行特定的 advanced 函數。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)   
 [詞彙](../../extensibility/source-control-plug-in-glossary.md)   
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
