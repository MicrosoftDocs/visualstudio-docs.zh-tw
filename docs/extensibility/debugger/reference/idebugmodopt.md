---
title: IDebugModOpt |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e142ed1229f59cfc22ff33cba48e9e35eb4e4406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726989"
---
# <a name="idebugmodopt"></a>IDebugModOpt
表示調試可選修改器。

## <a name="syntax"></a>語法

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>通話備註
 從表示類或方法的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)對象獲取。

## <a name="methods"></a>方法
 此介面實現以下方法:

|方法|描述|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|檢索可選修改器的清單。|

## <a name="requirements"></a>需求
 標題: Sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
