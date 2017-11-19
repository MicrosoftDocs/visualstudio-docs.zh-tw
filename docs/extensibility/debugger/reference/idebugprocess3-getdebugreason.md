---
title: "IDebugProcess3::GetDebugReason |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::GetDebugReason
helpviewer_keywords: IDebugProcess3::GetDebugReason
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c88282541c20e93f86c5d8369ade795ecb95387
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess3getdebugreason"></a>IDebugProcess3::GetDebugReason
這個方法會傳回處理程序已啟動的偵錯的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDebugReason(  
   DEBUG_REASON* pReason  
);  
```  
  
```csharp  
int GetDebugReason(  
   out enum_DEBUG_REASON pReason  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pReason`  
 [out]傳回值，從[DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)列舉型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)