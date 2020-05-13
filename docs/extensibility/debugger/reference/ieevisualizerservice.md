---
title: IEE可視化服務 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40d21dcc9b1da0e1e2250adcfad59b3ef46a2113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717936"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面實現關鍵方法,為[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)和[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面提供功能。

## <a name="syntax"></a>語法

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 Visual Studio 實現此介面,以允許運算式賦值器 (EE) 支援類型可視化器。

## <a name="notes-for-callers"></a>通話備註
 EE 呼叫[CreateVisualizer 服務](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)以取得此介面,作為其對類型可視化器的支援的一部分。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法

|方法|描述|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|檢索此服務知道的自定義查看器數。|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|檢索自定義檢視器的清單。|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|返回屬性的代理物件。|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|檢索要為指定屬性或欄位顯示的值字串數。|

## <a name="remarks"></a>備註
 IDE 使用[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面來確定是否有任何自定義查看器或類型可視化器的屬性。 通過創建視覺化工具服務(使用[CreateVisualizer 服務](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)),EE`IDebugProperty3`可以為和[IPropertyProxyEESide(](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)支援查看和更改屬性的值)介面提供功能,從而支援類型可視化器。

 如果 EE 具有自身實現的自訂檢視器,則 EE`CLSID`可以將這些 自訂檢視器的 s 追加到[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)返回的清單末尾。 這允許 EE 同時支援類型可視化器及其自己的自定義查看器。 只需確保[GetCustomViewerCount 反映](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)任何自定義查看器的添加。

 有關可視化工具與查看器之間的差異的討論,請參閱["類型可視化器"和"自定義檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)"。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
