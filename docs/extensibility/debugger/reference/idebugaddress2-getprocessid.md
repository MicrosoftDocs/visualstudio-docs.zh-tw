---
description: 抓取擁有這個 IDebugAddress2 介面所表示之物件的進程識別碼。
title: IDebugAddress2：： GetProcessID |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd7665af4f88c695dd74b51293da3eced3861230
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059193"
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
