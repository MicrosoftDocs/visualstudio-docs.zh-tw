---
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 90dbf573c60e17194546085d7d5fdcb70ea8a334
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Returns information that allows construction of a human-readable error message.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```cs  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pMessageType`  
 [out] Returns a value from the [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) enumeration, describing the type of message.  
  
 `pbstrErrorFormat`  
 [out] The format of the final message to the user (see "Remarks" for details).  
  
 `hrErrorReason`  
 [out] The error code the message is about.  
  
 `pdwType`  
 [out] Severity of the error (use the MB_XXX constants for `MessageBox`; for example, `MB_EXCLAMATION` or `MB_WARNING`).  
  
 `pbstrHelpFileName`  
 [out] Path to a help file (set to a null value if there is no help file).  
  
 `pdwHelpId`  
 [out] ID of the help topic to display (set to 0 if there is no help topic).  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The error message should be formatted along the lines of `"What I was doing.  %1"`. The `"%1"` would then be replaced by the caller with the error message derived from the error code (which is returned in `hrErrorReason`). The `pMessageType` parameter tells the caller how the final error message should be displayed.  
  
## <a name="see-also"></a>See Also  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
