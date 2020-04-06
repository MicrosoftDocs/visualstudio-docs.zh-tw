---
title: IDebugProcess 安全性:獲取使用者名 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef00a0b7489c3e5cb709520546f3d3f26c8a4eba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723253"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
從埠供應商獲取使用者名。

## <a name="syntax"></a>語法

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>參數
`pbstrUserName`\
[出]包含使用者名的字串。

## <a name="return-value"></a>傳回值
 如果方法成功，它會傳回 `S_OK`。 否則,它將返回一個錯誤代碼。

## <a name="remarks"></a>備註
 `GetUserName`傳回「**附加到行程**」 對話框的 **「使用者名**」列中顯示的使用者名稱。 要查看「**附加到流程**」對話框,請[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]按一下 整合式開發環境 (IDE) 中的 **「工具**」功能表上的 **「附加到行程**」 。

## <a name="see-also"></a>另請參閱
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
