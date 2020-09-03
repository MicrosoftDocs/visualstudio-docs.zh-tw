---
title: IDebugSourceServerModule |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2c362bc4a103c707238acfa3b3148f00c0e25be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719920"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
表示 PDB 檔案中包含的來源伺服器資訊。

## <a name="syntax"></a>語法

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

## <a name="requirements"></a>需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
