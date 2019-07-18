---
title: IDebugProgramNameChangedEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: abb117d9de09c11bbce1e1c935e108ec940e9c60
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703594"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

程式的名稱變更時傳送從偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM)。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 DE 會實作這個介面，以程式的名稱已變更的報表。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上。 使用 SDM [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)若要存取**IDebugEvent2**介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 DE 建立，並傳送這個事件物件，以報告程式名稱變更。 DE 使用傳送這個事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。 自訂的連接埠提供者會傳送這個事件，使用我的介面。  
  
## <a name="requirements"></a>需求  
 標頭：Msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll
