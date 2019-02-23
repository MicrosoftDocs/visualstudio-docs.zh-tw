---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58684cc5139d2797a08b74d9c0309252141e2498
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723392"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 可讓運算式評估工具 (EE)，才能偵錯工具的 [輸出] 視窗中顯示一則訊息。

## <a name="syntax"></a>語法

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 此回呼是由 managed 偵錯引擎實作。

## <a name="notes-for-callers"></a>呼叫端資訊
 它可供將輸出傳送至偵錯工具的 [輸出] 視窗的運算式評估工具。

## <a name="methods"></a>方法
 這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|將指定的訊息字串傳送至偵錯工具的 [輸出] 視窗中。|

## <a name="requirements"></a>需求
 標頭：Ee.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll