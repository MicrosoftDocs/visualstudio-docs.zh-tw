---
title: BP_FLAGS |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b6feb965c564e74dbb026a66a964d233b3ed75fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485084"
---
# <a name="bpflags"></a>BP_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[BP_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-flags)。  
  
提供可用來設定中斷點時，請指定其他資訊的選擇性旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```csharp  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## <a name="members"></a>成員  
 BP_FLAG_NONE  
 不指定任何中斷點旗標。  
  
 BP_FLAG_MAP_DOCPOSITION  
 指定偵錯引擎 (DE) 應該對應使用的文件位置的中斷點。 這是僅適用於指令碼導向的原始程式檔等動態伺服器網頁 (ASP) 中設定中斷點。  
  
 BP_FLAG_DONT_STOP  
 指定偵錯引擎中，應該處理中斷點，但，偵錯引擎最終應該不只如此 (亦即[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)應該不會傳送事件的物件)。 這個旗標被設計用於主要是使用追蹤點。  
  
## <a name="remarks"></a>備註  
 用於`dwFlags`隸屬[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)並[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構。  
  
 這些值可能會合併的位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)

