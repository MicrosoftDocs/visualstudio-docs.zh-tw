---
title: "IDebugAlias |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias
helpviewer_keywords: IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 128dc9001faba06b1c95c5ebc364f319891ce409
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表示變數的數值別名。 別名是變數只是不同的名稱。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 運算式評估工具 (EE) 會實作這個介面來支援數值的別名變數。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)建立特定物件的別名。 若要搜尋的別名，請使用[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)或[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下列方法定義中`IDebugAlias`介面。  
  
|方法|說明|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|取得這個別名所參考的物件。|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|取得別名名稱。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|擷取`ICorDebugValue`介面可存取 managed 程式碼 （僅限 managed 程式碼） 此物件相關的資訊。|  
|[處置](../../../extensibility/debugger/reference/idebugalias-dispose.md)|將此標示別名為不再使用。|  
  
## <a name="remarks"></a>備註  
 別名是後面接著 # 字元，例如 &#1001; 字串形式的十進位數字。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)