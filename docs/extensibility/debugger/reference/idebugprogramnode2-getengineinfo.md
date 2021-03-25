---
description: 取得 (DE) 執行程式的偵錯工具的名稱和識別碼。
title: IDebugProgramNode2：： GetEngineInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a902db31cb4d48810e673e7807bd3944c2a875
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053525"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
取得 (DE) 執行程式的偵錯工具的名稱和識別碼。

## <a name="syntax"></a>語法

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

## <a name="parameters"></a>參數
`pbstrEngine`\
擴展傳回執行程式 (c + + 特定的執行程式的名稱：這可能是 null 指標，表示呼叫端對引擎) 的名稱不感興趣。

`pguidEngine`\
擴展傳回執行程式 (c + + 特定的全域唯一識別碼：這可以是 null 指標，表示呼叫端對引擎的 GUID) 不感興趣。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
