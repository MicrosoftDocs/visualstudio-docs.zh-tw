---
title: "IDebugPortEx2::GetPortProcessId |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEx2::GetPortProcessId
helpviewer_keywords: IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 300f0553ee081dee8adc34ab48ce1989fc86e6c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)