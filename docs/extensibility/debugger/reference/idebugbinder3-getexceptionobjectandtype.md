---
title: "IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType"
helpviewer_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType 方法"
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

如果有的話，這個方法會擷取與物件相關聯的例外狀況。  
  
## 語法  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```c#  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### 參數  
 `ppException`  
 \[\] out傳回物件，表示例外狀況。  
  
 `ppField`  
 \[\] out傳回代表特定的欄位可能會造成例外狀況 \(這可能是空值\) 的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
> [!NOTE]
>  如果要確認是否有例外狀況，請檢查所傳回的值`ppException`： 如果是 null 值，那麼任何例外狀況就不是這個物件相關聯。  
  
## 請參閱  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)