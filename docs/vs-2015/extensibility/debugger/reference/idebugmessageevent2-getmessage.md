---
title: IDebugMessageEvent2::GetMessage |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b836c6b441e260e550e677e002fff393b981af17
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498879"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugMessageEvent2::GetMessage](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmessageevent2-getmessage)。  
  
取得要顯示的訊息。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [out]傳回值，以從[MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)描述訊息類型的列舉型別。  
  
 `pbstrMessage`  
 [out]傳回訊息。  
  
 `pdwType`  
 [out]傳回的訊息，並使用 Win32 的慣例類型`MessageBox`函式。 請參閱[AfxMessageBox](http://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8)函式，如需詳細資訊。  
  
 `pbstrHelpFileName`  
 [in、 out]傳回說明檔名稱。 可能是 null （c + +） 或空值 (C#)，如果沒有說明檔。  
  
 `pdwHelpId`  
 [in、 out]傳回的說明識別碼。 可能是 0，如果沒有說明關聯與此訊息。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](http://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8)

