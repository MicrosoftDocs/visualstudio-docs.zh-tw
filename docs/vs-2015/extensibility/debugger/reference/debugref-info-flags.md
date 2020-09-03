---
title: DEBUGREF_INFO_FLAGS |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 05a073b3663ff85fe3d68878999aaf1dfa9e0017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198843"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定要針對 debug 參考物件取得哪些資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## <a name="members"></a>成員  
 DEBUGREF_INFO_NAME  
 初始化/使用 `bstrName` 結構中的欄位。  
  
 DEBUGREF_INFO_TYPE  
 初始化/使用 `bstrType` 結構中的欄位。  
  
 DEBUGREF_INFO_VALUE  
 初始化/使用 `bstrValue` 結構中的欄位。  
  
 DEBUGREF_INFO_ATTRIB  
 初始化/使用 `dwAttrib` 結構中的欄位。  
  
 DEBUGREF_INFO_REFTYPE  
 初始化/使用 `dwRefType` 結構中的欄位。  
  
 DEBUGREF_INFO_REF  
 初始化/使用 `pReference` 結構中的欄位。  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 值欄位應該包含此類型物件的自動展開值（如果有的話）。  
  
 DEBUGREF_INFO_NONE  
 指出未設定任何旗標。  
  
 DEBUGREF_INFO_ALL  
 指出旗標的遮罩。  
  
## <a name="remarks"></a>備註  
 這些旗標會傳遞至 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 和 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) 方法，以指出要初始化 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 結構的哪些欄位。  
  
 用於結構的 `dwFields` 成員 `DEBUG_REFERENCE_INFO` ，以指出傳回結構時使用的欄位和有效的欄位。  
  
 這些值可能會與位結合 `OR` 。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
