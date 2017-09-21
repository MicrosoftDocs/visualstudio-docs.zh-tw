---
title: "IDebugProperty3::CreateObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::CreateObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::CreateObjectID"
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立這個屬性以確保其唯一性於所有其他屬性的唯一 ID。  
  
## 語法  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```c#  
int CreateObjectID();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 工作階段的偵錯管理員想要確定在所有其他屬性唯一識別這個屬性時，會呼叫這個方法。  偵錯引擎 \(DE\) 支援這種方式，除非已經唯一地識別它釐清屬性。  如果是不支援這個方法，則會傳回`E_NOTIMPL`。  
  
 使用所建立的任何唯一 ID `CreateObjectID`被終結時[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) ，會呼叫方法。 這也表示需要用來唯一識別這個屬性的結尾。  
  
> [!NOTE]
>  沒有擷取這個唯一的 ID，所以 DE 可以執行任何需要唯一 Id 的方法時`CreateObjectID` ，會呼叫方法。  
  
## 請參閱  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)