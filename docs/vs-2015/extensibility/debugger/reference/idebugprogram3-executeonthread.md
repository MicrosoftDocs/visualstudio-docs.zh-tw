---
title: IDebugProgram3::ExecuteOnThread |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e3f63b0afffb833fdc59bf39ac5214ccc799e0f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865046"
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
  
- 執行： 取消任何先前的步驟，並一直執行，直到下一個中斷點，依此類推。  
  
- 步驟： 取消任何舊的步驟，並執行，直到新的步驟會完成。  
  
- 繼續： 再次執行，並讓任何舊的步驟保持在作用中。  
  
  執行緒傳遞給`ExecuteOnThread`決定哪個步驟來取消時很有用。 如果您不知道執行的執行緒，執行會取消所有步驟。 了解的執行緒，您只需要取消作用中執行緒上的步驟。  
  
## <a name="see-also"></a>另請參閱  
 [執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)

