---
title: SccGetUserOption 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc7b68df3331c1240ad833048940e656da034ccf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700692"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption 函式
此功能檢索各種特定於用戶的選項。

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

[在]源代碼管理外掛程式上下文指標。

 nOption

[在]要檢索的選項(有關可能的選項,請參閱備註)。

 lpVal

[出]與選項關聯的值。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功檢索選項。|
|SCC_E_OPNOTSUPPORTED|不支援選項。|
|SCC_E_NONSPECIFICERROR|發生未指定的錯誤。|

## <a name="remarks"></a>備註
 此指令支援以下選項:

|使用者選項|描述|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|確定使用者是否要簽出檔的本地版本。 `lpVal`已配置`SCC_USEROPT_COLV_YES`(使用者希望簽出本地端檔案`SCC_USEROPT_COLV_NO`)或 。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [錯誤代碼](../extensibility/error-codes.md)
