---
title: 局部變數的樣本實施 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b70e0f9091d40ed6b5fc44934606f42ccd84b21
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713078"
---
# <a name="sample-implementation-of-locals"></a>部份變數的樣本實作
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 以下是 Visual Studio 如何從運算式賦值器 (EE) 取得方法的局部變數的概述:

1. Visual Studio 調用調試引擎的 (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)獲取[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件,該物件表示堆疊幀的所有屬性,包括局部變數。

2. `IDebugStackFrame2::GetDebugProperty`調用[GetMethod Property](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)獲取描述斷點發生方法的物件。 DE 提供符號提供者 ([IDebugSymbolProvider),](../../extensibility/debugger/reference/idebugsymbolprovider.md)位址 ([IDebugAddress)](../../extensibility/debugger/reference/idebugaddress.md)與活頁夾 ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty`使用提供`IDebugAddress`的物件調用[GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)以獲取表示包含指定位址的方法的[IDebugContainerField。](../../extensibility/debugger/reference/idebugcontainerfield.md)

4. 查詢`IDebugContainerField` [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)介面的介面。 正是這個介面提供了對方法的局部變數的訪問。

5. `IDebugExpressionEvaluator::GetMethodProperty`實例化運行`IDebugProperty2`介面以表示方法`CFieldProperty`的 局部變數的類(在示例中調用)。 物件`IDebugMethodField``CFieldProperty``IDebugSymbolProvider`與`IDebugAddress`、`IDebugBinder`物件一起放置在此物件中。

6. 初始化`CFieldProperty`物件時`IDebugMethodField`, 在物件上調用[GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md)以取得有關方法本身的所有可顯示資訊[FIELD_INFO](../../extensibility/debugger/reference/field-info.md)結構。

7. `IDebugExpressionEvaluator::GetMethodProperty`將`CFieldProperty`物件為物件`IDebugProperty2`傳回 。

8. Visual Studio 使用篩選器`IDebugProperty2`在返回 的物件上調用[Enum](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)`guidFilterLocalsPlusArgs`兒童 ,該篩選器 返回包含該方法的局部變數的[IEnum DebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件。 此枚舉通過調用[枚舉本地變數](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)和[枚舉參數](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)來填充。

9. 可視化工作室調用[下一個](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)獲取每個本地[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)結構。 此結構包含指向本地`IDebugProperty2`介面的指標。

10. Visual Studio 為每個本地呼叫[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)以獲取本地名稱、值和類型。 此資訊將顯示在 **「局部變數」** 視窗中。

## <a name="in-this-section"></a>本節內容
 [實現 GetMethod 屬性](../../extensibility/debugger/implementing-getmethodproperty.md)描述[GetMethod Property](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)的實現。

 [列舉局部變數](../../extensibility/debugger/enumerating-locals.md)描述調試引擎 (DE) 如何呼叫枚舉本地變數或參數。

 [取得本地端屬性](../../extensibility/debugger/getting-local-properties.md)描述 DE 如何呼叫以獲取一個或多個局部變數的名稱、類型和值。

 [取得本地端值](../../extensibility/debugger/getting-local-values.md)討論獲取本地值,這需要計算上下文提供的活頁夾物件的服務。

 [評估本地人](../../extensibility/debugger/evaluating-locals.md)解釋如何評估局部變數。

## <a name="related-sections"></a>相關章節
 [評估上下文](../../extensibility/debugger/evaluation-context.md)提供 DE 調用表示式賦值器 (EE) 時傳遞的參數。

 [MyCEE 樣本](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f)演示為 MyC 語言創建表達式賦值器的一種實現方法。

## <a name="see-also"></a>另請參閱
- [顯示本地變數](../../extensibility/debugger/displaying-locals.md)
