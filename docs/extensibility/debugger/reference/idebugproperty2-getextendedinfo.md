---
description: 取得屬性的延伸資訊。
title: IDebugProperty2：： GetExtendedInfo |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 004c7d545dbaaa20016fd94febe999420305fc7a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171495"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
取得屬性的延伸資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetExtendedInfo ( 
   REFGUID* guidExtendedInfo,
   VARIANT* pExtendedInfo
);
```

```csharp
int GetExtendedInfo ( 
   ref Guid guidExtendedInfo,
   out object pExtendedInfo
);
```

## <a name="parameters"></a>參數
`guidExtendedInfo`\
在判斷要抓取的擴充資訊類型的 GUID。 如需詳細資訊，請參閱備註。

`pExtendedInfo`\
擴展傳回 `VARIANT` (c + +) 或物件 (c # ) ，可用來取得擴充屬性資訊。 例如，這個參數可能會傳回 `IUnknown` 可針對 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) 介面進行查詢的介面。 如需詳細資訊，請參閱備註。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 `S_GETEXTENDEDINFO_NO_EXTENDEDINFO`如果沒有要取出的擴充資訊，則傳回。

## <a name="remarks"></a>備註
 這個方法的目的是為了抓取無法藉由呼叫 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 方法來取得本身的資訊。

 此方法通常會辨識下列 Guid (GUID 值是針對 c # 指定的，因為名稱無法在任何元件) 中使用。 您可以建立其他 Guid 以供內部使用。

|名稱|GUID|描述|
|----------|----------|-----------------|
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|傳回 `IUnknown` 檔的介面。 一般而言， [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) 介面可從這個 `IUnknown` 介面取得。|
|guidCodeCoNtext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|傳回 `IUnknown` 檔內容的介面。 一般而言， [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 介面可從這個 `IUnknown` 介面取得。|
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|傳回字串，其中包含自訂檢視器的 CLSID，通常是由運算式評估工具所執行。|
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|如果這個屬性代表 managed 程式碼本機位址，則傳回代表所需插槽號碼的32位數位。|
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|傳回字串，其中包含與屬性物件相關聯的變數簽章。|

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
