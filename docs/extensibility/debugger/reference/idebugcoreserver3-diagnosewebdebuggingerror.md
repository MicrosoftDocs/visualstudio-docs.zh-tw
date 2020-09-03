---
title: IDebugCoreServer3：:D iagnoseWebDebuggingError |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fec5b8fbe1cae18b8221702fe14443df231d8880
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732959"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
嘗試判斷自動附加失敗的原因。

## <a name="syntax"></a>語法

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
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
