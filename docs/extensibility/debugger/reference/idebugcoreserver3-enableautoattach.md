---
description: 針對指定的偵錯工具引擎啟用自動附加。
title: IDebugCoreServer3：： EnableAutoAttach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e3b78744d67183c368345af8c6c26e57edec8d1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058673"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
針對指定的偵錯工具引擎啟用自動附加。

## <a name="syntax"></a>語法

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>參數
`rgguidSpecificEngines`\
在要標示為自動附加的每個偵錯工具引擎的 Guid 陣列。

`celtSpecificEngines`\
在中指定的引擎數目 `rgguidSpecificEngines` 。

`pszStartPageUrl`\
在自動附加時所要使用的起始 URL。

`pbstrSessionID`\
擴展已自動附加之會話的識別碼。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 其中一個錯誤碼是 `E_AUTO_ATTACH_NOT_REGISTERED` ，表示尚未註冊自動附加類別 factory。

## <a name="remarks"></a>備註
 當與指定之 URL 相關聯的程式啟動時，會自動啟動並附加指定的偵錯工具引擎。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
