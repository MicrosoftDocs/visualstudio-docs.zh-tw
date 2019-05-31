---
title: IDebugArrayField::GetRank |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33d5118ffa045ccc2315ccb596850be6922fc2ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321681"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
取得的順位或陣列的維度數目。

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
[out]傳回順位。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 陣列陣序對應至維度的數目。 在C++和C#，多維度陣列其實是陣列的陣列，因此可被視為只是一維陣列 (和`GetRank`方法一律會傳回 1)。 在 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]相反地，多維度陣列的處理方式不同，這類陣列的陣序反映的維度數目 (和`GetRank`方法一律會傳回的維度數目)。

## <a name="see-also"></a>另請參閱
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)