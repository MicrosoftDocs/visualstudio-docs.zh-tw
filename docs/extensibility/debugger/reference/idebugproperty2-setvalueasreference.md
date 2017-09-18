---
title: "IDebugProperty2::SetValueAsReference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsReference"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsReference 方法"
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

設定這個屬性的值指定參考的值。  
  
## 語法  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```c#  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### 參數  
 `rgpArgs`  
 \[in\]要傳遞給 managed 程式碼屬性的 set 存取子的引數陣列。  如果屬性的 set 存取子不接受引數，或者此[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件並未參考這類屬性 setter `rgpArgs`應該能為空白值。  這個參數通常是 null 值。  
  
 `dwArgCount`  
 \[in\]以引數的數字`rgpArgs`陣列。  
  
 `pValue`  
 \[in\]參照位址形式的[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，用來設定此屬性的值。  
  
 `dwTimeout`  
 \[in\]多久才會設定值，以毫秒為單位。  典型的值是`INFINITE`。  這會影響任何可能的評估可以花時間的長度。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼，通常是下列一項動作：  
  
|錯誤|描述|  
|--------|--------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|不支援從參考的設定值。|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|無法設定值，因為這個屬性是指一種方法。|  
|`E_SETVALUE_VALUE_IS_READONLY`|值是唯讀的而且無法設定。|  
|`E_NOTIMPL`|未實作這個方法。|  
  
## 請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)