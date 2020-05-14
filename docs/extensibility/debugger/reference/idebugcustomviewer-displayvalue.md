---
title: IDebugCustom查看器::D播放價值 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732448"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
呼叫此方法以顯示指定的值。

## <a name="syntax"></a>語法

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>參數
`hwnd`\
[在]父視窗

`dwID`\
[在]支援多種類型的自定義檢視器的 ID。

`pHostServices`\
[in] 保留。 始終設定為 null。

`pDebugProperty`\
[在]可用於檢索要顯示的值的介面。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則返回錯誤代碼。

## <a name="remarks"></a>備註
 顯示是"模態的",因為此方法將創建必要的視窗、顯示值、等待輸入並關閉視窗,所有這些都在返回到調用方之前。 這意味著該方法必須處理顯示屬性值的所有方面,從為輸出創建視窗,到等待使用者輸入,到銷毀視窗。

 要支援更改給定[IDebug Property3](../../../extensibility/debugger/reference/idebugproperty3.md)物件上的值,可以使用[SetValueAsString WithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)方法 —如果該值可以表示為字串串。 否則,有必要在實現`DisplayValue``IDebugProperty3`介面的同一對象上創建自定義介面(獨佔表達式賦值器實現此方法)。 此自定義介面將提供用於更改任意大小或複雜性的數據的方法。

## <a name="see-also"></a>另請參閱
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
