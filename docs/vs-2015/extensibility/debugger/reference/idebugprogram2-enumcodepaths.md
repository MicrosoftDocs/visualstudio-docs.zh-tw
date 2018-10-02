---
title: IDebugProgram2::EnumCodePaths |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2f18a95fb63b0db7ea5e4a3a34a663ac1a5ad6c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486097"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProgram2::EnumCodePaths](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-enumcodepaths)。  
  
擷取一份原始程式檔中的指定位置的程式碼路徑。  
  
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
 [in]在游標下方 word**來源**或是**反組譯碼**在 IDE 中的檢視。  
  
 `pStart`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，表示目前的程式碼內容。  
  
 `pFrame`  
 [in][IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)物件代表堆疊框架的目前中斷點相關聯。  
  
 `fSource`  
 [in]非零值 (`TRUE`) 如果在**來源**檢視中，則為零 (`FALSE`) 中的 if**反組譯碼**檢視。  
  
 `ppEnum`  
 [out]傳回[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)物件，其中包含一份程式碼路徑。  
  
 `ppSafety`  
 [out]傳回[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件代表要設定為中斷點中，如果所選的程式碼路徑的額外的程式碼內容會略過。 這可能會發生在最少運算的布林運算式，例如。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 程式碼路徑描述方法或移至目前的點，在程式執行所呼叫函式的名稱。 一份程式碼路徑表示的呼叫堆疊。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)

