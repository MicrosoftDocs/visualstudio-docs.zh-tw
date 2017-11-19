---
title: "IDebugEngine2::CauseBreak |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::CauseBreak
helpviewer_keywords: IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eeb8c262d6e1abc88e40f027d921ae2d4ae12cf2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
其中一個其執行緒嘗試執行要求的所有程式進行偵錯這個偵錯引擎 (DE) 來停止執行下一次。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法是非同步： [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)程式接下來嘗試執行之後呼叫這個方法時，會傳送事件。  
  
## <a name="see-also"></a>另請參閱  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)