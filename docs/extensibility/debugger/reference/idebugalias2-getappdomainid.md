---
title: "IDebugAlias2::GetAppDomainId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetAppDomainId"
  - "IDebugAlias2::GetAppDomainId"
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAlias2::GetAppDomainId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取應用程式定義域的識別項。  
  
## 語法  
  
```cpp#  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```c#  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### 參數  
 `pappDomainId`  
 \[\] out傳回應用程式定義域識別項。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 建立的應用程式網域的識別項有變更時重新啟動應用程式和新的應用程式定義域。  
  
## 請參閱  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)