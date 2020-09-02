---
title: SccGetUserOption 函式 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700692"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption 函式
此函式會抓取各種使用者專屬的選項。

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

在原始檔控制外掛程式內容指標。

 nOption

在取得 (的選項請參閱備註，以取得可能的選項) 。

 lpVal

擴展與選項相關聯的值。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功抓取選項。|
|SCC_E_OPNOTSUPPORTED|選項不受支援。|
|SCC_E_NONSPECIFICERROR|發生未指定的錯誤。|

## <a name="remarks"></a>備註
 此命令支援下列選項：

|使用者選項|描述|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|判斷使用者是否想要簽出本機版本的檔案。 `lpVal` 指派 `SCC_USEROPT_COLV_YES` (使用者想要簽出本機檔案) 或 `SCC_USEROPT_COLV_NO` 。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [錯誤碼](../extensibility/error-codes.md)
