---
title: IDebugProgram2：： EnumCodePaths |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4d34b1b6519407e02d4340a5108ef03cece12b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202764"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

抓取原始程式檔中指定位置的程式碼路徑清單。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 在IDE 中 [ **來源** **] 或 [** 反組解碼] 視圖中游標下的文字。  
  
 `pStart`  
 在代表目前程式碼內容的 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 物件。  
  
 `pFrame`  
 在 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 物件，代表與目前中斷點相關聯的堆疊框架。  
  
 `fSource`  
 在非零 (`TRUE`) 如果在**來源**視圖中則為零，如果在 [反組解碼] 視圖中則為零 (`FALSE`) 。 **Disassembly**  
  
 `ppEnum`  
 擴展傳回 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) 物件，其中包含程式碼路徑的清單。  
  
 `ppSafety`  
 擴展傳回 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 物件，代表在略過選擇的程式碼路徑時，要設定為中斷點的額外程式碼內容。 例如，如果是縮短的布林運算式，就會發生這種情況。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 程式碼路徑描述方法或函式的名稱，這個方法或函式的名稱會被呼叫以取得程式執行的目前位置。 程式碼路徑清單代表呼叫堆疊。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
