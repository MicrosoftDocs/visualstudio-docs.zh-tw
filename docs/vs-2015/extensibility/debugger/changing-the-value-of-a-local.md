---
title: 變更區域變數的值 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 166b4d22ec24f3137044ab19255abb15b109fbe0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807214"
---
# <a name="changing-the-value-of-a-local"></a>變更區域變數的值
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 值欄位中輸入新值時**區域變數** 視窗中，偵錯封裝會將字串傳遞，因為運算式評估工具 (EE) 型別。 EE 會評估此字串可以包含簡單的值或運算式，並將產生的值儲存在相關聯的本機。  
  
 這是變更區域變數的值的程序的概觀：  
  
1. 使用者輸入新值之後，Visual Studio 會呼叫[SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)上[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)本機與相關聯的物件。  
  
2. `IDebugProperty2::SetValueAsString` 會執行下列工作：  
  
   1.  會評估要產生值的字串。  
  
   2.  繫結相關聯[IDebugField](../../extensibility/debugger/reference/idebugfield.md)物件取得[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)物件。  
  
   3.  將值轉換成一系列的位元組。  
  
   4.  呼叫[SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md)將放入記憶體的值的位元組，因此正在偵錯程式可以存取它們。  
  
3. Visual Studio 會重新整理**區域變數**顯示 (請參閱[顯示區域變數](../../extensibility/debugger/displaying-locals.md)如需詳細資訊)。  
  
   此程序也會變更變數的值**監看式**視窗，但是它`IDebugProperty2`而非區域變數的值相關聯的物件`IDebugProperty2`本機與相關聯的物件它本身。  
  
## <a name="in-this-section"></a>本節內容  
 [變更值的範例實作](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 若要逐步執行變更值的程序使用 MyCEE 範例。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [顯示區域變數](../../extensibility/debugger/displaying-locals.md)

