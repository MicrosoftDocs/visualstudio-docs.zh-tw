---
title: IDebugMessageEvent2::SetResponse | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2ea8e766561261b4860f973002d302ac99caa8dd
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2018
---
# <a name="idebugmessageevent2setresponse"></a>IDebugMessageEvent2::SetResponse
設定回應，如果有，從訊息方塊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetResponse(   
   DWORD dwResponse  
);  
```  
  
```csharp  
int SetResponse(   
   uint dwResponse  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwResponse`  
 [in]指定的回應，使用 Win32 的慣例`MessageBox`函式。 請參閱[AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)函式，如需詳細資訊。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)