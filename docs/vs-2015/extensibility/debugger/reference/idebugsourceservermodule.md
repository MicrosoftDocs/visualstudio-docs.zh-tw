---
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0dec9408d0cd1907a533a8cabe740832fe652398
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944079"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll
