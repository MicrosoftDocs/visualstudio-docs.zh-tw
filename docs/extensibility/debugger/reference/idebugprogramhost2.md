---
description: 此介面提供主機 (程式) 程式的相關資訊。
title: IDebugProgramHost2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6b58eb61a65ff8ed0a6455d81128539ad5e6d00a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058244"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
此介面提供主機 (程式) 程式的相關資訊。

## <a name="syntax"></a>Syntax

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 偵錯工具引擎會在與 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 介面相同的物件上執行這個介面，以提供裝載進程的相關資訊。 這是選擇性的介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫介面上的 [QueryInterface](/cpp/atl/queryinterface) `IDebugProgram2` 來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugProgramHost2` 。

|方法|描述|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|取得此程式之裝載進程的標題、易記名稱或檔案名。|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|取得此程式之裝載進程的處理序識別碼。|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|取得此程式的裝載進程正在其上執行的電腦名稱稱。|

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
