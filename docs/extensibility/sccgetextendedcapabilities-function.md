---
title: SccGetExtendedCapabilities 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ed27c996a94c4e81a946efbfa2684dc4169005a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720467"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities 函式
此函數會傳回原始檔控制外掛程式所支援的其他功能。

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

[in]原始檔控制外掛程式的內容指標。

 lSccExCaps

[in]旗標，指定用來測試擴充的功能 (請參閱中的擴充功能程式碼表格[功能旗標](../extensibility/capability-flags.md)可能的旗標)。

 pbSupported

[out]會傳回非零 (`TRUE`) 是否支援指定的功能; 否則會傳回零 (`FALSE`)。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|取得功能作業已順利完成。|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|發生未知或未指定的錯誤。|

## <a name="remarks"></a>備註
 視情況下，會呼叫這個方法也就是當一項功能需要進行測試時，呼叫這個方法是以判斷是否支援功能。 指定一次只能有一個旗標。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [錯誤碼](../extensibility/error-codes.md)
- [功能旗標](../extensibility/capability-flags.md)