---
title: "IDebugClassField::DoesInterfaceExist | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::DoesInterfaceExist"
helpviewer_keywords: 
  - "IDebugClassField::DoesInterfaceExist 方法"
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

決定是否特定的介面會定義在類別中。  
  
## 語法  
  
```cpp#  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```c#  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### 參數  
 `pszInterfaceName`  
 \[in\]字串，包含要尋找的介面名稱。  
  
## 傳回值  
 如果成功，傳回 S\_OK，則會傳回 S\_FALSE 如果介面不存在。 否則，會傳回錯誤碼。  
  
## 備註  
 作用中，這個方法會取得所有介面的列舉，並搜尋相符的介面清單。  
  
## 請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)