---
description: 取得在執行此程式時， (DE) 的偵測引擎的名稱和 GUID。
title: IDebugProgram2：： GetEngineInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetEngineInfo
helpviewer_keywords:
- IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8cf4dea1d85b6703b303ecf03d2080047f052458
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075857"
---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
取得在執行此程式時， (DE) 的偵測引擎的名稱和 GUID。

## <a name="syntax"></a>語法

```cpp
HRESULT GetEngineInfo( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo( 
   out string pbstrEngine,
   out GUID   pguidEngine
);
```

## <a name="parameters"></a>參數
`pbstrEngine`\
擴展傳回執行此程式之 DE 的名稱。

`pguidEngine`\
擴展傳回執行此程式之 DE 的 GUID。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 每個 DE 都會定義自己的 GUID 以進行識別。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
