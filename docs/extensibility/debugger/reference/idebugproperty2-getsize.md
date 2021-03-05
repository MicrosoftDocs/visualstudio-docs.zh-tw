---
description: 取得屬性值的大小（以位元組為單位）。
title: IDebugProperty2：： GetSize |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd6342efd1d9bcb2d2ac063438ee741df3c61325
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166810"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
取得屬性值的大小（以位元組為單位）。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>參數
`pdwSize`\
擴展傳回屬性值的大小（以位元組為單位）。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 `S_GETSIZE_NO_SIZE`如果屬性沒有大小，則會傳回。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
