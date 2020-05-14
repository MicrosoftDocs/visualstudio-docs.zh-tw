---
title: IEE視覺化服務::獲取自訂檢視器清單 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f3808ad6fb511270ee3825601c476f10a8b77124
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718012"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
此方法返回此服務知道的類型可視化器的清單。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>參數
`celtSkip`\
[在]要跳過的視覺化工具數。

`celRequested`\
[在]要檢索的可視化工具數(也指定`rgViewers`數位列的大小)。

`rgViewers`\
[進出]要填充[DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)結構的陣列。

`pceltFetched`\
[出]實際檢索的可視化工具數。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)將請求傳遞給此方法,作為其對類型可視化工具的支援的一部分。 如果表示式評估器還提供相同類型的自訂檢視器,則可以將這些自定義檢視器的[DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)結構追加到清單中。 確保[GetCustomViewerCount 反映](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)這些額外的查看器。

 有關可視化工具和查看器之間的差異的詳細資訊,請參閱["類型可視化器"和"自定義檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)"。

## <a name="see-also"></a>另請參閱
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
