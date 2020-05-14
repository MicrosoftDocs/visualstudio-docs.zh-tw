---
title: IDebugProgram2::獲取更新 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e90ff9f8a7a80913aec72b9fe2bb6fe470013d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722845"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
此方法獲取此程式的編輯並繼續 (ENC) 更新」。 自訂除錯引擎始終傳`E_NOTIMPL`回 。

## <a name="syntax"></a>語法

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>參數
`ppUpdate`\
[出]返回可用於更新此程式的內部介面。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

> [!NOTE]
> 自訂除錯引擎應傳回`E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
