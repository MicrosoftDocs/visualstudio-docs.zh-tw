---
title: "IDebugSettingsCallback2::GetEEMetricGuid | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEEMetricGuid"
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2::GetEEMetricGuid
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取運算式評估工具的度量單位，指定其名稱的唯一識別項。  
  
## 語法  
  
```cpp#  
HRESULT GetEEMetricGuid(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   GUID*   pguidValue  
);  
```  
  
```c#  
HRESULT GetEEMetricGuid(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out Guid pguidValue  
);  
```  
  
#### 參數  
 `guidLang`  
 \[in\]唯一的識別項的程式語言。  
  
 `guidVendor`  
 \[in\]廠商的唯一的識別項。  
  
 `pszMetric`  
 \[in\]計量值的名稱。  
  
 `pguidValue`  
 \[\] out傳回計量值的唯一識別項。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)