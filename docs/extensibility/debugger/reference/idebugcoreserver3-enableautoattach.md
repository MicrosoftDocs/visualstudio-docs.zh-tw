---
title: "IDebugCoreServer3::EnableAutoAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
helpviewer_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

啟用自動附加指定的偵錯引擎。  
  
## 語法  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```c#  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### 參數  
 `rgguidSpecificEngines`  
 \[in\]若要標記為自動附加的每個偵錯引擎 Guid 的陣列。  
  
 `celtSpecificEngines`  
 \[in\]控制台中的引擎數`rgguidSpecificEngines`。  
  
 `pszStartPageUrl`  
 \[in\]自動附加時所使用的起始 URL。  
  
 `pbstrSessionID`  
 \[\] out已自動附加工作階段的識別碼。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  一個錯誤碼`E_AUTO_ATTACH_NOT_REGISTERED`，表示 auto\-attach 類別處理站尚未註冊。  
  
## 備註  
 指定的 URL 相關聯的程式啟動時，指定偵錯引擎自動啟動並附加。  
  
## 請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)