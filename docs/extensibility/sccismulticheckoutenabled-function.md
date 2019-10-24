---
title: SccIsMultiCheckoutEnabled 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd8fb5439ac68200ba1a3bbf3af665595528173e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721074"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 函式
此函式會檢查原始檔控制外掛程式是否允許在檔案上多次簽出。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>參數
 pCoNtext

在原始檔控制外掛程式的內容結構。

 pbMultiCheckout

脫銷指定是否啟用此專案的多重簽出（非零表示支援多個簽出）。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|檢查成功。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明確的失敗。|

## <a name="remarks"></a>備註
 IDE 會進行兩項檢查，以判斷是否可以由多個使用者同時簽出檔案。 首先，原始檔控制系統必須支援多個簽出。 原始檔控制外掛程式可以藉由指定 `SCC_CAP_MULTICHECKOUT`，在初始化期間指定這項功能。 之後，在第二次檢查時，IDE 會呼叫這個函式，以判斷目前的專案是否支援多個簽出。 如果選取的專案支援多個簽出，外掛程式會傳回成功的程式碼，並將 `pbMultiCheckout` 設定為非零（`TRUE`）或 `FALSE`。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)