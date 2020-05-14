---
title: IDebugEngine2::設置局部性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8616dd827f99dfcfbc337cb5cdf5ac5a7d392e88
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730910"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
設置調試引擎 (DE) 區域設置。

## <a name="syntax"></a>語法

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale( 
   ushort wLangID
);
```

## <a name="parameters"></a>參數
`wLangID`\
[在]指定語言區域設置。 例如,英語為 1033。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 工作階段除錯管理員 (SDM) 呼叫此方法來傳播 IDE 的區域設定,以便 DE 傳回的字串正確當地語系化。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
