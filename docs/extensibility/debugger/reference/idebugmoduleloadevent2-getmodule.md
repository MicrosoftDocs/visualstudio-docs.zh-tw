---
description: 取得正在載入或卸載的模組。
title: IDebugModuleLoadEvent2：： GetModule |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4605b5eab9137fd918238143d8f0453f9f8c54b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065368"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
取得正在載入或卸載的模組。

## <a name="syntax"></a>語法

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>參數
`pModule`\
擴展傳回代表正在載入或卸載之模組的 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 物件。

`pbstrDebugMessage`\
[in，out]傳回描述這個事件的選擇性訊息。 如果此參數為 null 值，則不會要求訊息。

`pbLoad`\
[in，out]如果模組正在載入，則為非零 (`TRUE`) 如果模組正在卸載，則為零 (`FALSE`) 。 如果此參數為 null 值，則不會要求任何狀態。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
