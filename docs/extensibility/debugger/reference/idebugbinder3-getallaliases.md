---
description: 這個方法會從程式抓取別名清單。
title: IDebugBinder3：： GetAllAliases |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04e4f9887ff8cfa68ad4fd4b09d160e3ec2d1eaf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085165"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
這個方法會從程式抓取別名清單。

## <a name="syntax"></a>語法

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>參數
`uRequest`\
在要傳回的別名數目上限 (指定傳遞至) 的陣列長度 `ppAliases` 。

`ppAliases`\
[in，out]要填入別名的陣列 (如果這是 null 值且 `uRequest` 為0，則) 會傳回可傳回的別名計數 `puFetched` 。

`puFetched`\
擴展傳回取得的別名數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
