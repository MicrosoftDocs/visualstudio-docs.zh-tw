---
title: BP_ERROR_RESOLUTION_INFO |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 246cdc245d6b6828eee7cd60e1aa94c487b77905
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153553"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

描述錯誤中斷點的解決方式，包括位置、程式和執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## <a name="members"></a>成員  
 `dwFields`  
 [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)列舉值的組合，指定要填入此結構的哪些欄位。  
  
 `bpResLocation`  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)聯集，指定中斷點解析位置。  
  
 `pProgram`  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，代表發生中斷點錯誤的應用程式。  
  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，代表產生中斷點錯誤的應用程式正在其上執行的執行緒。  
  
 `bstrMessage`  
 字串，包含此錯誤解決所產生的任何警告或錯誤訊息。  
  
 `dwType`  
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)列舉中的值，指定中斷點錯誤類型。  
  
## <a name="remarks"></a>備註  
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)方法會傳回這個結構。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
