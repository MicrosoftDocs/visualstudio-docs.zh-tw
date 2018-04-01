---
title: IDebugPortEx2::GetPortProcessId |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5ecc39025ce92cf2b2d230b6690ad1b7bc5896ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
取得本身的連接埠的處理序識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPortProcessId (   
   DWORD* pdwProcessId  
);  
```  
  
```csharp  
int GetPortProcessId (   
   out uint pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwProcessId`  
 [out]傳回本身的連接埠之實體的處理序識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 Win32 執行階段中，這個方法通常會呼叫 Win32 函式`GetCurrentProcessId`取得實體的處理序識別碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)