---
title: IPropertyProxyEEside:獲取託管檢視器建立資料 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e72922b348c8744f10037e199e93f735ff4be8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714956"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
檢索有關此屬性類型的查看器的資訊,以便實例化該查看器。

## <a name="syntax"></a>語法

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>參數
`assemName`\
[出]返回保存此物件的程式集的名稱。

`assemBytes`\
[出]返回包含此物件的程式集位元組的[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件(如果沒有可用的位元組,則為空值)。

`assemPdb`\
[出]返回包含`IEEDataStorage`此物件符號存儲資訊的物件(如果沒有可用的符號存儲,則為空值)。

`className`\
[出]返回包含此物件的類名稱。

`alr`\
[出]從[「裝配」](../../../extensibility/debugger/reference/assemblylocresolution.md)枚舉中返回一個值,指示程式集的位置。

`replacementOk`\
[出]如果可以更改此`TRUE`物件的值,則傳回非零 ( ), 如果可以更改此物件的值。如果對`FALSE`像是唯讀的,則為零 ( )。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法由類型可視化器用於實例化託管檢視器。

## <a name="see-also"></a>另請參閱
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
