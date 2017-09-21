---
title: "IDebugProperty2::EnumChildren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::EnumChildren"
helpviewer_keywords: 
  - "IDebugProperty2::EnumChildren"
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取屬性的子系的清單。  
  
## 語法  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### 參數  
 `dwFields`  
 \[in\]從的旗標組合[DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)在列舉指定那一個欄位的列舉型別[DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構是要在 \[填滿。  
  
 `dwRadix`  
 \[in\]指定要用於格式化數字的任何資訊的基數。  
  
 `guidFilter`  
 \[in\]搭配使用的篩選器的 GUID `dwAttribFilter`和`pszNameFilter`參數，以選取哪一個`DEBUG_PROPERTY_INFO`是要列舉的子系。  例如， `guidFilterLocals`的本機變數的篩選器。  
  
 `dwAttribFilter`  
 \[in\]從的旗標組合[DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)列舉型別來指定何種類型的物件，例如列舉`DBG_ATTRIB_METHOD`可能是這個屬性的子系的所有方法。  用來結合`guidFilter`和`pszNameFilter`參數。  
  
 `pszNameFilter`  
 \[in\]搭配使用的篩選器名稱`guidFilter`和`dwAttribFilter`參數，以選取哪一個`DEBUG_PROPERTY_INFO`是要列舉的子系。  例如，設定這個參數為"MyX"的篩選器的所有子系，名稱為"MyX"。  
  
 `dwTimeout`  
 \[in\]以毫秒為單位，這個方法傳回之前等待指定的最長的時間。  使用`INFINITE`無限期地等待。  
  
 `ppEnum`  
 \[\] out傳回[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件，其中包含的子屬性清單。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  
  
## 請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)