---
title: "IDebugErrorEvent2::GetErrorMessage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
helpviewer_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回可讓建構的人們可讀取的錯誤訊息的資訊。  
  
## 語法  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```c#  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### 參數  
 `pMessageType`  
 \[\] out傳回值，從[訊息類型](../../../extensibility/debugger/reference/messagetype.md)列舉型別，描述訊息的型別。  
  
 `pbstrErrorFormat`  
 \[\] out最後的訊息給使用者的格式 \(如需詳細資訊，請參閱 「 備註 」\)。  
  
 `hrErrorReason`  
 \[\] out錯誤碼訊息是有關。  
  
 `pdwType`  
 \[\] out錯誤的嚴重性 \(使用 MB\_XXX 常數，如`MessageBox`。 for example, `MB_EXCLAMATION` or `MB_WARNING`\).  
  
 `pbstrHelpFileName`  
 \[\] out\(設定為 null 值，如果沒有說明檔\) 中的 \[說明\] 檔案的路徑。  
  
 `pdwHelpId`  
 \[\] out要顯示 \(設為 0，如果沒有任何 \[說明\] 主題\) 的 \[說明\] 主題的 ID。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 錯誤訊息應設定的格式像`"What I was doing.  %1"`。  `"%1"`會接著由呼叫端以取代衍生自錯誤代碼的錯誤訊息 \(它會傳回`hrErrorReason`\)。  `pMessageType`參數會告訴呼叫者應如何顯示最後的錯誤訊息。  
  
## 請參閱  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [訊息類型](../../../extensibility/debugger/reference/messagetype.md)