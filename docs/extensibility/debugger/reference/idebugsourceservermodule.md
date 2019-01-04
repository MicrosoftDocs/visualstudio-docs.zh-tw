---
title: IDebugSourceServerModule |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fcdeac3d68b2b26f0613dc92b473a17ce2ffd122
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945791"
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