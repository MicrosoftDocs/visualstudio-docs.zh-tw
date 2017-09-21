---
title: "IDebugProgramNode2::GetProgramName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetProgramName"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetProgramName"
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramNode2::GetProgramName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得程式的名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetProgramName (   
   BSTR* pbstrProgramName  
);  
```  
  
```c#  
int GetProgramName (   
   out string pbstrProgramName  
);  
```  
  
#### 參數  
 `pbstrProgramName`  
 \[\] out傳回程式的名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 程式名稱不一樣的程式路徑，即使程式的名稱，可以將這類路徑的一部分。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CProgram`實作物件[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)介面。  `MakeBstr`函式會配置一份指定的字串，為 BSTR。  
  
```cpp#  
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {    
   if (!pbstrProgramName)    
      return E_INVALIDARG;    
  
   // Assign the member program name to the passed program name.    
   *pbstrProgramName = MakeBstr(m_pszProgramName);    
   return NOERROR;    
}    
```  
  
## 請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)