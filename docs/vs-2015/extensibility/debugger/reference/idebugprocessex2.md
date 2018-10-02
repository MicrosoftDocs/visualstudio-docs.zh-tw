---
title: IDebugProcessEx2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff9e8555df8041a8a4a61b3c4ecca27068419614
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485799"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProcessEx2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocessex2)。  
  
此介面可讓偵錯管理員 (SDM) 通知的程序，它會附加至或從處理序中斷連結的工作階段。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 自訂連接埠供應商的相同物件上實作這個介面[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)介面才能：  
  
-   支援追蹤的工作階段連線到處理程序  
  
-   支援自動附加跨多個偵錯引擎  
  
 自訂連接埠供應商可以實作這個介面，如果選擇。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
  
-   SDM 呼叫[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上`IDebugProcess2`介面，以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugProcessEx2`。  
  
|方法|描述|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|通知程序工作階段現在正在偵錯程序。|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|通知程序工作階段不會再偵錯程序。|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|加入程式節點，如需偵錯引擎的清單。|  
  
## <a name="remarks"></a>備註  
 這個介面是 SDM 和處理序之間的私用。  
  
## <a name="requirements"></a>需求  
 標頭： Portpriv.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

