---
title: "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

跨處理序界限，會取得指定的介面。  
  
## 語法  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```c#  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### 參數  
 `riid`  
 \[in\]取得介面的 GUID。  
  
 `ppvObject`  
 \[\] out傳回的物件實作所需的介面。  \[C \+ \+\] 這樣就可以直接與您想要的介面型別轉換。  \[C\#\] 使用<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>方法來取得所要的介面。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 當偵錯引擎正在執行，這個方法使用[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]處理序空間及偵錯的程式正在執行它自己的處理序空間。  
  
## 請參閱  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)