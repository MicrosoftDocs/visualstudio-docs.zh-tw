---
title: "原始檔控制外掛程式架構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0cde4ca360aa0059abcbe0b64d63b4a94e85d78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-in-architecture"></a>原始檔控制外掛程式架構
您可以加入至原始檔控制支援[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由實作和附加原始檔控制外掛程式整合式的開發環境 (IDE)。 IDE 會連接到原始檔控制外掛程式透過定義完善的原始檔控制外掛程式 API。 IDE 會藉由提供使用者介面 (UI)，其中包含的工具列和功能表命令顯示原始檔控制系統的版本控制功能。 原始檔控制外掛程式實作原始檔控制功能。  
  
## <a name="source-control-plug-in-resources"></a>原始檔控制外掛程式資源  
 原始檔控制外掛程式提供有助於建立及連接您的版本控制應用程式的資源[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。 原始檔控制外掛程式包含必須實作原始檔控制外掛程式，讓它可以整合到應用程式開發介面規格[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。 它也包含實作的基本架構的原始檔控制外掛程式示範實作必要的功能與原始檔控制外掛程式 API 相容的程式碼範例 （寫在 c + +）。  
  
 原始檔控制外掛程式 API 規格可讓您充分利用您選擇的任何原始檔控制系統，如果您建立一組必要的函式，根據原始檔控制外掛程式 API 實作了原始檔控制 DLL。  
  
## <a name="components"></a>元件  
 在圖表中的原始檔控制配接器套件是將原始檔控制作業至原始檔控制外掛程式所支援的函式呼叫的使用者的要求轉譯在 IDE 的元件。 此選項，IDE 和原始檔控制外掛程式必須有一個有效的對話方塊，其中 IDE 與外掛程式之間來回傳遞資訊。 進行這個對話，它們都必須宣告相同的語言。 這份文件中所述的原始檔控制外掛程式 API 是此交換的通用詞彙。  
  
 ![原始檔控制架構圖表](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")  
顯示互動 VS 和原始檔控制外掛程式架構圖  
  
 架構在圖表中所示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層，作為 VS shell 在圖表中，標示為裝載使用者的工作專案和相關聯的元件，例如 [編輯器] 和 [方案總管]。 原始檔控制配接器封裝處理 IDE 與原始檔控制外掛程式之間的互動。 原始檔控制配接器套件提供它自己的原始檔控制 UI。 它是使用者互動才能起始，並定義的原始檔控制作業範圍的最上層 UI。  
  
 原始檔控制外掛程式可以有它自己的 UI，可能會包含兩個部分，如下圖所示。 標示為 「 廠商 UI 」 方塊都代表您，做為原始檔控制外掛程式建立者提供的自訂使用者介面項目。 當使用者叫用的進階的原始檔控制作業，這些會顯示直接由原始檔控制外掛程式。 標記為 「 協助程式 UI 」 的方塊會是原始檔控制外掛程式 UI 功能間接透過 IDE 叫用的一組。 原始檔控制外掛程式會將 UI 相關訊息傳遞至由 IDE 所提供的特殊的回呼函式透過 IDE。 協助程式 UI 有助於更緊密的整合和 IDE (通常透過使用的**進階**按鈕)，因此會提供更一致的使用者體驗。  
  
 原始檔控制外掛程式無法進行變更來[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層，因此，原始檔控制配接器套件或來源控制 IDE 所提供的 UI。 它必須進行透過整合的經驗給終端使用者促成各種原始檔控制外掛程式 API 函式實作所提供的彈性最大的使用。 原始檔控制外掛程式 API 文件的參考章節包含一些進階原始檔控制外掛程式功能的資訊。 若要利用這些功能，原始檔控制外掛程式必須在初始化期間，宣告其進階的功能加入 IDE 和它必須實作每項功能的特定進階函式。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)   
 [名詞解釋](../../extensibility/source-control-plug-in-glossary.md)   
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)