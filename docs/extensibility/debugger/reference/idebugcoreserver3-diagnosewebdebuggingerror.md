---
description: 嘗試判斷自動附加失敗的原因。
title: IDebugCoreServer3：:D iagnoseWebDebuggingError |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95e54add3616fa0ec97f4114b4cd628213e752f9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154687"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
嘗試判斷自動附加失敗的原因。

## <a name="syntax"></a>語法

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>參數
`pszUrl`\
在目前未使用;應該一律設定為 null 值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 以下是其他一般傳回碼：

|程式碼|描述|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|無法判斷遠端伺服器無法啟動調試的原因。|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|無法在遠端伺服器上進行偵錯工具，可能是因為許可權不足或偵錯工具動詞未啟用。|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web 服務器已經鎖定，並封鎖了啟用偵錯工具所需的偵錯工具動詞。|

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
