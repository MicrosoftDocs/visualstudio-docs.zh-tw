---
title: "PORT_SUPPLIER_DESCRIPTION_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PORT_SUPPLIER_DESCRIPTION_FLAGS 列舉型別"
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# PORT_SUPPLIER_DESCRIPTION_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

定義可擷取有關連接埠提供者的中繼資料。  
  
## 語法  
  
```cpp#  
enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS  
{  
   PSDFLAG_SHOW_WARNING_ICON = 0x1  
};  
typedef DWORD PORT_SUPPLIER_DESCRIPTION_FLAGS;  
```  
  
```c#  
public enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS  
{  
   PSDFLAG_SHOW_WARNING_ICON = 0x1  
};  
```  
  
## 詞彙  
 PSDFLAG\_SHOW\_WARNING\_ICON  
 如果選取，則會在 UI 中顯示的警告圖示。  
  
## 備註  
 這個列舉型別傳回的[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)方法。  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)