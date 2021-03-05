---
description: IDebugProgramNode2：： GetProgramName 取得程式的名稱。
title: IDebugProgramNode2：： GetProgramName |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88a4bc58f5d91cdb52482f4dc862446cfc9e7eb1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161381"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
取得程式的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

## <a name="parameters"></a>參數
`pbstrProgramName`\
擴展傳回程序的名稱。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
程式的名稱和程式的路徑不同，不過程式的名稱可能是這類路徑的一部分。

## <a name="example"></a>範例
下列範例示範如何針對實 IDebugProgramNode2 介面的簡單物件，執行這個方法 `CProgram` 。 [](../../../extensibility/debugger/reference/idebugprogramnode2.md) 函數會將 `MakeBstr` 指定之字串的複本配置為 BSTR。

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
