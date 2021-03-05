---
description: 根據指定的權杖來抓取類型。
title: IDebugDynamicFieldCOMPlus：： GetTypeFromTypeDef |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypeFromTypeDef
- IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68f0747c61f1e2c19ea1abde309f8fab437ecc84
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154102"
---
# <a name="idebugdynamicfieldcomplusgettypefromtypedef"></a>IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
根據指定的權杖來抓取類型。

## <a name="syntax"></a>語法

```cpp
HRESULT GetTypeFromTypeDef(
   ULONG32       ulAppDomainID,
   GUID          guidModule,
   _mdToken      tokClass,
   IDebugField** ppType
);
```

```csharp
int GetTypeFromTypeDef(
   uint            ulAppDomainID,
   Guid            guidModule,
   int             tokClass,
   out IDebugField ppType
);
```

## <a name="parameters"></a>參數
`ulAppDomainID`\
在應用程式域的識別碼。

`guidModule`\
在模組的唯一識別碼。

`tokClass`\
在表示類型的標記。

`ppType`\
擴展傳回包含類型的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
