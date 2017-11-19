---
title: "IDebugProcess2::EnumThreads |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::EnumThreads
helpviewer_keywords: IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e1cc33d1a84f5f8a3cd186b148f57e296a350f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
擷取處理序中執行的所有執行緒的清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)物件，其中包含所有處理序中的程式中的所有執行緒的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會列舉在每一個程式中執行的執行緒，然後將它們合併成一個執行緒處理序檢視。 單一執行緒可以執行多個程式。這個方法一次列舉該執行緒。  
  
 這個方法提供一份不重複的處理序的執行緒。 否則，若要列舉執行特定程式的執行緒，請使用[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)