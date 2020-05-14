---
title: IDebug屬性2::獲取大小 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f57a742bae0217493d8869b257e4a17839e4e14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721333"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
獲取屬性值的大小(以位元組為單位)。

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
[出]返回屬性值的大小(以位元組為單位)。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則返回錯誤代碼。 如果`S_GETSIZE_NO_SIZE`屬性沒有大小,則返回。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
