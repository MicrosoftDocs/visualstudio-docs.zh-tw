---
title: IDebugBinder3::獲取服務 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c08d7df4a6b05be489f6b9ab06569c085f3b1f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735821"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
此方法返回請求的服務。

## <a name="syntax"></a>語法

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>參數
`vendor`\
[在]`GUID`供應商的 null 值是可以接受的)。

`language`\
[在]`GUID`語言(空值是可以接受的)。

`iid`\
[在]`IID`獲得的服務。

`ppService`\
[出]與請求的服務的介面。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 傳遞[IEE 視覺化服務提供者](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)介面`IID_IEEVisualizerServiceProvider`(), 以檢視類型可視化工具服務`IID`是否可用。 如果是這樣,表達式賦值器可以獲取[IEE 可視化器服務](../../../extensibility/debugger/reference/ieevisualizerservice.md)介面以支援類型可視化器。 關於詳細資訊[,請參閱可視化和檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)。

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)
