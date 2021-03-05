---
description: 設定 debug engine (DE) 的地區設定。
title: IDebugEngine2：： SetLocale |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54cfd2d9d51cbad414cfb481b88f1e3277500efa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153907"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
設定 debug engine (DE) 的地區設定。

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
在指定語言地區設定。 例如，1033（英文）。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 會話 debug manager (SDM) 呼叫這個方法，以傳播 IDE 的地區設定，讓 DE 所傳回的字串適當地當地語系化。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
