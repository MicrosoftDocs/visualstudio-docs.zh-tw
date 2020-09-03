---
title: 型別視覺化程式和自訂檢視器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a85be2978abe35e91096b55fba5ec5281be25fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185319"
---
# <a name="type-visualizer-and-custom-viewer"></a>類型視覺化檢視和自訂檢視器
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

型別視覺化程式是以非常特定的格式來顯示一段資料的元件。 這種格式完全取決於視覺化檢視的實作者，也就是使用者或視覺化程式的協力廠商供應商。  
  
 自訂檢視器是自訂表格達式評估工具的一部分，會以非常特定的格式來顯示資料片段。 這種格式完全由自訂檢視器的實作者所組成，這表示格式取決於運算式評估工具的實作者 (EE) 。  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>支援運算式評估工具中的型別視覺化  
 EE 可以支援視覺化程式可存取的一組介面，藉此支援型別視覺化器：介面，例如 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) 和 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)。 不過請注意，EE 不負責實作為型別視覺化程式本身： EE 只允許外部的視覺化程式存取其型別資訊。 這類的視覺化程式可能隨附于 EE，並安裝在 Visual Studio 中的適當位置，也就是由其他協力廠商廠商或使用者（甚至是使用者）所提供。  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>運算式評估工具中自訂檢視器的支援  
 EE 也可以支援自訂檢視器，讓 EE 本身提供用來查看資料類型的程式碼。 自訂檢視器會執行 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 介面，此介面會處理以所需的任何格式顯示資料的所有責任;檢視器可以完全掌控顯示器，甚至可以允許修改資料。 當產品出貨時，EE 提供的任何自訂檢視器都會隨附 EE。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)   
 [Debug 引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
