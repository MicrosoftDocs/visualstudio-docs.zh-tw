---
description: 表示 PDB 檔案中包含的來源伺服器資訊。
title: IDebugSourceServerModule |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b12e93d52fe841b66baae341a6854e0217dcb00
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071164"
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
