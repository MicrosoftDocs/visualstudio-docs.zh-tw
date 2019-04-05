---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945544"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

可讓偵錯引擎覆寫預設行為[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]UI 時結束偵錯工作階段。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 此介面是由偵錯引擎實作。 它適合的主機，可能會建立處理程序的存留期間終結多個程式。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugProgramDestroyEventFlags2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|擷取程式終結旗標。|  
  
## <a name="remarks"></a>備註  
 預設行為[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]UI 是以返回設計模式中所有的程式已送出程式之後終結事件。 此介面可讓偵錯引擎變更該行為。  
  
## <a name="requirements"></a>需求  
 標頭：Msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll
