---
title: 運算式賦值器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a477aaceb57e6ccd2eb5125fcf9d8af9be59472b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738684"
---
# <a name="expression-evaluator"></a>運算式評估工具
表達式賦值器 (EE) 檢查語言的語法,以在運行時解析和評估變數和表達式,從而允許使用者在 IDE 處於中斷模式時查看它們。

## <a name="use-expression-evaluators"></a>使用運算式賦值器
 使用[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法建立表示式,如下所示:

1. 除錯引擎 (DE) 實現[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。

2. 調試包從[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)`IDebugExpressionContext2`介面獲取 對象,然後`IDebugStackFrame2::ParseText`調用它上 的方法以獲取[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件。

3. 調試包調用[評估同步](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)方法或[評估Async](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)方法來獲取表達式的值。 `IDebugExpression2::EvaluateAsync`從命令/立即窗口調用。 所有其他 UI`IDebugExpression2::EvaluateSync`元件 呼叫 。

4. 運算式計算的結果是[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件,它包含表達式計算結果的名稱、類型和值。

   在運算式計算期間,EE 需要來自符號提供程式元件的資訊。 符號提供程式提供用於標識和理解解析表達式的符號資訊。

   非同步運算完成後,DE 將透過工作階段除錯管理員 (SDM) 傳送非同步事件,通知 IDE 運算式計算已完成。 然後,從調用`IDebugExpression2::EvaluateSync`方法返回評估結果。

## <a name="implementation-notes"></a>實作附註
 調試[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]引擎希望使用通用語言運行時 (CLR) 介面與運算式賦值器進行對話。 因此,與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]調試引擎配合的運算式賦值器必須支援 CLR(可在 debugref.doc 中找到所有 CLR 調試介面的完整清單,[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]該清單是 中的一部分)。

## <a name="see-also"></a>另請參閱
- [除錯器元件](../../extensibility/debugger/debugger-components.md)
