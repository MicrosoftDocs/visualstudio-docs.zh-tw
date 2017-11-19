---
title: "IDebugProgramDestroyEventFlags2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bee4fe04f22bd9afbff8e2d26ef9d699b0226241
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
可讓偵錯引擎，將覆寫預設行為[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 偵錯工作階段結束時。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 實作這個介面是由偵錯引擎。 它可用於主機，可能會建立並終結多個程式的處理序存留期。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugProgramDestroyEventFlags2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|擷取程式旗標會終結。|  
  
## <a name="remarks"></a>備註  
 預設行為[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 是以返回設計模式之後，所有的程式已送出程式損毀事件。 此介面可讓偵錯引擎變更該行為。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll