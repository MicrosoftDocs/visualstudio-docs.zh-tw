---
title: "IDebugErrorEvent2::GetErrorMessage |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords: IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b8a4e4c2ca938d8c600d3fd9ef0e615aa847fd9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
傳回可讓人類看得懂的錯誤訊息建構的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pMessageType`  
 [out]傳回值，從[MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)描述的訊息類型的列舉。  
  
 `pbstrErrorFormat`  
 [out]最後一個訊息給使用者的格式 （如需詳細資訊，請參閱 < 備註 >）。  
  
 `hrErrorReason`  
 [out]錯誤碼的訊息是關於。  
  
 `pdwType`  
 [out]錯誤的嚴重性 (使用如 MB_XXX 常數`MessageBox`; 例如，`MB_EXCLAMATION`或`MB_WARNING`)。  
  
 `pbstrHelpFileName`  
 [out]說明檔 （設定為 null 值，如果沒有說明檔） 的路徑。  
  
 `pdwHelpId`  
 [out]若要顯示 （設定為 0，表示沒有任何說明主題） 說明主題的識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 錯誤訊息的格式應沿著`"What I was doing.  %1"`。 `"%1"`會再變成由呼叫端衍生自錯誤碼的錯誤訊息 (在傳回`hrErrorReason`)。 `pMessageType`參數會告知呼叫端應如何顯示最後的錯誤訊息。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)