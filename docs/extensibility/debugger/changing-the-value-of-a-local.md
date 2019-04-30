---
title: 變更區域變數的值 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5a6854911735c5bbc004a91c86d5d16305a928b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409909"
---
# <a name="change-the-value-of-a-local"></a>變更區域變數的值
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 值欄位中輸入新值時**區域變數** 視窗中，偵錯封裝會將字串傳遞，因為運算式評估工具 (EE) 型別。 EE 會評估此字串可以包含簡單的值或運算式，並將產生的值儲存在相關聯的本機。

 這是變更區域變數的值的程序的概觀：

1. 使用者輸入新值之後，Visual Studio 會呼叫[SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)上[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)本機與相關聯的物件。

2. `IDebugProperty2::SetValueAsString` 會執行下列工作：

   1. 會評估要產生值的字串。

   2. 繫結相關聯[IDebugField](../../extensibility/debugger/reference/idebugfield.md)物件取得[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)物件。

   3. 將值轉換成一系列的位元組。

   4. 呼叫[SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md)將放入記憶體的值的位元組，因此正在偵錯程式可以存取它們。

3. Visual Studio 會重新整理**區域變數**顯示 (請參閱[顯示區域變數](../../extensibility/debugger/displaying-locals.md)如需詳細資訊)。

   此程序也會變更變數的值**監看式**視窗中，除非它是`IDebugProperty2`而非區域變數的值相關聯的物件`IDebugProperty2`本機與相關聯的物件它本身。

## <a name="in-this-section"></a>本節內容
 [變更值的範例實作](../../extensibility/debugger/sample-implementation-of-changing-values.md)使用 MyCEE 範例來逐步執行變更值的程序。

## <a name="see-also"></a>另請參閱
- [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [顯示區域變數](../../extensibility/debugger/displaying-locals.md)