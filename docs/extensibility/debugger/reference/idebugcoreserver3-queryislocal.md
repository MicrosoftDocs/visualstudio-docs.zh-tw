---
description: 判斷伺服器是否為呼叫端的本機。
title: IDebugCoreServer3：： QueryIsLocal |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::QueryIsLocal
helpviewer_keywords:
- IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e18074c92bdd63c1c378d71d3c84c4dde1745536
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054305"
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
判斷伺服器是否為呼叫端的本機。

## <a name="syntax"></a>語法

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>傳回值
 傳回 `S_OK` ，表示伺服器在本機。 `S_FALSE`如果伺服器是在 msvsmon.exe 的實例（通常用於遠端偵錯）中執行，則會傳回。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
