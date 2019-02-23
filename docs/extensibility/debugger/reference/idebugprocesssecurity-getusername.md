---
title: IDebugProcessSecurity::GetUserName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8340e9fd9e5f38963a9de78e2974404f600deef
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686167"
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

#### <a name="parameters"></a>參數
 `pbstrUserName`

 [out]字串，包含使用者名稱。

## <a name="return-value"></a>傳回值
 如果方法成功，它會傳回`S_OK`。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 `GetUserName` 傳回會顯示在使用者名稱**使用者名**資料行**附加至處理序** 對話方塊。 若要檢視**připojit k procesu**  對話方塊中，按一下**附加至處理序**上**工具**功能表[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。

## <a name="see-also"></a>另請參閱
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)