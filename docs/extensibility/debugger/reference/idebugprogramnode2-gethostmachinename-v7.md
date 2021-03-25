---
title: IDebugProgramNode2：： GetHostMachineName_V7 |Microsoft Docs
description: 這是舊的已被取代的方法，可用來取得 Visual Studio 2005 之前使用的主電腦名稱稱。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20d62c180848c4875fa3312e0194ebdb467a93ca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053538"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> 廢棄。 請勿使用。

## <a name="syntax"></a>語法

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>參數

`pbstrHostMachineName`\
擴展傳回正在執行程式的電腦名稱稱。

## <a name="return-value"></a>傳回值

實作為應一律傳回 `E_NOTIMPL` 。

## <a name="remarks"></a>備註

> [!WARNING]
> 從 Visual Studio 2005，這個方法已不再使用，應該一律傳回 `E_NOTIMPL` 。

## <a name="see-also"></a>另請參閱

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
