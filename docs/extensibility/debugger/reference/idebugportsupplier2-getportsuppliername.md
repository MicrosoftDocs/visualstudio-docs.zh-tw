---
title: IDebugPort供應商2::獲取港口供應商名稱 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPortSupplierName
helpviewer_keywords:
- IDebugPortSupplier2::GetPortSupplierName
ms.assetid: e4c368ab-640d-4b5b-9f74-810dc9364d8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24eac6d1dee8e76caf70fed9071bd1ae7412fdc6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724587"
---
# <a name="idebugportsupplier2getportsuppliername"></a>IDebugPortSupplier2::GetPortSupplierName
獲取埠供應商名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPortSupplierName( 
   BSTR* pbstrName
);
```

```csharp
int GetPortSupplierName( 
   out string pbstrName
);
```

## <a name="parameters"></a>參數
`pbstrName`\
[出]返回埠供應商的名稱。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
