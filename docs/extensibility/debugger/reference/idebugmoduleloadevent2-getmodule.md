---
title: IDebugModuleLoadEvent2::GetModule |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6188ba6842a922fa0758a21c0f496f50889f8b3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
取得模組，正在載入或卸載。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pModule`  
 [out]傳回[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)物件，表示已載入或卸載模組。  
  
 `pbstrDebugMessage`  
 [in、 out]傳回描述此事件是選擇性的訊息。 如果這個參數是 null 值，會不要求任何訊息。  
  
 `pbLoad`  
 [in、 out]非零 (`TRUE`) 如果模組已載入與零 (`FALSE`) 如果正在卸載模組。 如果這個參數是 null 值，會不要求任何狀態。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)