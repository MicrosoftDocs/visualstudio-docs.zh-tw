---
title: "IDebugBinder3::GetEEService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetEEService"
helpviewer_keywords: 
  - "IDebugBinder3::GetEEService 方法"
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder3::GetEEService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會傳回要求的服務。  
  
## 語法  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```c#  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### 參數  
 `vendor`  
 \[in\]`GUID`的供應商 \(null 值是可接受的\)。  
  
 `language`  
 \[in\]`GUID` \(null 值是可接受的\) 的語言。  
  
 `iid`  
 \[in\]`IID`要取得的服務。  
  
 `ppService`  
 \[\] out要求的服務介面。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 傳遞`IID`的[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)介面 \(`IID_IEEVisualizerServiceProvider`\)，看看是否可以使用型別視覺化檢視的服務。  如果運算式評估工具可以取得， [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)介面以支援型別視覺化檢視。  如需詳細資訊，請參閱[視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)。  
  
## 請參閱  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)