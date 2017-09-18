---
title: "IDebugProperty2::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得擴充屬性的資訊。  
  
## 語法  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```c#  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### 參數  
 `guidExtendedInfo`  
 \[in\]決定要擷取的延伸資訊類型的 GUID。  如需詳細資訊，請參閱 「 備註 」。  
  
 `pExtendedInfo`  
 \[\] out傳回`VARIANT` \(c \+ \+\) 或物件 \(C\#\)，可用來擷取擴充的屬性的資訊。  例如，這個參數可能會傳回`IUnknown`介面，可查詢的[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)介面。  如需詳細資訊，請參閱 「 備註 」。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  傳回`S_GETEXTENDEDINFO_NO_EXTENDEDINFO`如果沒有擴充擷取資訊。  
  
## 備註  
 這個方法，所以為了擷取本身就無法藉由呼叫所擷取的資訊的[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。  
  
 \(GUID 值指定給 C\# 由於名稱中不提供任何組件\) 這個方法通常可識別下列 Guid。  供內部使用，可以建立額外的 Guid。  
  
|名稱|GUID|描述|  
|--------|----------|--------|  
|guidDocument|{} 3f98de84\-fee9\-11d0\-b47f\-00a0244a1dd2|傳回`IUnknown`文件的介面。  一般而言， [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)介面可以取自這`IUnknown`介面。|  
|guidCodeContext|{e2fc65e\-56ce\-11 d 1\-b528\-00aax004a8797}|傳回`IUnknown`的文件內容的介面。  一般而言， [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面可以取自這`IUnknown`介面。|  
|guidCustomViewerSupported|{} d9c9da31\-ffbe\-4eeb\-9186\-23121e3c088c|傳回字串，包含自訂的檢視器，通常由運算式評估工具中實作的 CLSID。|  
|guidExtendedInfoSlot|{} 6df235ad\-82c6\-4292\-9c97\-7389770bc42f|傳回代表您想要的介面槽編號，如果這個屬性表示 managed 程式碼的本機位址的 32 位元數字。|  
|guidExtendedInfoSignature|{} b5fb6d46\-f805\-417f\-96a3\-8ba737073ffd|傳回字串，包含變數的屬性物件相關聯的簽章。|  
  
## 請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)