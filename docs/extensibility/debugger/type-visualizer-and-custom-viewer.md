---
title: 型別視覺化程式和自訂檢視器 |Microsoft Docs
description: 深入瞭解型別視覺化元件和自訂檢視器，其會以特定格式顯示資料，以及兩者之間的差異。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 869f0997ee166b9b7eb29c1a313854437d670ee4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057815"
---
# <a name="type-visualizer-and-custom-viewer"></a>型別視覺化器和自訂檢視器
型別視覺化程式是以特定格式顯示一段資料的元件。 此格式完全由執行視覺化程式的人員所組成，也就是使用者或協力廠商的視覺化檢視。

 自訂檢視器是自訂表格達式評估工具的一部分，會以特定格式顯示資料片段。 這種格式完全由自訂檢視器的實作者所組成，這表示格式取決於運算式評估工具的實作者 (EE) 。

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>支援運算式評估工具中的型別視覺化
 EE 支援型別視覺化器，支援視覺化程式可存取的一組介面：介面，例如 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) 和 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)。 不過，EE 不負責實作為型別視覺化程式本身： EE 只允許外部的視覺化程式存取其型別資訊。 這類的視覺化程式可能隨附于 EE，並安裝在 Visual Studio 中的適當位置，也就是由其他協力廠商廠商或使用者（甚至是使用者）所提供。

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>運算式評估工具中自訂檢視器的支援
 EE 也可以支援自訂檢視器，讓 EE 本身提供用來查看資料類型的程式碼。 自訂檢視器會執行 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 介面，此介面會處理以所需的任何格式顯示資料的所有責任;檢視器可以完全掌控顯示器，甚至可以讓資料進行修改。 當產品出貨時，EE 提供的任何自訂檢視器都會隨附 EE。

## <a name="see-also"></a>另請參閱
- [偵錯工具元件](../../extensibility/debugger/debugger-components.md)
- [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)
- [Debug 引擎](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
