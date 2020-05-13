---
title: IDebugProgramNode2::GetHostMachineName_V7 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8c328c83ebe52f842b1990debe07aed3fd764c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722079"
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
[出]返回運行程式的電腦的名稱。

## <a name="return-value"></a>傳回值

實現應始終返回`E_NOTIMPL`。

## <a name="remarks"></a>備註

> [!WARNING]
> 自 Visual Studio 2005 起,此方法不再使用`E_NOTIMPL`,應始終返回 。

## <a name="see-also"></a>另請參閱

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
