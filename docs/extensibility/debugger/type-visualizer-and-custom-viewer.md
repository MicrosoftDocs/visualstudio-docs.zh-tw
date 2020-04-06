---
title: 類型視覺化器和自訂檢視器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712471"
---
# <a name="type-visualizer-and-custom-viewer"></a>類型視覺化器和自訂檢視器
類型視覺化工具是以特定格式顯示資料片段的元件。 格式完全取決於實現可視化工具的人員,無論是最終用戶還是可視化工具的第三方供應商。

 自定義查看器是自定義表達式賦值器的一部分,該計算機以特定格式顯示數據片段。 此格式完全由自定義檢視器的實現者決定,這意味著該格式由表達式賦值器 (EE) 的實現者決定。

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>支援表示式賦值器中的類型視覺化器
 EE 支援一組可視化工具可存取的介面,支援類型可視化器[:IEE 可視化服務](../../extensibility/debugger/reference/ieevisualizerservice.md)介面和[IEE 視覺化資料提供程式](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)等介面。 但是,EE 不負責實現類型可視化工具本身:EE 僅允許外部可視化工具訪問其類型資訊。 此類可視化工具可能隨 EE 一起運輸,並安裝在 Visual Studio 的相應位置,由其他第三方供應商甚至最終使用者提供。

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>支援表示式賦值器中的自訂檢視器
 EE 還可以支援自訂檢視器,其中 EE 本身提供用於查看數據類型的代碼。 自定義查看器實現[IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)介面,該介面處理以所需的任何格式顯示數據的所有職責;查看器可以完全控制顯示,甚至可以修改數據。 產品發貨時,EE 提供的任何自定義查看器都隨 EE 一起使用。

## <a name="see-also"></a>另請參閱
- [除錯器元件](../../extensibility/debugger/debugger-components.md)
- [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)
- [偵錯引擎](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
