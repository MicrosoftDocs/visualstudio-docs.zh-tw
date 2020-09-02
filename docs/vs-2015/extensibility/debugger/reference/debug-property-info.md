---
title: DEBUG_PROPERTY_INFO |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4c4200cb5a44e185d50158829fe44152707ee459
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143039"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

包含 debug 屬性的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
typedef struct tagDEBUG_PROPERTY_INFO {   
   DEBUGPROP_INFO_FLAGS dwValidFields;  
   BSTR                 bstrFullName;  
   BSTR                 bstrName;  
   BSTR                 bstrType;  
   BSTR                 bstrValue;  
   IDebugProperty2*     pProperty;  
   DBG_ATTRIB_FLAGS     dwAttrib;  
} DEBUG_PROPERTY_INFO;  
```  
  
```csharp  
public struct DEBUG_PROPERTY_INFO {   
   public uint            dwValidFields;  
   public string          bstrFullName;  
   public string          bstrName;  
   public string          bstrType;  
   public string          bstrValue;  
   public IDebugProperty2 pProperty;  
   public ulong           dwAttrib;  
};  
```  
  
## <a name="members"></a>成員  
 dwValidFields  
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)列舉中的旗標組合，可指定要填入的欄位。  
  
 bstrFullName  
 屬性的完整名稱。  
  
 bstrName  
 內容中的屬性名稱。  
  
 bstrType  
 格式化字串形式的屬性類型。  
  
 bstrValue  
 格式化字串形式的屬性值。  
  
 pProperty  
 此結構所描述的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 物件。  
  
 dwAttrib  
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)列舉中的旗標組合，描述這個屬性的屬性。  
  
## <a name="remarks"></a>備註  
 屬性是具有名稱、類型和值之階層式本質的物件。 例如，屬性可以描述區域變數、參數、監看式變數和運算式，以及註冊。  
  
 此結構會傳遞至其填入的 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 方法。 此結構也會從 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 介面傳回做為此結構清單的一部分，而這會從呼叫 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 和 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) 方法時傳回。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
