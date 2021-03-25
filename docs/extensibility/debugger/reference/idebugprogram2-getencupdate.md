---
description: 這個方法會取得此程式的 [編輯後繼續] (ENC) 更新。
title: IDebugProgram2：： GetENCUpdate |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d6b60c8b17a8db1420222a7242164ce1c0eedd1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075922"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
這個方法會取得此程式的 [編輯後繼續] (ENC) 更新。 自訂的 debug engine 一律會傳回 `E_NOTIMPL` 。

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
擴展傳回可用於更新此程式的內部介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

> [!NOTE]
> 自訂的 debug engine 應該一律傳回 `E_NOTIMPL` 。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
