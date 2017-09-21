---
title: "IDebugSettingsCallback2::EnumEEs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::EnumEEs"
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugSettingsCallback2::EnumEEs
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

列舉給定語言和廠商的識別項使用的運算式評估工具。  
  
## 語法  
  
```cpp#  
HRESULT EnumEEs(  
   DWORD  celtBuffer,  
   GUID*  rgguidLang,  
   GUID*  rgguidVendor,  
   DWORD* pceltEEs  
);  
```  
  
```c#  
public int EnumEEs(  
   uint       celtBuffer,  
   ref Guid   rgguidLang,  
   ref Guid   rgguidVendor,  
   ref uint[] pceltEEs  
);  
```  
  
#### 參數  
 `celtBuffer`  
 \[in\]中的項目數`pceltEEs`的緩衝區。  
  
 `rgguidLang`  
 輸入 \[、 輸出\]程式語言的唯一識別項。  
  
 `rgguidVendor`  
 輸入 \[、 輸出\]供應商的唯一識別項。  
  
 `pceltEEs`  
 輸入 \[、 輸出\]運算式評估工具的陣列。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)