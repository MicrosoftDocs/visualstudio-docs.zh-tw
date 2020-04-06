---
title: IDebug程式節點2::獲取程式名稱 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9af930716725a62fff5ea3d1635b506b06b26086
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721994"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
獲取程式的名稱。

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
[出]返回程式的名稱。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
程式的名稱與程式的路徑不同,儘管程式的名稱可能是此類路徑的一部分。

## <a name="example"></a>範例
下面的範例展示如何實現[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)介面`CProgram`的簡單物件實現此方法。 該`MakeBstr`函數將指定字串的副本分配為 BSTR。

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
