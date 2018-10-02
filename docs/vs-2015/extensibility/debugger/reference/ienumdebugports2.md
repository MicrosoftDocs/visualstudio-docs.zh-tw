---
title: IEnumDebugPorts2 |Microsoft Docs
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
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9ff7eac1da5cba43bf93a352e571c7a1f912932b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498256"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IEnumDebugPorts2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugports2)。  
  
此介面列舉電腦或連接埠的供應商的連接的埠。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 自訂的連接埠提供者會實作這個介面來代表供應商所建立的連接埠清單。 Visual Studio 會實作這個介面來支援它自己的連接埠提供者。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)來取得這個介面，表示連接埠提供者所建立的連接埠清單。 呼叫[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)來取得這個介面，表示已儲存的連接埠清單到磁碟。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugPorts2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|擷取指定的數目的列舉型別序列中的連接埠。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|略過指定的數目的列舉型別序列中的連接埠。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|將列舉型別序列重設到開頭。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|取得列舉值中的連接埠數目。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會使用此介面，以便填入用來附加至處理序的連接埠清單。  
  
 偵錯引擎通常不使用此介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)

