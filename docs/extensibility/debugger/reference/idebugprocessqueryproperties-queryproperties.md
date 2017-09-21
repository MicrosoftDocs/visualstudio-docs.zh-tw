---
title: "IDebugProcessQueryProperties::QueryProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessQueryProperties::QueryProperties"
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugProcessQueryProperties::QueryProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定的屬性值，偵錯的處理程序的這個方法查詢。  
  
## 語法  
  
```cpp#  
HRESULT QueryProperties(  
   ULONG                  celt,  
   PROCESS_PROPERTY_TYPE *rgdwPropTypes,  
   VARIANT               *rgtPropValues);  
```  
  
```c#  
int QueryProperties(  
   uint                       celt,  
   enum_PROCESS_PROPERTY_TYPE rgdwPropTypes,  
   out object[ ]              rgtPropValues);  
```  
  
#### 參數  
 `celt`  
 \[in\]包含的屬性定義與屬性值的陣列的大小。  
  
 `dwPropType`  
 \[in\]陣列，包含定義查詢的屬性。  可能的值為：  
  
-   PROCESS\_PROPERTY\_COMMAND\_LINE \= 1  
  
-   PROCESS\_PROPERTY\_CURRENT\_DIRECTORY \= 2  
  
-   PROCESS\_PROPERTY\_ENVIRONMENT\_VARIABLES \= 3  
  
 `pvarPropValue`  
 \[\] out陣列，其中包含的屬性值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 很少使用這個方法。  
  
## 請參閱  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)