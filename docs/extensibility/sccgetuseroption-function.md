---
title: SccGetUserOption 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b237ded8ac0d22500986a9d390834147f24a2c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433184"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption 函式
此函式會擷取各種不同的使用者特定的選項。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>參數
 pContext

[in]原始檔控制外掛程式的內容指標。

 nOption

[in]若要擷取 （如需可能的選項，請參閱 < 備註 >） 的選項。

 lpVal

[out]與選項相關聯的值。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功擷取選項。|
|SCC_E_OPNOTSUPPORTED|不支援選項。|
|SCC_E_NONSPECIFICERROR|發生未指定的錯誤。|

## <a name="remarks"></a>備註
 此命令支援下列選項：

|使用者選項|描述|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|判斷使用者是否想要簽出檔案的本機版本。 `lpVal` 指派`SCC_USEROPT_COLV_YES`（使用者想要簽出本機檔案） 或`SCC_USEROPT_COLV_NO`。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [錯誤碼](../extensibility/error-codes.md)