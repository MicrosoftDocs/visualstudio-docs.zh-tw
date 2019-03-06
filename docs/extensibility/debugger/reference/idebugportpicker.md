---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 845e197b186d462b74aaf8cf3cd7218e4606dfc7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716541"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
代表自訂的 UI 中選取連接埠。

## <a name="syntax"></a>語法

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 連接埠提供者會實作這個介面。 連接埠提供者會定義將其公開為 CLSID，並指向其連接埠選擇器`metricPortPickerCLSID`計量在公開的 CLSID。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugPortPicker`。

|方法|描述|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|顯示指定的對話方塊中，可讓使用者選取一個連接埠。|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|設定服務提供者。|

## <a name="requirements"></a>需求
 標頭：Msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll