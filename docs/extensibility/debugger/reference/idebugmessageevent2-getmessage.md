---
title: IDebugMessageEvent2::GetMessage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2cb6db61048765ec577a0d14ff4079f78e013219
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2018
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
取得要顯示的訊息。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMessage(   
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrMessage,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetMessage(   
   out enum_MESSAGETYPE pMessageType,  
   out string           pbstrMessage,  
   out uint             pdwType,  
   out string           pbstrHelpFileName,  
   out uint             dwHelpId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pMessageType`  
 [out]傳回值，從[MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)描述訊息類型的列舉。  
  
 `pbstrMessage`  
 [out]傳回訊息。  
  
 `pdwType`  
 [out]傳回的訊息，使用 Win32 的慣例類型`MessageBox`函式。 請參閱[AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)函式，如需詳細資訊。  
  
 `pbstrHelpFileName`  
 [in、 out]傳回說明檔名稱。 如果沒有說明檔可能是 null （c + +） 或空值 (C#)。  
  
 `pdwHelpId`  
 [in、 out]傳回說明識別碼。 可能是 0，如果沒有說明關聯與此訊息。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)