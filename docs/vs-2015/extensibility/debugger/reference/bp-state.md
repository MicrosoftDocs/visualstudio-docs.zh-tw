---
title: BP_STATE |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4de23d462136ad417859d7064fef6b4ace7e59c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153256"
---
# <a name="bp_state"></a>BP_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定系結中斷點是否存在，並指定是否已啟用。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```csharp  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>成員  
 BPS_NONE  
 指定不存在任何中斷點。  
  
 BPS_DELETED  
 指定中斷點已刪除。  
  
 BPS_DISABLED  
 指定停用中斷點。  
  
 BPS_ENABLED  
 指定中斷點已啟用。  
  
## <a name="remarks"></a>備註  
 從 [>getstate](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) 方法傳回。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [>getstate](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
