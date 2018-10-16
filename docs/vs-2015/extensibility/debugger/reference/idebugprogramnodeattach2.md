---
title: IDebugProgramNodeAttach2 |Microsoft Docs
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
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 752d863deb3f44f0cc2a36ce6e32db879225c2c1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258384"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

允許程式節點，嘗試附加至相關聯的程式的通知。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 實作在相同類別上實作這個介面[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)介面以接收通知的附加作業，並提供機會，以取消在附加作業。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 取得這個介面，藉由呼叫`QueryInterface`方法中的[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件。 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)之前，必須呼叫方法[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法，以提供 [程式] 節點停止附加處理序的機會。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|將附加至相關聯的程式，或是遵照的附加程序[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。|  
  
## <a name="remarks"></a>備註  
 這個介面是慣用的替代做法已被取代[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)方法。 所有偵錯引擎一律會載入與`CoCreateInstance`函式中，也就是它們正在偵錯之程式的位址空間之外具現化。  
  
 如果先前的實作`IDebugProgramNode2::Attach_V7`方法只需要設定`GUID`偵錯程式，然後只[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法需要實作。  
  
 如果先前的實作`IDebugProgramNode2::Attach_V7`方法使用所提供的回呼介面，則該功能必須要實作移動[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法和`IDebugProgramNodeAttach2`介面則否必須實作。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

