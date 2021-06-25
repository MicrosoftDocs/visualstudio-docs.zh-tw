---
description: 此函式會檢查原始檔控制外掛程式是否允許在檔案上進行多次簽出。
title: SccIsMultiCheckoutEnabled 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b9fc81a20e3a8078a2d4cebbc6a8db10c2e2e49
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902510"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 函式
此函式會檢查原始檔控制外掛程式是否允許在檔案上進行多次簽出。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>參數
 pContext

在原始檔控制外掛程式內容結構。

 pbMultiCheckout

擴展指定是否啟用此專案的多個簽出 (非零表示) 支援多重簽出。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|檢查成功。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|模糊失敗。|

## <a name="remarks"></a>備註
 IDE 會進行兩項檢查，以判斷是否可由一個以上的使用者同時簽出檔案。 首先，原始檔控制系統必須支援多次簽出。 原始檔控制外掛程式可以藉由指定，在初始化期間指定這項功能 `SCC_CAP_MULTICHECKOUT` 。 之後，在第二次檢查時，IDE 會呼叫這個函式來判斷目前的專案是否支援多重簽出。 如果選取的專案支援多個簽出，則外掛程式會傳回成功的程式碼，並將設定 `pbMultiCheckout` 為非零 (`TRUE`) 或 `FALSE` 。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
