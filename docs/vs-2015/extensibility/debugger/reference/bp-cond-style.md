---
title: BP_COND_STYLE |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2674381992bd86f0144af103615f0a3922fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153579"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定暫止和系結中斷點的中斷點條件樣式。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>成員  
 BP_COND_NONE  
 到達中斷點的位置時引發中斷點。 未指定中斷點條件。  
  
 BP_COND_WHEN_TRUE  
 只有當與中斷點相關聯的條件運算式評估為時，才會引發中斷點 `true` 。  
  
 BP_COND_WHEN_CHANGED  
 只有當與中斷點相關聯之條件運算式的值已從其先前的評估變更時，才會引發中斷點。  
  
## <a name="remarks"></a>備註  
 用於 `styleCondition` [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 結構的成員。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
