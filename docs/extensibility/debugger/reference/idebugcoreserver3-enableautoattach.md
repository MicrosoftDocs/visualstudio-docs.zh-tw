---
title: IDebugCoreServer3：： EnableAutoAttach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732919"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
針對指定的偵錯工具引擎啟用自動附加。

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
