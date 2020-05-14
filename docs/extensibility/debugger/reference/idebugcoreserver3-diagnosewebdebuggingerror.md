---
title: IDebugCoreServer3::Diagnose網络調試錯誤 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732959"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
嘗試確定自動附加失敗的原因。

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
[在]當前未使用;應始終設定為 null 值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 以下是其他典型的退貨代碼:

|程式碼|描述|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|無法確定遠端伺服器無法啟動調試的原因。|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|無法在遠端伺服器上調試,可能是由於許可權不足或未啟用 DEBUG 謂詞。|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web 伺服器已鎖定並阻止啟用除錯所需的 DEBUG 謂詞。|

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
