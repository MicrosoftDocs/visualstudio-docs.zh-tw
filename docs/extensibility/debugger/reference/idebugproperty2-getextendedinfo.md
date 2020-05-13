---
title: IDebug屬性2::獲取擴展資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34d6cd880ccae520bf000ad01b52223857f4f10f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721482"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
獲取屬性的擴展資訊。

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
[在]確定要檢索的擴展資訊的類型的 GUID。 有關詳細資訊,請參閱備註。

`pExtendedInfo`\
[出]返回可用於`VARIANT`檢索擴展屬性資訊的 (C++) 或物件 (C#)。 例如,此參數可能會返回一個`IUnknown`介面,該介面可以查詢[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)介面。 有關詳細資訊,請參閱備註。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則返回錯誤代碼。 如果沒有`S_GETEXTENDEDINFO_NO_EXTENDEDINFO`要檢索的擴展資訊,則返回。

## <a name="remarks"></a>備註
 此方法的存在是為了檢索無法通過調用[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法檢索的資訊。

 此方法通常可識別以下 GUID(GUID 值指定為 C#,因為名稱在任何程式集中不可用)。 可以創建其他 GUID 供內部使用。

|名稱|GUID|描述|
|----------|----------|-----------------|
|吉德檔案|[3f98de84-fee9-11d0-b47f-00a0244a1d2]|返回文`IUnknown`檔的介面。 通常,可以從此`IUnknown`介面獲取[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)介面。|
|吉德代碼內容|[e2fc65e-56ce-11d1-b528-00ax004a8797]|返回文`IUnknown`檔 上下文的介面。 通常,可以從此`IUnknown`介面獲取[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面。|
|吉德自訂檢視器支援|[d9c9da31-ffbe-4eeb-9186-23121e3c088c]|返回包含自定義檢視器的 CLSID 的字串,通常由表達式賦值器實現。|
|吉德擴充資訊槽|[6df235ad-82c6-4292-9c97-7389770bc42f]|如果此屬性表示託管代碼本地位址,則返回表示所需插槽號的 32 位數位。|
|吉德延伸資訊簽名|[b5fb6d46-f805-417f-96a3-8ba737073ffd]|返回一個字串,其中包含與屬性對象關聯的變數的簽名。|

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
