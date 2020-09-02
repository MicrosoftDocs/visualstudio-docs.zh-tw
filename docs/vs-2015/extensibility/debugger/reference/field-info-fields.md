---
title: FIELD_INFO_FIELDS |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3f947db7606d6f7495cb1d88591aafa9e9933b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423708"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定要對 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件取得哪些資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>成員  
 FIF_FULLNAME  
 初始化/使用 `bstrFullName` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 結構中的欄位。  
  
 FIF_NAME  
 初始化/使用 `bstrName` 結構中的欄位 `FIELD_INFO` 。  
  
 FIF_TYPE  
 初始化/使用 `bstrType` 結構中的欄位 `FIELD_INFO` 。  
  
 FIF_MODIFIERS  
 初始化/使用 `bstrModifiers` 結構中的欄位 `FIELD_INFO` 。  
  
## <a name="remarks"></a>備註  
 這些值也會以引數的形式傳遞至 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 方法，以指定要初始化 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 結構的哪些欄位。  
  
 這些值也會用在結構的成員中， `dwFields` `FIELD_INFO` 以指出哪些欄位已使用且有效。  
  
 這些旗標可以與位結合 `OR` 。  
  
## <a name="requirements"></a>需求  
 標頭： sh. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
