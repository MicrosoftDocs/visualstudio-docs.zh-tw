---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae51d604f455b12fd6933a54954b75a97aea4eb7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547464"
---
# <a name="moduleflags"></a>MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

用來描述模組。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```csharp  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## <a name="members"></a>成員  
 MODULE_FLAG_NONE  
 指定沒有模組。  
  
 MODULE_FLAG_SYSTEM  
 指定系統模組。  
  
 MODULE_FLAG_SYMBOLS  
 指定符號的模組。  
  
 MODULE_FLAG_64BIT  
 指定 64 位元模組。  
  
 MODULE_FLAG_OPTIMIZED  
 指定模組已經過最佳化。 此狀態會反映在**模組**視窗。  
  
 MODULE_FLAG_UNOPTIMIZED  
 指定模組尚未經過最佳化。 此狀態會反映在**模組**視窗。 這是預設狀態。  
  
## <a name="remarks"></a>備註  
 用於`m_dwModuleFlags`隸屬[MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構。  
  
 這些旗標可能會結合的位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
