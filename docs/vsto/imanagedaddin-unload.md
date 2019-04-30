---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 296502aa461688c34152d86ee21aab5f2c83ecb4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956740"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  卸載 Managed VSTO 增益集之前呼叫。

## <a name="syntax"></a>語法

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>傳回值
 HRESULT 值，表示此方法是否已順利完成。

## <a name="remarks"></a>備註
 Microsoft Office 的目前版本不會呼叫這個方法。 這個方法是保留供日後使用。

## <a name="see-also"></a>另請參閱
- [IManagedAddin 介面](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
