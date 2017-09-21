---
title: "IDebugSymbolProviderDirect::GetCurrentModulesInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetCurrentModulesInfo"
  - "GetCurrentModulesInfo"
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugSymbolProviderDirect::GetCurrentModulesInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取 \[符號\] 群組中模組的相關資訊。  
  
## 語法  
  
```cpp#  
HRESULT GetCurrentModulesInfo(  
   unsigned long * pCount,  
   GUID *          ppGuids,  
   DWORD *         pADIds,  
   DWORD *         pCurrentState,  
   IUnknown **     ppCDModItfs  
);  
```  
  
```c#  
int GetCurrentModulesInfo(  
   uint       pCount,  
   Guid       ppGuids,  
   uint       pADIds,  
   uint       pCurrentState,  
   out object ppCDModItfs  
);  
```  
  
#### 參數  
 `pCount`  
 \[in\]模組中的數字`ppGuids`陣列。  
  
 `ppGuids`  
 \[in\]包含模組的唯一識別項的陣列。  
  
 `pADIds`  
 \[in\]應用程式定義域的識別項。  
  
 `pCurrentState`  
 \[in\]\[符號\] 群組的目前狀態。  
  
 `ppCDModItfs`  
 \[\] out傳回物件，包含 \[符號\] 群組中的模組。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)