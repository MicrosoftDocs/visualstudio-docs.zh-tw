---
title: IDebugNoSymbolevent2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9483c5a434ddfddb3f877111deabea9be6520b05
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726717"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
向[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]調試器 UI 發出訊號,警告使用者無法為啟動的可執行檔找到符號。

## <a name="syntax"></a>語法

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 由調試引擎實現,並由[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]調試器 UI 使用。

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
