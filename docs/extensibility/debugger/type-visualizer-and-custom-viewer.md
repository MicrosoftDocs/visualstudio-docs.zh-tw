---
title: 類型視覺化檢視和自訂檢視器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5cf2cc9c8f89ed0ecc7935f9afa8e096f05a840
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276490"
---
# <a name="type-visualizer-and-custom-viewer"></a>類型視覺化檢視和自訂檢視器
類型視覺化檢視是顯示某份資料以特定格式的元件。 格式為全部都是最多由誰實作視覺化檢視，是使用者或第三方供應商的視覺化檢視。  
  
 自訂檢視器屬於某份資料會以特定格式顯示自訂的運算式評估工具。 此格式會完全由實作者的自訂檢視器中，這表示的格式是由實作者的運算式評估工具 (EE)。  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>類型視覺化檢視中的運算式評估工具支援  
 EE 支援一組介面的視覺化檢視必須能夠支援類型視覺化檢視： 例如介面[IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)並[IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)。 不過，概不負責實作類型視覺化檢視本身 EE: EE 只允許外部的視覺化檢視其類型資訊的存取權。 這類的視覺化檢視可能會隨附 EE，且安裝在另一個第三方廠商，或甚至是由使用者提供的 Visual Studio 中的適當位置。  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>自訂檢視器中的運算式評估工具支援  
 EE 也可以支援順序 EE 本身提供檢視的資料類型的程式碼的自訂檢視器。 自訂檢視器會實作[IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)想要使用介面，用來處理的任何格式顯示資料的所有職務; 檢視器可顯示的完整控制，並甚至可以讓修改的資料。 EE 所提供的任何自訂檢視器隨附 EE 產品出貨時。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)