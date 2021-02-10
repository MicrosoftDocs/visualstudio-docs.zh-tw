---
title: 執行型別視覺化器和自訂檢視器 |Microsoft Docs
description: 瞭解如何執行型別視覺化程式和自訂檢視器，讓使用者以比數位傾印更有意義的方式來查看資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8cf456dca27a45a2674f7138a6c0b21b12750c81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945964"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>執行型別視覺化和自訂檢視器
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 型別視覺化程式和自訂檢視器可讓使用者以比簡單十六進位的數位傾印更有意義的方式，來查看特定類型的資料。 運算式評估工具 (EE) 可以將自訂檢視器與特定類型的資料或變數產生關聯。 這些自訂檢視器是由 EE 所執行。 EE 也可以支援外部類型的視覺化檢視，這可能來自另一個協力廠商或甚至是終端使用者。

## <a name="discussion"></a>討論

### <a name="type-visualizers"></a>型別視覺化
 Visual Studio 會要求在 [監看式] 視窗中顯示每個物件的視覺化類型清單和自訂檢視器。 運算式評估工具 (EE) 為想要支援型別視覺化程式和自訂檢視器的每個類型，提供這類清單。 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)和[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)的呼叫會啟動存取型別視覺化程式和自訂檢視器的整個程式 (請參閱[視覺化和查看資料](../../extensibility/debugger/visualizing-and-viewing-data.md)，以取得呼叫順序) 的詳細資料。

### <a name="custom-viewers"></a>自訂檢視器
 自訂檢視器會在特定資料類型的 EE 中執行，並以 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 介面表示。 自訂檢視器並不像型別視覺化一樣有彈性，因為它只能在執行特定自訂檢視器的 EE 執行時使用。 執行自訂檢視器比實作為視覺化型別支援的程式更簡單。 不過，支援的型別視覺化可提供最大的彈性給終端使用者，以將其資料視覺化。 這項討論的其餘部分只考慮視覺化型別。

## <a name="interfaces"></a>介面
 EE 會執行下列介面來支援型別視覺化程式，Visual Studio 使用這些介面：

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE 會使用下列介面來支援型別視覺化：

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>另請參閱
- [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [視覺化和查看資料](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
