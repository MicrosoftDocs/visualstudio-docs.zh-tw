---
description: 在指定的 debug 位址抓取方法的相關資訊。
title: IDebugSymbolProviderDirect：： GetMethodFromAddress |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 306cb3bbe863ed0d8ca37c50b44158ea087ac015
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071086"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
在指定的 debug 位址抓取方法的相關資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMethodFromAddress(
   IDebugAddress* pAddress,
   GUID*          pGuid,
   DWORD*         pAppID,
   _mdToken*      pTokenClass,
   _mdToken*      pTokenMethod,
   DWORD*         pdwOffset,
   DWORD*         pdwVersion
);
```

```csharp
int GetMethodFromAddress(
   IDebugAddress pAddress,
   out Guid      pGuid,
   out uint      pAppID,
   out uint      pTokenClass,
   out uint      pTokenMethod,
   out uint      pdwOffset,
   out uint      pdwVersion
);
```

## <a name="parameters"></a>參數
`pAddress`\
在 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面所代表的 Debug 位址。

`pGuid`\
擴展模組的唯一識別碼。

`pAppID`\
擴展應用程式域的識別碼。

`pTokenClass`\
擴展代表包含類別的 Token。

`pTokenMethod`\
擴展代表模組的 Token。

`pdwOffset`\
擴展從參數開頭算起的位移（以位元組為單位） `pAddress` 。

`pdwVersion`\
擴展方法的版本號碼。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
