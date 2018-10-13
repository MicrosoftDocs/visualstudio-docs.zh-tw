---
title: MODULE_INFO_FIELDS |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a0ab7baf5a878cecdf3cb1644187fd50a5e6be3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222387"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定偵錯模組資訊旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## <a name="members"></a>成員  
 MIF_NONE  
 初始化/使用無結構中的欄位。  
  
 MIF_NAME  
 初始化/使用`m_bstrName`欄位中[MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構。  
  
 MIF_URL  
 初始化/使用`m_bstrUrl`欄位中`MODULE_INFO`結構。  
  
 MIF_VERSION  
 初始化/使用`m_bstrVersion`欄位中`MODULE_INFO`結構。  
  
 MIF_DEBUGMESSAGE  
 初始化/使用`m_bstrDebugMessage`欄位中`MODULE_INFO`結構。  
  
 MIF_LOADADDRESS  
 初始化/使用`m_addrLoadAddress`欄位中`MODULE_INFO`結構。  
  
 MIF_PREFFEREDADDRESS  
 初始化/使用`m_addrPreferredLoadAddress`欄位中`MODULE_INFO`結構。  
  
 MIF_SIZE  
 初始化/使用`m_dwSize`欄位中`MODULE_INFO`結構。  
  
 MIF_LOADORDER  
 初始化/使用`m_dwLoadOrder`欄位中`MODULE_INFO`結構。  
  
 MIF_TIMESTAMP  
 初始化/使用`m_TimeStamp`欄位中`MODULE_INFO`結構。  
  
 MIF_URLSYMBOLLOCATION  
 初始化/使用`m_bstrUrlSymbolLocation`欄位中`MODULE_INFO`結構。  
  
 MIF_FLAGS  
 初始化/使用`m_dwModuleFlags`欄位中`MODULE_INFO`結構。  
  
 MIF_ALLFIELDS  
 初始化/使用中的欄位的所有`MODULE_INFO`結構。  
  
## <a name="remarks"></a>備註  
 這些值會傳遞做為引數[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)方法，以表示哪些欄位[MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構會進行初始化。  
  
 這些值也會在`MODULE_INFO`表示哪些欄位已使用且有效的結構。  
  
 這些旗標可能會結合的位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)

