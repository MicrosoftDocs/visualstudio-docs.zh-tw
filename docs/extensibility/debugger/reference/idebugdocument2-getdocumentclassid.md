---
title: IDebugDocument2::獲取文檔類 ID |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71683c91082f477da530ec1be1fdc7627d6a7635
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732036"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
獲取文檔的類標識碼。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDocumentClassID( 
   CLSID* pclsid
);
```

```csharp
int GetDocumentClassID( 
   out Guid pclsid
);
```

## <a name="parameters"></a>參數
`pclsid`[出]返回作為文件的類 ID 的 GUID。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 類GUID可用於實例化每個類,每個類都表示文檔。

## <a name="see-also"></a>另請參閱
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
