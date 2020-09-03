---
title: IEnumDebugProcesses2 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178430"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面會列舉在 debug 埠上執行的處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 自訂埠供應商會執行這個介面，以提供在埠上執行的進程清單。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 Visual Studio 會呼叫 [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) 來取得這個介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IEnumDebugProcesses2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[下一個](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|抓取列舉序列中指定數目的進程。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|略過列舉序列中指定數目的進程。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|將列舉順序重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|取得列舉值中的進程數目。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 使用此介面來填入 **處理** 程式視窗。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
