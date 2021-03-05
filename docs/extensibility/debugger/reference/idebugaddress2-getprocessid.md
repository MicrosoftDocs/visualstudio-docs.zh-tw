---
description: 抓取擁有這個 IDebugAddress2 介面所表示之物件的進程識別碼。
title: IDebugAddress2：： GetProcessID |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eeae55e91df8dac3fb176952a352df642facb055
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154947"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
抓取擁有這個 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) 介面所表示之物件的進程識別碼。

## <a name="syntax"></a>語法

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

## <a name="parameters"></a>參數
`pProcID`\
擴展處理序識別碼。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
