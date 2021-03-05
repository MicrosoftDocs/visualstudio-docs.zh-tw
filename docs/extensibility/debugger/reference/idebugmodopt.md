---
description: 表示 debug 選擇性修飾詞。
title: IDebugModOpt |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 047c01f78931e1b13110640952c67c11a68bc8a2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149856"
---
# <a name="idebugmodopt"></a>IDebugModOpt
表示 debug 選擇性修飾詞。

## <a name="syntax"></a>Syntax

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>呼叫者注意事項
 從代表類別或方法的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件取得。

## <a name="methods"></a>方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|抓取選用修飾詞的清單。|

## <a name="requirements"></a>規格需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
