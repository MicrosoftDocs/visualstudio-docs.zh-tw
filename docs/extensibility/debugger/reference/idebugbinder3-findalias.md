---
title: IDebugBinder3::查找別名 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735871"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
此方法定位一個別名,給定一個名稱。 這將搜索程式中的所有別名。

## <a name="syntax"></a>語法

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>參數
`pcstrName`\
[在]要查找的別名的名稱。

`ppAlias`\
[出]找到(如果有)由[IDebugAlias 介面](../../../extensibility/debugger/reference/idebugalias.md)表示的別名。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回`S_FALSE`(如果未找到別名)或錯誤代碼。

## <a name="remarks"></a>備註
 此方法在調用之前將目標物件初始化為 null;然後,它會在之後測試一個空值,以確定是否找到別名。

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
