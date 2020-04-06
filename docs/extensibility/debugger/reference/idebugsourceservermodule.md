---
title: IDebugSourceServer模組 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719920"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
表示 PDB 檔中的源伺服器資訊。

## <a name="syntax"></a>語法

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由調試器引擎實現,並由調試器 UI 使用。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugSourceServerModule`。

|方法|描述|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|檢索源伺服器資訊陣組。|

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
