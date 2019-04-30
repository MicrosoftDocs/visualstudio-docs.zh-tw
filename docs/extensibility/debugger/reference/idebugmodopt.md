---
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1bbfbc6b6e567e0e56aa369f9c0d1f13a4cbe34
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918630"
---
# <a name="idebugmodopt"></a>IDebugModOpt
表示偵錯的選擇性修飾詞。

## <a name="syntax"></a>語法

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>呼叫端資訊
 取自[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，表示類別或方法。

## <a name="methods"></a>方法
 這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|擷取一份選擇性修飾詞。|

## <a name="requirements"></a>需求
 標頭：Sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll