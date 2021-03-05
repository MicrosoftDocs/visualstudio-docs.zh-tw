---
description: 當您結束 debug 會話時，可讓 debug engine 覆寫 Visual Studio UI 的預設行為。
title: IDebugProgramDestroyEventFlags2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02b2d934c2a556d3556d494368145e52a8c97394
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168188"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]當您結束 debug 會話時，可讓 debug engine 覆寫 UI 的預設行為。

## <a name="syntax"></a>Syntax

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 這個介面是由偵錯工具引擎所執行。 它適用于可能在進程存留期間建立和終結多個程式的主機。

## <a name="methods"></a>方法
 下表顯示的方法 `IDebugProgramDestroyEventFlags2` 。

|方法|描述|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|抓取程式損毀旗標。|

## <a name="remarks"></a>備註
 UI 的預設行為 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 是在所有程式都已傳送程式損毀事件之後返回設計模式。 這個介面可讓 debug engine 變更該行為。

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
