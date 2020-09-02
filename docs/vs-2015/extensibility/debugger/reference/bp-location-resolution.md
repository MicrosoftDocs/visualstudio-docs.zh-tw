---
title: BP_LOCATION_RESOLUTION |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_LOCATION_RESOLUTION
helpviewer_keywords:
- BP_LOCATION_RESOLUTION structure
ms.assetid: 86ea2c8a-54a3-48e8-83c7-18a515273129
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d24ae48df790e452145e5aa8c67998d55760bb24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153423"
---
# <a name="bp_location_resolution"></a>BP_LOCATION_RESOLUTION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

描述中斷點在特定位置的解決方式。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
typedef struct _BP_LOCATION_RESOLUTION {   
   IDebugBreakpointResolution2* pResolution;  
} BP_LOCATION_RESOLUTION;  
```  
  
## <a name="members"></a>成員  
 pResolution  
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)物件，可決定中斷點的類型及其解析資訊。  
  
## <a name="remarks"></a>備註  
 此結構是 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 結構的成員，做為聯集的一部分。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
