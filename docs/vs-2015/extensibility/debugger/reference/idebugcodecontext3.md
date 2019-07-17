---
title: IDebugCodeContext3 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 62b84bd77038c7a17b65f764bd303d6a6372a52c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154159"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擴充[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)介面，可讓模組和處理程序介面擷取。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 藉由將偵錯引擎，而且由[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]偵錯封裝。  
  
## <a name="methods"></a>方法  
 上的方法除了`IDebugCodeContext2`介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|擷取的偵錯模組介面的參考。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|擷取偵錯處理序的介面的參考。|  
  
## <a name="remarks"></a>備註  
 這是選擇性的介面，但通常不需要實作。  
  
## <a name="requirements"></a>需求  
 標頭：Msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll
