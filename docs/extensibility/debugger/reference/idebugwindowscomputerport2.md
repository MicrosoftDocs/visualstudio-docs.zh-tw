---
title: IDebugWindows計算機埠2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ef4162469651e4b69502d3a9639d1e86c62e0b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718221"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
允許查詢有關目標計算機的資訊。

## <a name="syntax"></a>語法

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由會話調試管理器的埠對象實現。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugWindowsComputerPort2`。

|方法|描述|
|------------|-----------------|
|[取得電腦資訊](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|檢索有關調試器運行的計算機的資訊。|

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
