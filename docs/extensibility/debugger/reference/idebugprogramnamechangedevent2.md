---
title: IDebug程式名稱更改事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae58728601c3adbe6e37a00fd0694a5d71eef0b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722156"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
當程式名稱更改時,從除錯引擎 (DE) 傳送到工作階段除錯管理員 (SDM)。

## <a name="syntax"></a>語法

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面以報告程式的名稱已更改。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現。 SDM 使用[查詢介面](/cpp/atl/queryinterface)訪問**IDebugEvent2**介面。

## <a name="notes-for-callers"></a>通話備註
 DE 創建並發送此事件物件以報告程式名稱更改。 DE 使用 SDM 在連接到正在除錯的程式時提供的[IDebugEvent 回檔2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔函數發送此事件。 自定義埠供應商使用 I 介面發送此事件。

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
