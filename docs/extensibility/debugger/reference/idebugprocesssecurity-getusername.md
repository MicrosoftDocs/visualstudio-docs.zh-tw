---
title: "IDebugProcessSecurity::GetUserName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::GetUserName"
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

從連接埠提供者取得使用者名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```c#  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### 參數  
 `pbstrUserName`  
 \[\] out字串，包含使用者名稱。  
  
## 傳回值  
 如果此方法將會成功，則會傳回`S_OK`。  否則，它會傳回錯誤碼。  
  
## 備註  
 `GetUserName`傳回顯示在所使用的使用者名稱**的使用者名稱**資料行的**附加至處理序**對話方塊。  若要檢視**附加至處理序**對話方塊中，按一下 \[ **附加至處理序**上**工具**在功能表[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\)。  
  
## 請參閱  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)