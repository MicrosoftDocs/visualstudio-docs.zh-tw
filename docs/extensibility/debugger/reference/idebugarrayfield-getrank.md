---
title: IDebugarrayField:獲取排名 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692f2f13d861d9688ba349fbc80cb1ca426582c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736304"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
獲取陣列的級別或維度數。

## <a name="syntax"></a>語法

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>參數
`pdwRank`\
[出]返回排名。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 陣列的排名對應於維度數。 在C++和C#中,多維陣組實際上是陣列的陣列,因此可以只視為一維陣列(`GetRank`該方法始終返回 1)。 另[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]一方面,多維陣列的處理方式不同,此類陣列的排名反映維度數(`GetRank`該方法始終返回維度數)。

## <a name="see-also"></a>另請參閱
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
