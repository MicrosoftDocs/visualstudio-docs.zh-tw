---
title: "IDebugProperty2::GetPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetPropertyInfo"
helpviewer_keywords: 
  - "IDebugProperty2::GetPropertyInfo"
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetPropertyInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得[DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構描述屬性。  
  
## 語法  
  
```cpp#  
HRESULT GetPropertyInfo (   
   DEBUGPROP_INFO_FLAGS dwFields,  
   DWORD                nRadix,  
   DWORD                dwTimeout,  
   IDebugReference2**   rgpArgs,  
   DWORD                dwArgCount,  
   DEBUG_PROPERTY_INFO* pPropertyInfo  
);  
```  
  
```cpp#  
int GetPropertyInfo (   
   enum_DEBUGPROP_INFO_FLAGS dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_PROPERTY_INFO[]     pPropertyInfo  
);  
```  
  
#### 參數  
 `dwFields`  
 \[in\]從值的組合[DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)列舉型別會指定哪一個欄位中填寫， `pPropertyInfo`結構。  
  
 `nRadix`  
 \[in\]要用於格式化數字的任何資訊的基數。  
  
 `dwTimeout`  
 \[in\]以毫秒為單位，這個方法傳回之前等待指定的最長的時間。  使用`INFINITE`無限期地等待。  
  
 `rgpArgs`  
 輸入 \[、 輸出\]保留供日後使用。 設定為 null 值。  
  
 `dwArgCount`  
 \[in\]保留供日後使用。 設為零。  
  
 `pPropertyInfo`  
 \[\] outA [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)會填入這些屬性的描述的結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  
  
## 請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)