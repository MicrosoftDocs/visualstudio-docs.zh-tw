---
title: IDebugIDE回撥 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 585ff354cef9686097325ea4dea25cd08c4cbb1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727834"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 使運算式賦值器 (EE) 能夠在除錯器的輸出視窗中顯示消息。

## <a name="syntax"></a>語法

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此回調由託管調試引擎實現。

## <a name="notes-for-callers"></a>通話備註
 表達式賦值器可以使用它將輸出發送到調試器的輸出視窗。

## <a name="methods"></a>方法
 此介面實現以下方法:

|方法|描述|
|------------|-----------------|
|[顯示訊息](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|將指定的消息字串發送到除錯器的輸出視窗。|

## <a name="requirements"></a>需求
 標題: Ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
