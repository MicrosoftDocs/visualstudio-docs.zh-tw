---
title: IDebugEngine3::設置我的代碼狀態 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9930f8ecf0c2f9b6fff4ce1c9e3edb935c5a7912
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730680"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
此方法向調試引擎介紹 JustMyCode 狀態資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>參數
`fUpdate`\
[在]非零`TRUE`( ) 更新`FALSE`當前資訊, 零 ( ) 以重置所有資訊(忽略以前設定的任何資訊)。

`dwModules`\
[在]中的資訊結構數量`rgJMCSpec.`

`rgJMCSpec`\
[在][要使用的JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)結構陣組。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 JustMyCode 是僅調試屬於用戶的代碼並忽略所有中間代碼(如系統代碼)的概念,即使原始程式碼可用於該系統代碼也是如此。

## <a name="see-also"></a>另請參閱
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
