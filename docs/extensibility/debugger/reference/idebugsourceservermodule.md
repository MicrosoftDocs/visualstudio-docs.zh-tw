---
description: 表示 PDB 檔案中包含的來源伺服器資訊。
title: IDebugSourceServerModule |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74fa5f3aafea5f709777bbead81743c7c5aef358
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164639"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
表示 PDB 檔案中包含的來源伺服器資訊。

## <a name="syntax"></a>Syntax

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 此介面是由偵錯工具引擎所執行，並由偵錯工具 UI 取用。

## <a name="methods"></a>方法
 下表顯示的方法 `IDebugSourceServerModule` 。

|方法|描述|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|捕獲來源伺服器資訊的陣列。|

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
