---
title: IDebugProgram3::ExecuteOnThread |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8aff643014da16ed9644573a77cb8444836d713d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117058"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
執行偵錯工具的程式。 執行緒會傳回給哪一個執行緒執行程式時，正在檢視使用者的偵錯工具資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 有三種不同的方式偵錯工具可以繼續之後停止執行：  
  
-   執行： 取消任何先前的步驟，並執行下一個中斷點為止，依此類推。  
  
-   步驟： 取消任何舊的步驟，並執行，直到新的步驟會完成。  
  
-   繼續： 再次執行，並保持使用中的任何舊的步驟。  
  
 執行緒傳遞給`ExecuteOnThread`決定哪個步驟取消時很有用。 如果您不知道執行的執行緒，執行會取消所有步驟。 執行緒的資訊之後，您只需要取消使用中執行緒上的步驟。  
  
## <a name="see-also"></a>另請參閱  
 [執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)