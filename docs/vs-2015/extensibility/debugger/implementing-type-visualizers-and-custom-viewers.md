---
title: 實作類型視覺化檢視和自訂檢視器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f74dcee5e72221271e2756af37d3d9284841db5f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944636"
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>實作類型視覺化檢視和自訂檢視器
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 類型視覺化檢視和自訂檢視器可讓使用者更有意義，比簡單的十六進位傾印的數字的方式檢視特定類型的資料。 運算式評估工具 (EE) 可以將自訂檢視器與特定類型的變數或資料產生關聯。 EE 實作這些自訂檢視器。 EE 也可支援外部類型視覺化檢視，可能是來自其他第三方廠商或甚至是一般使用者。  
  
## <a name="discussion"></a>討論  
  
### <a name="type-visualizers"></a>類型視覺化檢視  
 Visual Studio 會要求類型視覺化檢視和每個物件的自訂檢視器，要在監看式視窗中顯示的清單。 運算式評估工具 (EE) 提供這類它要支援類型視覺化檢視和自訂檢視器的每一個型別清單。 呼叫[GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)並[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)開始整個程序的存取類型視覺化檢視和自訂檢視器 (請參閱[視覺化及檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md)如需有關呼叫的順序)。  
  
### <a name="custom-viewers"></a>自訂檢視器  
 自訂檢視器會在特定的資料型別的 EE 中實作和都由[IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)介面。 自訂檢視器不具有彈性，類型視覺化檢視，因為實作該特定的自訂檢視器 EE 正在執行時，才會提供。 實作自訂檢視器會比實作類型視覺化檢視支援簡單的。 不過，支援類型視覺化檢視提供最大的彈性使用者他 / 她的資料視覺化。 在本文的其餘部分是有關只有類型視覺化檢視。  
  
## <a name="interfaces"></a>介面  
 EE 會實作下列介面以支援類型的視覺化檢視，以供 Visual Studio:  
  
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
  EE 會取用要支援類型視覺化檢視的下列介面：  
  
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [視覺化及檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
