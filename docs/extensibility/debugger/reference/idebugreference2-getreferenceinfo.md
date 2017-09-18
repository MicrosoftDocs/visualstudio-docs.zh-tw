---
title: "IDebugReference2::GetReferenceInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::GetReferenceInfo"
helpviewer_keywords: 
  - "IDebugReference2::GetReferenceInfo"
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得[DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構描述的參考。  保留供將來使用。  
  
## 語法  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```c#  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### 參數  
 `dwFields`  
 \[in\]從的旗標組合[DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)列舉型別，決定欄位中填寫[DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。  
  
 `nRadix`  
 \[in\]要用於格式化數字的任何資訊基數。  
  
 `dwTimeout`  
 \[in\]最大時間 \(毫秒\)，從這個方法傳回之前等待。  使用`INFINITE`無限期地等待。  
  
 `rgpArgs`  
 \[in\]陣列的[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件。  保留供日後使用。 設定為 null 值。  
  
 `dwArgCount`  
 \[in\]參照中的引數`rgpArgs`陣列。  保留供日後使用。 設為 0。  
  
 `pReferenceInfo`  
 \[\] outA [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)會填入這些屬性的描述的結構。  
  
## 傳回值  
 永遠傳回 `E_NOTIMPL`。  
  
## 請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)