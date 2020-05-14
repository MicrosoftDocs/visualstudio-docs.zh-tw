---
title: IDebug預設連接埠2::查詢本地 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c06230f7bbd1825fe73a22f9b1fdc35aea35c499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732334"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
此方法確定此埠是否位於本地電腦上。

## <a name="syntax"></a>語法

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>傳回值
 如果`S_OK`此埠是本地的(與調用方在同一台電腦上),或者`S_FALSE`該埠位於另一台電腦上,則返回。

## <a name="see-also"></a>另請參閱
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
