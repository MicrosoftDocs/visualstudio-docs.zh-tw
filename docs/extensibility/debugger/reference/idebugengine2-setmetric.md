---
title: IDebugEngine2::設置指標 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: caada8db1791d94e7a9632394cd4659bf8cec3a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730905"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
此方法設置稱為指標的註冊表值。

## <a name="syntax"></a>語法

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>參數
`pszMetric`\
[在]指標名稱。

`varValue`\
[在]指定指標值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 指標是用於更改調試引擎的行為或通告支援的功能的註冊表值。 此方法可以將呼叫到用於除錯功能的 SDK[協助器](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)的適當`SetMetric`形式 。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
