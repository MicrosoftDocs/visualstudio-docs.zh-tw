---
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2032620653b1e7733664ca40113dcb0cffd418f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922101"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
表示包含在 PDB 檔案中的來源伺服器資訊。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 此介面是由偵錯工具引擎實作，並供偵錯工具 UI。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugSourceServerModule`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|擷取來源伺服器資訊的陣列。|  
  
## <a name="requirements"></a>需求  
 標頭：Msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll