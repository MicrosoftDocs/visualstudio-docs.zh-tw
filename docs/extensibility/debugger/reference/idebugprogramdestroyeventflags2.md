---
title: IDebugProgram銷毀事件標誌2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d869304dd8b6dc82db78cc09ed9d51a54acdc3c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722499"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
使調試引擎在結束調試會話時覆蓋[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 的默認行為。

## <a name="syntax"></a>語法

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由調試引擎實現。 對於可能在進程生命週期內創建和銷毀多個程式的主機,它非常有用。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugProgramDestroyEventFlags2`。

|方法|描述|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|檢索程序銷毀標誌。|

## <a name="remarks"></a>備註
 UI[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]的 默認行為是在所有程式都發送程式銷毀事件後返回設計模式。 此介面使調試引擎能夠更改該行為。

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
