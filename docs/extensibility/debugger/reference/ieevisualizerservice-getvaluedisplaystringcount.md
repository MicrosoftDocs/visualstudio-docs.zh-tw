---
description: 抓取要針對指定的屬性或欄位顯示的值字串數目。
title: IEEVisualizerService：： GetValueDisplayStringCount |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b77e2537e7581bb15f6458b4515d407fcfa1f827
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222844"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
抓取要針對指定的屬性或欄位顯示的值字串數目。

## <a name="syntax"></a>語法

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>參數
`displayKind`\
在來自 [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) 列舉的值。

`propertyOrField`\
在代表屬性或欄位的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 介面。

`pcelt`\
擴展傳回要顯示的值字串數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
