---
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c40a2da886b4e999649349d4af306295c87863ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916073"
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

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll