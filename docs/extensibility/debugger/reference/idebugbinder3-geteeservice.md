---
description: 這個方法會傳回要求的服務。
title: IDebugBinder3：： GetEEService |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ecd439ba1af40a54512c3ef15efb4728c8c54a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167668"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
這個方法會傳回要求的服務。

## <a name="syntax"></a>語法

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>參數
`vendor`\
[in] `GUID` 在廠商 (null 值是可接受的) 。

`language`\
[in] `GUID` 在語言 (null 值是可接受的) 。

`iid`\
[in] `IID` 取得的服務。

`ppService`\
擴展要求之服務的介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 傳遞 `IID` [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) 介面 (`IID_IEEVisualizerServiceProvider`) ，以查看是否有可用的型別視覺化程式服務。 如果是的話，運算式評估工具可以取得 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 介面，以支援型別視覺化檢視。 如需詳細資料，請參閱 [視覺化和查看資料](../../../extensibility/debugger/visualizing-and-viewing-data.md) 。

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)
