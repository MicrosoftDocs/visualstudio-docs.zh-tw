---
title: ATTACH_REASON |Microsoft Docs
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
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff2c71418f3586c2915f1d4f4f4ff2fe37ed9bf4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873600"
---
# <a name="attachreason"></a>ATTACH_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定偵錯引擎 (DE) 附加至程式節點的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>成員  
 ATTACH_REASON_AUTO  
 附加，因為處理序目前正在偵錯模式。  
  
 ATTACH_REASON_LAUNCH  
 附加，因為處理序已啟動。  
  
 ATTACH_REASON_USER  
 由於使用者要求附加。  
  
## <a name="remarks"></a>備註  
 這些值用做為參數[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)並[附加](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)

