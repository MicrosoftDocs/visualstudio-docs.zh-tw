---
description: 卸離進程中的所有程式，以卸離這個進程的偵錯工具。
title: IDebugProcess2：:D etach |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5775ee9ffc3fa3c4151df999b64ba1160da6f7c3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166277"
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
