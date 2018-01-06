---
title: "IDebugProgramNodeAttach2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNodeAttach2
helpviewer_keywords: IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1ff6b3aa49030ed49a05cb81e0a949c7bc55806c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
允許的嘗試附加至相關聯的程式通知程式節點。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 實作位於同一個類別會實作這個介面[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)介面以接收通知的附加作業，並提供一個機會，若要取消附加作業。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 取得此介面，藉由呼叫`QueryInterface`方法中的[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件。 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)之前，必須呼叫方法[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法，讓程式節點停止 attach 程序。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|附加至相關聯的程式或延後的附加程序[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。|  
  
## <a name="remarks"></a>備註  
 這個介面是已被取代慣用的替代做法[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)方法。 所有的偵錯引擎會一律載入與`CoCreateInstance`函式中，也就是具現化外部程式偵錯時的位址空間。  
  
 如果先前的實作`IDebugProgramNode2::Attach_V7`方法只需要已設定`GUID`偵錯程式，然後只[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)必須實作的方法。  
  
 如果先前的實作`IDebugProgramNode2::Attach_V7`方法使用所提供的回呼介面，則該功能必須移至的實作[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法和`IDebugProgramNodeAttach2`介面並不會會實作。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)