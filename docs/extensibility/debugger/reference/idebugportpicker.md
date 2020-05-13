---
title: IDebugPortPicker |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 554ac24d7148f0d5de07779f35376b28b7ff7b07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724842"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
表示用於選擇埠的自定義 UI。

## <a name="syntax"></a>語法

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由埠供應商實現。 埠供應商通過將埠選取器公開為 CLSID 並將`metricPortPickerCLSID`指標指向公開的 CLSID 來定義其埠選取器。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugPortPicker`。

|方法|描述|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|顯示允許用戶選擇埠的指定對話方塊。|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|設置服務提供者。|

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
