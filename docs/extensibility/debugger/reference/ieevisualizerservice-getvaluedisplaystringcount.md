---
title: IEE視覺化服務::獲取價值顯示字串計數 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c1a664594e55b8db21562a650c2c750668c2584
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717996"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
檢索要為指定屬性或欄位顯示的值字串數。

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
[在][顯示金德](../../../extensibility/debugger/reference/displaykind.md)枚舉中的值。

`propertyOrField`\
[在]表示屬性或欄位的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。

`pcelt`\
[出]返回要顯示的值字串數。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
