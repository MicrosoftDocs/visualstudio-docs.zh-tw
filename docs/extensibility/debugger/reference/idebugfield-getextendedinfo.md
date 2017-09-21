---
title: "IDebugField::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugField::GetExtendedInfo 方法"
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法取得擴充欄位的相關資訊。  
  
## 語法  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```c#  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### 參數  
 `guidExtendedInfo`  
 \[in\]選取要傳回的資訊。  有效值為：  
  
|值|描述|  
|-------|--------|  
|`guidConstantValue`|成為一連串的位元組的值。|  
|`guidConstantType`|型別簽名碼為型別。|  
  
 `prgBuffer`  
 \[\] out傳回額外的資訊。  
  
 `pdwLen`  
 輸入 \[、 輸出\]會傳回大小的額外的資訊，以位元組為單位。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 目前，這個方法會傳回只有型別或常數的值。  呼叫端必須釋放傳回在緩衝區`prgBuffer`地呼叫 COM 的`CoTaskMemFree`函式 \(c \+ \+\) 或<xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> \(C\#\)。  
  
## 請參閱  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)