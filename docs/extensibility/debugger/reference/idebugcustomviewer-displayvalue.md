---
title: "IDebugCustomViewer::DisplayValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer::DisplayValue"
helpviewer_keywords: 
  - "IDebugCustomViewer::DisplayValue"
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

若要顯示指定的值，會呼叫這個方法。  
  
## 語法  
  
```cpp#  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```c#  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### 參數  
 `hwnd`  
 \[in\]父視窗  
  
 `dwID`  
 \[in\]支援多種類型的自訂檢視器的識別碼。  
  
 `pHostServices`  
 \[in\] 保留。  永遠設定為 null。  
  
 `pDebugProperty`  
 \[in\]可以用來擷取要顯示值的介面。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  
  
## 備註  
 因為這個方法會建立所需的視窗、 顯示值、 等待輸入，並關閉視窗中，所有傳回給呼叫端之前，顯示為"modal"。  這表示該方法必須處理所有層面顯示屬性的值，無法建立輸出中、 等候使用者輸入，來終結視窗的視窗。  
  
 若要支援變更值在指定[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)物件時，您可以使用[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)方法 — 如果值可以表示為字串。  否則，就必須建立一個自訂介面，由運算式評估工具實作這`DisplayValue`方法 — 相同的物件實作`IDebugProperty3`介面。  這個自訂介面提供方法，用於修改任意大小或複雜的資料。  
  
## 請參閱  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)