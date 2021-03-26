---
description: 表示用來選取埠的自訂 UI。
title: IDebugPortPicker |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8390c8a055a9c919bb1a35d8f3288fc810e5329d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072243"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
表示用來選取埠的自訂 UI。

## <a name="syntax"></a>Syntax

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 此介面是由埠供應商所執行。 埠供應商會以 CLSID 的形式公開，並將計量指向公開的 CLSID，以定義其埠選擇器 `metricPortPickerCLSID` 。

## <a name="methods"></a>方法
 下表顯示的方法 `IDebugPortPicker` 。

|方法|描述|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|顯示允許使用者選取埠的指定對話方塊。|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|設定服務提供者。|

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
