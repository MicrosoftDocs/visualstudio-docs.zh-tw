---
title: IDebugSettingsCallback2：： GetEEMetricString |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricString
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 710b4e7623450cbba04e449cbd732486f00932d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963636"
---
# <a name="idebugsettingscallback2geteemetricstring"></a>IDebugSettingsCallback2::GetEEMetricString
抓取運算式評估工具度量的值字串（指定其名稱）。

## <a name="syntax"></a>語法

```cpp
HRESULT GetEEMetricString(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricString(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

## <a name="parameters"></a>參數
`guidLang`\
在程式設計語言的唯一識別碼。

`guidVendor`\
在廠商的唯一識別碼。

`pszMetric`\
在度量的名稱。

`pbstrValue`\
擴展傳回度量值字串。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
