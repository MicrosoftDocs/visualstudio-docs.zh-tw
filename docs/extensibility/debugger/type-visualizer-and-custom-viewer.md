---
title: "輸入視覺化檢視和自訂檢視器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80798887beee6116b3a93b5d8ec86b14269b5475
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="type-visualizer-and-custom-viewer"></a>類型的視覺化檢視和自訂檢視器
類型的視覺化檢視是非常特定的格式顯示一段資料的元件。 這種格式是完全由實作者的視覺化檢視，是使用者或協力廠商供應商的視覺化檢視。  
  
 自訂檢視器是以非常特定的格式顯示資料片段的自訂運算式評估工具的一部分。 這種格式是完全由實作者的自訂檢視器中，這表示的格式是由實作者的運算式評估工具 (EE)。  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>支援的運算式評估工具中的類型視覺化檢視  
 EE 可支援一組介面的視覺化檢視必須能夠支援類型的視覺化檢視： 這類介面[IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)和[IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)。 不過請注意，EE 不負責實作本身的類型視覺化檢視： EE 只允許外部的視覺化檢視其類型資訊的存取權。 這類視覺化檢視可能會與 EE 一起出貨並安裝在另一個協力廠商或甚至是由使用者提供的 Visual Studio 中的適當位置。  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>自訂檢視器中的運算式評估工具支援  
 EE 也支援自訂檢視器中 EE 本身提供的程式碼檢視的資料類型。 自訂檢視器會實作[IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)想要使用介面，用來處理的任何格式顯示資料的所有責任; 檢視器顯示的完整控制權，而且甚至可以允許資料修改。 EE 所提供的任何自訂檢視器隨附 EE 時隨附產品。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)