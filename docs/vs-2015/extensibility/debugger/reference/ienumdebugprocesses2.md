---
title: IEnumDebugProcesses2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d56d284d08a1c6b55318300ef7e1db1e385d584e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178430"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面會列舉在偵錯連接埠上執行的處理程序。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 自訂的連接埠提供者會實作這個介面來提供連接埠上執行的處理序的清單。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 Visual Studio 呼叫[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)來取得這個介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugProcesses2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一個](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|擷取指定的數目的列舉型別序列中的程序。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|略過指定的數目的列舉型別序列中的程序。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|將列舉型別序列重設到開頭。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|取得列舉值中的處理序數目。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會使用此介面來填入**處理序**視窗。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
