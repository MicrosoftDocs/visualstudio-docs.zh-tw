---
title: IDebugProgramDestroyEventFlags2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 86f7e211c742e4d95f3459d058139854874e7d85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182210"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]當您結束 debug 會話時，可讓 debug engine 覆寫 UI 的預設行為。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 這個介面是由偵錯工具引擎所執行。 它適用于可能在進程存留期間建立和終結多個程式的主機。  
  
## <a name="methods"></a>方法  
 下表顯示的方法 `IDebugProgramDestroyEventFlags2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|抓取程式損毀旗標。|  
  
## <a name="remarks"></a>備註  
 UI 的預設行為 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 是在所有程式都已傳送程式損毀事件之後返回設計模式。 這個介面可讓 debug engine 變更該行為。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll
