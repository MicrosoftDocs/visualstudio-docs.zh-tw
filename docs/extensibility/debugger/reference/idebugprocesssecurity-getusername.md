---
title: IDebugProcessSecurity::GetUserName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a42b67eb3fd308011bf725f8dd7e24a4d9ddca6f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311528"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
從連接埠提供者取得的使用者名稱。

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
[out]字串，包含使用者名稱。

## <a name="return-value"></a>傳回值
 如果方法成功，它會傳回`S_OK`。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 `GetUserName` 傳回會顯示在使用者名稱**使用者名**資料行**附加至處理序** 對話方塊。 若要檢視**připojit k procesu**  對話方塊中，按一下**附加至處理序**上**工具**功能表[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。

## <a name="see-also"></a>另請參閱
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)