---
title: 變更本地值 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98e40e4b6ea10bb6ff1242f23f1b6dd83ce0c0cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739144"
---
# <a name="change-the-value-of-a-local"></a>變更本地值
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 在 **「局部變數」** 視窗的值欄位中鍵入新值時,調試包會將字串(鍵入)傳遞給運算式賦值器 (EE)。 EE 計算此字串,該字串可以包含簡單值或運算式,並將結果值存儲在關聯的本地中。

 這是更改本地值的過程的概述:

1. 使用者輸入新值後,Visual Studio 會在與本地關聯的[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件上調用[SetValueAsString。](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)

2. `IDebugProperty2::SetValueAsString` 會執行下列工作：

   1. 評估要生成值的字串。

   2. 繫結關係的[IDebugField](../../extensibility/debugger/reference/idebugfield.md)物件以取得[IDebugObject 物件](../../extensibility/debugger/reference/idebugobject.md)。

   3. 將值轉換為一系列位元組。

   4. 調用[SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md)將值的位元組放入記憶體中,以便正在調試的程式可以訪問它們。

3. 可視化工作室刷新 **「局部變數」** 顯示(有關詳細資訊[,請參閱顯示局部變數](../../extensibility/debugger/displaying-locals.md))。

   此過程還用於更改**Watch**視窗中變數的值,只不過它是與所使用的局部變數的值關聯的`IDebugProperty2`物件,而不是與本地本身關聯`IDebugProperty2`的 物件。

## <a name="in-this-section"></a>本節內容
 [變更值的範例](../../extensibility/debugger/sample-implementation-of-changing-values.md)使用 MyCEE 範例逐步完成更改值的過程。

## <a name="see-also"></a>另請參閱
- [編寫 CLR 表示式賦值器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [顯示本地變數](../../extensibility/debugger/displaying-locals.md)
