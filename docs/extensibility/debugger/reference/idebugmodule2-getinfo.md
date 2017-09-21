---
title: "IDebugModule2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2::GetInfo"
helpviewer_keywords: 
  - "GetInfo 方法"
  - "IDebugModule2::GetInfo 方法"
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得本單元的相關資訊。  
  
## 語法  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### 參數  
 `dwFields`  
 \[in\]從的旗標組合[MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)指定的欄位的列舉型別`pInfo`都必須填寫。  
  
 `pInfo`  
 輸入 \[、 輸出\]A [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)會被填入的模組描述的結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)結構包含中所顯示的模組名稱**模組**視窗。  
  
## 請參閱  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)