---
title: "IDebugExtendedField::GetExtendedKind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExtendedField::GetExtendedKind"
  - "GetExtendedKind"
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugExtendedField::GetExtendedKind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取指定的延伸的欄位種類。  
  
## 語法  
  
```cpp#  
HRESULT GetExtendedKind(  
   FIELD_KIND_EX* pdwKind  
);  
```  
  
```c#  
int GetExtendedKind(  
   ref enum_FIELD_KIND_EX pdwKind  
);  
```  
  
#### 參數  
 `pdwKind`  
 輸入 \[、 輸出\]從數值[FIELD\_KIND\_EX](../../../extensibility/debugger/reference/field-kind-ex.md)定義的欄位類型的列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)