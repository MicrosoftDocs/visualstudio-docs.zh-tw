---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfc64f8ae928b4bb0057a16b8a74c6ddbff588c0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942226"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

偵錯工具將程式執行。 執行緒會傳回給哪一個執行緒執行程式時，正在檢視使用者的偵錯工具資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 有三種不同的方式偵錯工具可以繼續執行停止後的執行：  
  
- 執行：取消任何先前的步驟，並一直執行，直到下一個中斷點，依此類推。  
  
- 步驟：取消任何舊的步驟，並執行，直到新的步驟會完成。  
  
- 繼續：再次執行，並讓任何舊的步驟保持在作用中。  
  
  執行緒傳遞給`ExecuteOnThread`決定哪個步驟來取消時很有用。 如果您不知道執行的執行緒，執行會取消所有步驟。 了解的執行緒，您只需要取消作用中執行緒上的步驟。  
  
## <a name="see-also"></a>另請參閱  
 [執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
