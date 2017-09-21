---
title: "IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
helpviewer_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

伺服器上建立偵錯引擎執行的個體。  
  
## 語法  
  
```cpp#  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```c#  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### 參數  
 `szDll`  
 \[in\]實作控制台中的 CLSID 的 dll 路徑`clsidObject`參數。  如果這是`NULL`，然後 COM 的`CoCreateInstance`函式被呼叫。  
  
 `wLangId`  
 \[in\]偵錯引擎的地區設定。  這可以是 0，如果[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)不應該呼叫方法。  
  
 `clsidObject`  
 \[in\]若要建立偵錯引擎的 CLSID。  
  
 `riid`  
 \[in\]特定介面的介面識別碼來擷取 object 的類別。  
  
 `ppvObject`  
 \[\] out`IUnknown`介面執行個體化的物件。  轉型或封送處理這個物件所要的介面。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)