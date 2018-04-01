---
title: IDebugProgram2::CauseBreak |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 48029ed4e925073b0d121a88846aa2f0af0a51cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
程式停止執行下一個要求的時間它執行緒嘗試執行的其中一個。  
  
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
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)程式接下來嘗試執行程式碼之後會呼叫這個方法, 時，會傳送事件。  
  
 這個方法是非同步方法會立即傳回而不一定會等候程式停止。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)