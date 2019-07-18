---
title: IDebugModOpt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 66f499225d2b319f3678c88894a1217d90b10135
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68162512"
---
# <a name="idebugmodopt"></a>IDebugModOpt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

表示偵錯的選擇性修飾詞。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugModOpt : IUnknown  
```  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 取自[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，表示類別或方法。  
  
## <a name="methods"></a>方法  
 這個介面會實作下列方法：  
  
|方法|說明|  
|------------|-----------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|擷取一份選擇性修飾詞。|  
  
## <a name="requirements"></a>需求  
 標頭：Sh.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll
