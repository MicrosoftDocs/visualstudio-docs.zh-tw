---
title: 區域變數的範例執行 |Microsoft Docs
description: 瞭解 Visual Studio 如何從本文的運算式評估工具取得方法的區域變數。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: aad77c9b9481ed6ae32c66260b1e3ef2a662c836
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847633"
---
# <a name="sample-implementation-of-locals"></a>區域變數的範例執行
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 以下概述 Visual Studio 如何從運算式評估工具 (EE) 取得方法的區域變數：

1. Visual Studio 會呼叫 debug engine 的 (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 來取得 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 物件，該物件代表堆疊框架的所有屬性，包括區域變數。

2. `IDebugStackFrame2::GetDebugProperty` 呼叫 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 來取得物件，該物件會描述中斷點發生的方法。 DE 會提供符號提供者 ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)) 、位址 ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) 以及系結器 ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)) 。

3. `IDebugExpressionEvaluator::GetMethodProperty` 使用提供的物件呼叫 [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) ， `IDebugAddress` 以取得代表包含指定位址之方法的 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 。

4. 此 `IDebugContainerField` 介面會針對 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 介面進行查詢。 這個介面可讓您存取方法的區域變數。

5. `IDebugExpressionEvaluator::GetMethodProperty` 具現化類別 (`CFieldProperty` 在執行介面的範例) 中呼叫， `IDebugProperty2` 以代表方法的區域變數。 `IDebugMethodField`物件 `CFieldProperty` 與 `IDebugSymbolProvider` 、 `IDebugAddress` 和物件放在這個物件中 `IDebugBinder` 。

6. `CFieldProperty`初始化物件時，會在物件上呼叫[GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) ， `IDebugMethodField` 以取得包含方法本身所有可顯示資訊的[FIELD_INFO](../../extensibility/debugger/reference/field-info.md)結構。

7. `IDebugExpressionEvaluator::GetMethodProperty``CFieldProperty`以物件形式傳回物件 `IDebugProperty2` 。

8. Visual Studio 會[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)在傳回的 `IDebugProperty2` 物件上使用篩選呼叫 EnumChildren，此篩選器會傳回 `guidFilterLocalsPlusArgs` 包含方法區域變數的[IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件。 呼叫 [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) 和 [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)即會填入此列舉。

9. Visual Studio 呼叫 [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) 來取得每個本機的 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 結構。 此結構包含 `IDebugProperty2` 區域介面的指標。

10. Visual Studio 會呼叫每個本機的 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) ，以取得本機的名稱、值和類型。 這項資訊會顯示在 [ **區域變數** ] 視窗中。

## <a name="in-this-section"></a>本節內容
 [執行 GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) 描述 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)的執行。

 [列舉區域變數](../../extensibility/debugger/enumerating-locals.md) 描述 debug engine (DE) 如何進行呼叫，以列舉區域變數或引數。

 [取得區域屬性](../../extensibility/debugger/getting-local-properties.md) 描述 DE 如何進行呼叫，以取得一或多個區域變數的名稱、類型和值。

 [取得區域值](../../extensibility/debugger/getting-local-values.md) 討論取得本機的值，這需要評估內容所提供之系結器物件的服務。

 [評估區域變數](../../extensibility/debugger/evaluating-locals.md) 說明如何評估區域變數。

## <a name="related-sections"></a>相關章節
 [評估內容](../../extensibility/debugger/evaluation-context.md) 提供當 DE 呼叫運算式評估工具 (EE) 時傳遞的引數。

 [MyCEE 範例](/previous-versions/) 示範建立 MyC 語言的運算式評估工具的一個實方法。

## <a name="see-also"></a>另請參閱
- [顯示區域變數](../../extensibility/debugger/displaying-locals.md)