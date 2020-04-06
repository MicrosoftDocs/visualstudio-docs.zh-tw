---
title: IDebugProgramnode2::獲取引擎資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2e74ba3c0f826314818bc883778a6364ff3fb6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722096"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
取得執行程式的除錯引擎 (DE) 的名稱和識別碼。

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
[出]返回運行程式的 DE 的名稱(特定於 C++:這可以是一個空指標,指示調用方對引擎的名稱不感興趣)。

`pguidEngine`\
[出]返回運行程式的 DE 的全域唯一標識符(特定於 C++:這可以是一個空指標,指示呼叫方對引擎的 GUID 不感興趣)。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
