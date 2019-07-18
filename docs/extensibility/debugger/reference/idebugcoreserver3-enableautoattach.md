---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9eb8beed7f32e9c6fb64212f73a41a35544259bb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326978"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
可讓自動附加指定的偵錯引擎。

## <a name="syntax"></a>語法

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>參數
`rgguidSpecificEngines`\
[in]每個偵錯引擎將標示為自動附加 Guid 的陣列。

`celtSpecificEngines`\
[in]中指定的引擎數`rgguidSpecificEngines`。

`pszStartPageUrl`\
[in]若要使用自動附加時起始的 URL。

`pbstrSessionID`\
[out]已自動附加的工作階段識別碼。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 一個錯誤碼是`E_AUTO_ATTACH_NOT_REGISTERED`，這表示尚未註冊 auto-attach class factory。

## <a name="remarks"></a>備註
 使用指定的 URL 相關聯的程式啟動時，將指定的偵錯引擎會自動啟動和附加。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)