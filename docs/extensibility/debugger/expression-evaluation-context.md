---
title: 運算運算上下文 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e939a4fa5f4673e2f701206c96599c54bc0c3b51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738744"
---
# <a name="expression-evaluation-context"></a>運算式運算內容
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]除錯中,**表示式計算內容 :**

- 表示表達式計算的上下文。 通常,計算上下文對應於計算變數、參數、函數和方法的詞法範圍。 例如,與堆疊框架關聯的表達式計算上下文將提供用於評估局部變數、方法參數和類成員(如果適用)的上下文。

- 當程式在斷點停止時存在。 表達式本身是一個數據結構,表示可準備在給定上下文中綁定和評估的解析表達式。

     有關詳細資訊,將使用[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法建立運算式。 計算運算式時,它生成一個可列印的字串,其中包含變數或參數的名稱和類型及其值。 此字串顯示在「監視」視窗或 IDE 的「局部變數」視窗中。

     給定`BSTR`和[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面,調試引擎 (DE) 可以透過分析運算式創建[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面。 給定介面`IDebugExpression2`,DE 可以通過同步或非同步運算式計算獲取值。 此值以及變數或參數的名稱和類型將發送到 IDE 進行顯示。

## <a name="see-also"></a>另請參閱
- [運算式評估介面](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [除錯器上下文](../../extensibility/debugger/debugger-contexts.md)
