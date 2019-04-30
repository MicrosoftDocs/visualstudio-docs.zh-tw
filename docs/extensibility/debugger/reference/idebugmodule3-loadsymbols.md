---
title: IDebugModule3::LoadSymbols |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9068eed8881124e75f06f4b97d3430ff3ef80e8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918676"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
載入目前模組的符號。

## <a name="syntax"></a>語法

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>傳回值
 如果方法成功，它會傳回`S_OK`。 如果失敗，它會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會從目前的搜尋路徑載入符號 (這可以藉由呼叫改變[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)方法)。

 這個方法是透過[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)