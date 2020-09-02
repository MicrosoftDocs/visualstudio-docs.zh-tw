---
title: THREADPROPERTY_FIELDS |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc0e0f7cae4aed887809c22bda0cd6a9ed50307f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204807"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定要抓取之執行緒的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>成員  
 TPF_ID  
 初始化/使用 `dwThreadId` [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 結構的欄位。  
  
 TPF_SUSPENDCOUNT  
 初始化/使用 `dwSuspendCount` S 結構的欄位 `THREADPROPERTIE` 。  
  
 TPF_STATE  
 初始化/使用 `dwThreadState` S 結構的欄位 `THREADPROPERTIE` 。  
  
 TPF_PRIORITY  
 初始化/使用 `bstrPriority` S 結構的欄位 `THREADPROPERTIE` 。  
  
 TPF_NAME  
 初始化/使用 `bstrName` S 結構的欄位 `THREADPROPERTIE` 。  
  
 TPF_LOCATION  
 初始化/使用 `bstrLocation` S 結構的欄位 `THREADPROPERTIE` 。  
  
 TPF_ALLFIELDS  
 指定所有欄位。  
  
## <a name="remarks"></a>備註  
 這些值會以引數的形式傳遞至 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) 方法，以指出要初始化 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 結構的哪些欄位。  
  
 這些值也會用在 `dwFields` 結構的成員中， `THREADPROPERTIES` 以指出哪些欄位已使用且有效。  
  
 這些旗標可以與位結合 `OR` 。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
