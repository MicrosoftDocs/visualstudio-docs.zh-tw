---
title: IEnumCodepath2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89c8cac9a7c2baa020002fe852330639d7081982
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717712"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
此介面表示代碼路徑的清單。

## <a name="syntax"></a>語法

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示代碼路徑的清單。

## <a name="notes-for-callers"></a>通話備註
 調用[EnumCodePath](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumCodePaths2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|檢索枚舉序列中指定數量的代碼路徑。|
|[跳](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|在枚舉序列中跳過指定數量的代碼路徑。|
|[重設](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|獲取枚舉器中的代碼路徑數。|

## <a name="remarks"></a>備註
 代碼路徑表示程式中的分支點或函數調用。 代碼路徑清單表示代碼執行所通過的路徑。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
