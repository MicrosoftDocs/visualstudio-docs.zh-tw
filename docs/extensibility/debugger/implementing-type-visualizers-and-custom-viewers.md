---
title: "實作類型視覺化檢視和自訂檢視器 |Microsoft 文件"
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
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 301c0311b8398ae14b36fedca5653d607b3274c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>實作類型視覺化檢視和自訂檢視器
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 類型的視覺化檢視和自訂檢視器可讓使用者以數字的簡單十六進位傾印比更有意義的方式檢視特定類型的資料。 運算式評估工具 (EE) 可以建立自訂檢視器關聯與特定類型的變數或資料。 EE 實作這些自訂檢視器。 EE 也可以支援的其他協力廠商或一般使用者可能來自於外部類型視覺化檢視。  
  
## <a name="discussion"></a>討論  
  
### <a name="type-visualizers"></a>類型的視覺化檢視  
 Visual Studio 會要求的類型視覺化檢視，以及每個物件的自訂檢視器監看式視窗中顯示的清單。 運算式評估工具 (EE) 提供這類清單的每個它要支援類型的視覺化檢視和自訂檢視器的類型。 呼叫[GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)和[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)開始整個程序的存取類型的視覺化檢視和自訂檢視器 (請參閱[Visualizing 和檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md)的呼叫順序的詳細資訊)。  
  
### <a name="custom-viewers"></a>自訂檢視器  
 自訂檢視器會實作中特定資料型別的 EE 和都由[IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)介面。 自訂檢視器不具有彈性，類型視覺化檢視，因為它才可使用該特定自訂檢視器會實作 EE 正在執行。 實作自訂檢視器會實作類型視覺化檢視的支援比簡單的。 不過，支援類型的視覺化檢視提供最大的彈性終端使用者視覺化他或她的資料。 此討論的其餘部分是有關只有使用視覺化檢視類型。  
  
## <a name="interfaces"></a>介面  
 EE 實作下列介面以支援類型的視覺化檢視，使用 Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 EE 取用下列介面，才能支援類型的視覺化檢視：  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [視覺化及檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)