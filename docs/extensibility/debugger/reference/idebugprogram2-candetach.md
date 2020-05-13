---
title: IDebugProgram2::可分離 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d03d942bbc052a7ac6bebc6a89c55ec21a1b4c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723130"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
確定調試引擎 (DE) 是否可以從程式分離。

## <a name="syntax"></a>語法

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>傳回值
 如果可以分離,則`S_OK`傳回 。否則,返回錯誤代碼。 如果`S_FALSE`DE 無法從程式分離,則返回。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
