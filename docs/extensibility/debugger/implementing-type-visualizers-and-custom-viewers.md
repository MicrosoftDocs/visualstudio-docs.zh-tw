---
title: 實現類型視覺化器和自訂檢視器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ebbb5c8e27df4ae4baf2d9a9f1c3314188e2b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738502"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>實現類型視覺化器和自訂檢視器
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 類型可視化器和自定義檢視器允許使用者以比簡單的十六進位數位轉儲更有意義的方式查看特定類型的數據。 運算式賦值器 (EE) 可以將自訂檢視器與特定類型的數據或變數相關聯。 這些自定義查看器由 EE 實現。 EE 還可以支援外部類型可視化工具,這些可視化工具可能來自其他第三方供應商甚至最終使用者。

## <a name="discussion"></a>討論區

### <a name="type-visualizers"></a>類型視覺化器
 Visual Studio 要求列出要在監視視窗中顯示的每個物件的類型可視化器和自定義查看器。 運算式賦值器 (EE) 為它希望支援類型視覺化器和自訂檢視器的每種類型提供此類清單。 對[GetCustomViewer( GetCustomViewer) Count 和](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)的呼叫開始存取類型視覺化器和自訂檢視器的整個過程(有關呼叫序列的詳細資訊,請參閱[視覺化和查看資料](../../extensibility/debugger/visualizing-and-viewing-data.md))。

### <a name="custom-viewers"></a>自訂檢視器
 自定義檢視器在 EE 中為特定數據類型實現,並由[IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)介面表示。 自定義檢視器不像類型可視化器那樣靈活,因為它僅在執行該特定自定義查看器的 EE 時才可用。 實現自定義查看器比實現對類型可視化工具的支援更簡單。 但是,支持類型可視化器為最終用戶可視化其數據提供了最大的靈活性。 本討論的其餘部分僅涉及類型可視化工具。

## <a name="interfaces"></a>介面
 EE 實作以下介面以支援 Visual Studio 使用的型可視化工具:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE 使用以下介面來支援類型視覺化工具:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>另請參閱
- [編寫 CLR 表示式賦值器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [視覺化與檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
