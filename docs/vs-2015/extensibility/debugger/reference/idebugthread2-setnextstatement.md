---
title: IDebugThread2::SetNextStatement |Microsoft Docs
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
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55482e4bf3b4795f7c7f036c0074e456fd642a33
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500000"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugThread2::SetNextStatement](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugthread2-setnextstatement)。  
  
設定目前的指令指標至指定的程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pStackFrame`  
 保留供未來使用;設定為 null 的值。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)描述將要執行的程式碼位置的物件和其內容。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 下表顯示其他可能的值。  
  
|值|描述|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|下一個陳述式不能在框架的堆疊上更深入的堆疊框架。|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|找不到任何堆疊框架相關聯的下一步 的陳述式。|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|有些偵錯引擎不能設定例外狀況之後的下一個陳述式。|  
  
## <a name="remarks"></a>備註  
 指令指標表示下一個指令或陳述式來執行。 這個方法用來重試一次一行程式碼，來源，或強制在另一個函式，例如繼續執行。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)

