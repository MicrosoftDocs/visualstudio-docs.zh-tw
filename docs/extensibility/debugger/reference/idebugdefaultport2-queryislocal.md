---
description: 這個方法會判斷這個埠是否在本機電腦上。
title: IDebugDefaultPort2：： QueryIsLocal |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f732de2526aa71698b4c01a636dab541050015a5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150636"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
這個方法會判斷這個埠是否在本機電腦上。

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
 `S_OK`如果此埠在與呼叫端相同的電腦上是本機 (，或在 `S_FALSE` 另一部電腦上，則會) 傳回。

## <a name="see-also"></a>另請參閱
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
