---
title: 變更區域變數的值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 516725510c5f5bc7baa8bd96d3f7fb969b6589e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838795"
---
# <a name="changing-the-value-of-a-local"></a>變更區域變數的值
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 在 [ **區域變數** ] 視窗的 [值] 欄位中輸入新值時，debug 封裝會將字串（如輸入）傳遞給運算式評估工具 (EE) 。 EE 會評估這個字串，其中可以包含簡單值或運算式，並將產生的值儲存在相關聯的本機中。  
  
 這是變更本機值的程式總覽：  
  
1. 在使用者輸入新的值之後，Visual Studio 會在與本機相關聯的[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件上呼叫[SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 。  
  
2. `IDebugProperty2::SetValueAsString` 會執行下列工作：  
  
   1. 評估字串以產生值。  
  
   2. 系結相關聯的 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 物件，以取得 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 物件。  
  
   3. 將值轉換成一連串的位元組。  
  
   4. 呼叫 [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) 將值的位元組放入記憶體中，讓正在進行調試的程式可以存取它們。  
  
3. Visual Studio 會重新整理 [ **區域變數** ] 顯示 (如需詳細資料，請參閱 [顯示區域變數](../../extensibility/debugger/displaying-locals.md)) 。  
  
   此程式也用來變更 [ **監看** 式] 視窗中的變數值，但它是 `IDebugProperty2` 與使用的本機值相關聯的物件，而不是 `IDebugProperty2` 與本機本身相關聯的物件。  
  
## <a name="in-this-section"></a>本節內容  
 [變更值的範例實作](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 使用 MyCEE 範例逐步執行變更值的程式。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [顯示區域變數](../../extensibility/debugger/displaying-locals.md)
