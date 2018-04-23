---
title: IDebugProgram2::EnumCodePaths |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56cc9580ec2e434066d1c0a3ce674a4111e433af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
擷取原始程式檔中指定位置之程式碼路徑的清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```csharp  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszHint`  
 [in]將游標置於下面的字**來源**或**反組譯碼**在 IDE 中的檢視。  
  
 `pStart`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，代表目前的程式碼內容。  
  
 `pFrame`  
 [in][IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)代表堆疊框架與目前中斷點相關聯的物件。  
  
 `fSource`  
 [in]非零 (`TRUE`) 如果在**來源** 檢視中，則為零 (`FALSE`) 如果在**反組譯碼**檢視。  
  
 `ppEnum`  
 [out]傳回[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)物件，其中包含的程式碼路徑清單。  
  
 `ppSafety`  
 [out]傳回[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)代表額外的程式碼內容，如果所選的程式碼路徑設定為中斷點會略過的物件。 這可能會發生在最少運算的布林運算式，例如。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 程式碼路徑描述方法或函式呼叫來取得目前程式的執行點的名稱。 程式碼路徑的清單表示的呼叫堆疊。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)