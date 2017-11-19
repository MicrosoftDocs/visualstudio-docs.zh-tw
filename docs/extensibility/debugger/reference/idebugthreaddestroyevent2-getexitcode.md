---
title: "IDebugThreadDestroyEvent2::GetExitCode |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThreadDestroyEvent2::GetExitCode
helpviewer_keywords: IDebugThreadDestroyEvent2::GetExitCode
ms.assetid: 8bf47a17-f811-4d9b-bcea-7488908830ff
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3da51d051b6c76410274b22819f10b9eae4c19f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthreaddestroyevent2getexitcode"></a>IDebugThreadDestroyEvent2::GetExitCode
取得執行緒結束代碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetExitCode (   
   DWORD* pdwExit  
);  
```  
  
```csharp  
int GetExitCode (   
   out uint pdwExit  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwExit`  
 [out]傳回執行緒結束代碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)