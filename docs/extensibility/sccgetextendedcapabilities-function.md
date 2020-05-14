---
title: SccGet 擴充功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5247f2de7ffc63db7235f915c72b3274b8fee5f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700728"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGet 擴充功能功能
此功能返回原始程式碼管理外掛程式支援的其他功能。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>參數
 pContext

[在]源代碼管理外掛程式上下文指標。

 lSccExCaps

[在]指定要測試的擴展功能的標誌(請參閱["功能"標誌](../extensibility/capability-flags.md)中的擴展功能代碼表,瞭解可能的標誌)。

 pb 支援

[出]如果支援指定的功能,`TRUE`則傳回非零 ( ),否則,返回零`FALSE`()。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|獲取功能操作已成功完成。|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|發生未知或未指定的錯誤。|

## <a name="remarks"></a>備註
 此方法是按需調用的;也就是說,當需要測試功能時,將調用此方法以確定該功能是否受支援。 一次只指定一個標誌。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [錯誤碼](../extensibility/error-codes.md)
- [功能旗標](../extensibility/capability-flags.md)
