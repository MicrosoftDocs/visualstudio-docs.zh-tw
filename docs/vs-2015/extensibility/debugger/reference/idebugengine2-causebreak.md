---
title: IDebugEngine2：： CauseBreak |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b6e52e4885a61c3fe04fff5bdcca08fd00cf460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198478"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

要求此 debug engine 所進行的所有程式都 (取消) ，以在下一個執行緒嘗試執行時停止執行。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法是非同步：當程式下一次嘗試在呼叫這個方法之後執行時，就會傳送 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 事件。  
  
## <a name="see-also"></a>另請參閱  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
