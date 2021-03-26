---
description: 設定服務提供者。
title: IDebugPortPicker：： SetSite |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a442c438f233187265c90e724f57e8681b95556
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072255"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
設定服務提供者。

## <a name="syntax"></a>語法

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

## <a name="parameters"></a>參數
`pSP`\
在服務提供者介面的參考。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫任何其他方法之前，將會呼叫這個方法。

## <a name="see-also"></a>另請參閱
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
