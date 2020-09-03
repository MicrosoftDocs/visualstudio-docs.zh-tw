---
title: FIELD_KIND_EX |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e6384ea963fe1da145cacc0be46b5989f7bc610
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198762"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

列舉 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件可以包含的其他欄位類型。 此列舉會擴充 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 列舉。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
} ;  
typedef DWORD FIELD_KIND_EX;  
```  
  
```csharp  
public enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
};  
```  
  
## <a name="members"></a>成員  
 FIELD_KIND_EX_NONE  
 欄位未包含擴充類型。  
  
 FIELD_TYPE_EX_METHODVAR  
 欄位包含方法變數。  
  
 FIELD_TYPE_EX_CLASSVAR  
 欄位包含類別變數。  
  
## <a name="requirements"></a>需求  
 標頭： Sh. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
