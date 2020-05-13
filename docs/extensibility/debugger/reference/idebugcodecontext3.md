---
title: IDebugCodeContext3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3f81168d9af7fbbb93b5c59f3ab19a17107b56b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734183"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
擴展[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)介面,以便檢索模組和進程介面。

## <a name="syntax"></a>語法

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>實施者說明
 由調試引擎實現,並由[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]調試包使用。

## <a name="methods"></a>方法
 除了介面上的方法外`IDebugCodeContext2`,此介面還實現以下方法:

|方法|描述|
|------------|-----------------|
|[取得模組](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|檢索對調試模組介面的引用。|
|[抓取程序](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|檢索對調試過程介面的引用。|

## <a name="remarks"></a>備註
 這是一個可選的介面,通常不需要實現。

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
