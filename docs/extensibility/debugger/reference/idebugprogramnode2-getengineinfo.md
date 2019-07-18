---
title: IDebugProgramNode2::GetEngineInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d49bbaf4ca4b4d85d198eeb51b2eb4d13508d39
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351150"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
取得名稱和執行程式的偵錯引擎 (DE) 的識別碼。

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
[out]傳回的執行程式的預設名稱 (C++-特定： 這可以是 null 指標，指出呼叫端不想在引擎的名稱)。

`pguidEngine`\
[out]傳回執行程式 DE 的全域唯一識別碼 (C++-特定： 這可以是 null 指標，表示呼叫端不感興趣的引擎 GUID)。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)