---
title: SccGetExtendedCapabilities 函式 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700728"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities 函式
此函式會傳回原始檔控制外掛程式所支援的其他功能。

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

在原始檔控制外掛程式內容指標。

 lSccExCaps

在旗標，指定要測試的擴充功能， (查看可能旗標的 [功能旗標](../extensibility/capability-flags.md) 中的擴充功能程式碼表) 。

 pbSupported

擴展如果支援指定的功能，則會傳回非零的 (`TRUE`) ; 否則會傳回零 (`FALSE`) 。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|取得功能作業已順利完成。|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|發生未知或未指定的錯誤。|

## <a name="remarks"></a>備註
 視需要呼叫此方法;也就是說，當需要測試功能時，會呼叫這個方法來判斷是否支援該功能。 一次只能指定一個旗標。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [錯誤碼](../extensibility/error-codes.md)
- [功能旗標](../extensibility/capability-flags.md)
