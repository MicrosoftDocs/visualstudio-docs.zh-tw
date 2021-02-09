---
title: IDebugIDECallback |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 83243899bdc11c58e76c35b6d9eb7b9555794374
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838652"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 讓運算式評估工具 (EE) 在偵錯工具的輸出視窗中顯示訊息。

## <a name="syntax"></a>Syntax

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 此回呼是由 managed debug 引擎所執行。

## <a name="notes-for-callers"></a>呼叫者注意事項
 運算式評估工具可以使用它來將輸出傳送至偵錯工具的輸出視窗。

## <a name="methods"></a>方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|將指定的訊息字串傳送至偵錯工具的輸出視窗。|

## <a name="requirements"></a>規格需求
 標頭： Ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
