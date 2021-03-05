---
description: 允許查詢目的電腦的相關資訊。
title: IDebugWindowsComputerPort2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a9c7e940c2284b5b39097226f9a5b0c3b34a0d18
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222948"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
允許查詢目的電腦的相關資訊。

## <a name="syntax"></a>Syntax

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 這個介面是由會話偵錯工具管理員的埠物件所執行。

## <a name="methods"></a>方法
 下表顯示的方法 `IDebugWindowsComputerPort2` 。

|方法|描述|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|抓取正在執行之偵錯工具的電腦相關資訊。|

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
