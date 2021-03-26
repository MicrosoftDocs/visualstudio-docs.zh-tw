---
description: 卸離進程中的所有程式，以卸離這個進程的偵錯工具。
title: IDebugProcess2：:D etach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d75f9dd58e2a26f6d465fc93988fa3d3785a0d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071658"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
卸離進程中的所有程式，以卸離這個進程的偵錯工具。

## <a name="syntax"></a>語法

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 所有程式和進程會繼續執行，但不再是 debug 會話的一部分。 卸離作業完成之後，就不會再 (此進程的任何偵錯工具事件，而且會傳送) 的程式。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
