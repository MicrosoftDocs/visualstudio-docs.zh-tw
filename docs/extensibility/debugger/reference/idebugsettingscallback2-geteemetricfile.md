---
title: "IDebugSettingsCallback2::GetEEMetricFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEEMetricFile"
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2::GetEEMetricFile
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取運算式評估工具公制檔案指定名稱\] 或 \[公制。  
  
## 語法  
  
```cpp#  
HRESULT GetEEMetricFile(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```c#  
private int GetEEMetricFile(  
   ref Guid   guidLang,  
   ref Guid   guidVendor,  
   string     pszMetric,  
   out string pbstrValue  
);  
```  
  
#### 參數  
 `guidLang`  
 \[in\]唯一的識別項的程式語言。  
  
 `guidVendor`  
 \[in\]廠商的唯一的識別項。  
  
 `pszMetric`  
 \[in\]計量值的名稱。  
  
 `pbstrValue`  
 \[\] out以字串傳回公制檔案的內容。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)