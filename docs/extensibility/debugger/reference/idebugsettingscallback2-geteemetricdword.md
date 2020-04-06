---
title: IDebugsettings 回調2::獲取EEMetricDword |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricDword
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce326c63f97dfafd06e3e2b3e760b1c06e60d442
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720062"
---
# <a name="idebugsettingscallback2geteemetricdword"></a>IDebugSettingsCallback2::GetEEMetricDword
檢索對應於表達式賦值器的指定指標的值。

## <a name="syntax"></a>語法

```cpp
HRESULT GetEEMetricDword(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   DWORD*  pdwValue
);
```

```csharp
private int GetEEMetricDword(
   ref Guid guidLang,
   ref Guid guidVendor,
   string   pszMetric,
   out uint pdwValue
);
```

## <a name="parameters"></a>參數
`guidLang`\
[在]程式設計語言的唯一標識符。

`guidVendor`\
[在]供應商的唯一標識碼。

`pszMetric`\
[在]指標的名稱。

`pdwValue`\
[出]返回對應於指標字串的值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
