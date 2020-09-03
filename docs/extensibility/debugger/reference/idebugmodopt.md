---
title: IDebugModOpt |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726989"
---
# <a name="idebugmodopt"></a>IDebugModOpt
表示 debug 選擇性修飾詞。

## <a name="syntax"></a>語法

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

## <a name="requirements"></a>需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
