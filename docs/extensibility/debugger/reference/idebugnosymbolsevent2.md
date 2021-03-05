---
description: 向 Visual Studio 偵錯工具 UI 發出警告，以警告使用者已啟動的可執行檔找不到符號。
title: IDebugNoSymbolsEvent2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859c9c1d07a5f4660f2d13dcffac4f19659a2bc2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149817"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
通知 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 偵錯工具 UI 警告使用者，找不到已啟動可執行檔的符號。

## <a name="syntax"></a>Syntax

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 由偵錯工具 UI 所執行，並由調試 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 程式 UI 使用。

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
