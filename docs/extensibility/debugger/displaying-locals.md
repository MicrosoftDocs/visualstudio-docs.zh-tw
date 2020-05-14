---
title: 顯示本地變數 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d44b276aeb9c6acb0ef34cc186662d49246de7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738939"
---
# <a name="display-locals"></a>顯示區域變數
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 執行始終發生在方法的上下文中,也稱為包含方法或當前方法。 當執行暫停時,Visual Studio 調用調試引擎 (DE) 來獲取本地變數和參數的清單,統稱為方法的局部變數。 可視化工作室在 **「局部變數」** 視窗中顯示這些局部變數及其值。

 要顯示局部變數,DE 呼叫屬於 EE 的[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)方法,並給它一個評估上下文,即符號提供程式 (SP)、當前執行位址和活頁夾物件。 有關詳細資訊,請參閱[評估上下文](../../extensibility/debugger/evaluation-context.md)。 如果呼叫成功,`IDebugExpressionEvaluator::GetMethodProperty`該方法將傳回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件,該物件表示包含當前執行位址的方法。

 DE 調用[Enum 兒童](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)獲取[IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件,該物件經過篩選以僅返回局部變數並枚舉以生成[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)結構的清單。 每個結構都包含本地的名稱、類型和值。 類型和值儲存為格式化字串,適合顯示。 名稱、類型和值通常一起顯示在 **「局部變數」** 視窗的一行中。

> [!NOTE]
> **"快速監視**"和 **"監視"** 視窗還顯示名稱、值和類型格式相同的變數。 但是,這些值是通過調用[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)而不是`IDebugProperty2::EnumChildren`獲得。

## <a name="in-this-section"></a>本節內容
 [部份變數的樣本實作](../../extensibility/debugger/sample-implementation-of-locals.md)使用示例逐步完成本地變數的實現過程。

## <a name="related-sections"></a>相關章節
 [評估上下文](../../extensibility/debugger/evaluation-context.md)說明當調試引擎 (DE) 調用表示式賦值器 (EE) 時,它將傳遞三個參數。

## <a name="see-also"></a>另請參閱
 [編寫 CLR 表示式賦值器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
