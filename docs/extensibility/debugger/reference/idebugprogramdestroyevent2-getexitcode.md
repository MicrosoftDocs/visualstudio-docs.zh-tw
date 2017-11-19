---
title: "IDebugProgramDestroyEvent2::GetExitCode |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramDestroyEvent2::GetExitCode
helpviewer_keywords: IDebugProgramDestroyEvent2::GetExitCode
ms.assetid: 7f540cf6-e2d1-42b0-913e-a26d654b7659
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d075ddafb81bf30423842986317d4724b6b42e7c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramdestroyevent2getexitcode"></a>IDebugProgramDestroyEvent2::GetExitCode
取得程式的結束代碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetExitCode(   
   DWORD* pdwExit  
);  
```  
  
```csharp  
int GetExitCode(   
   out uint pdwExit  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwExit`  
 [out]傳回程式的結束代碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)