---
title: SccIs 多檢出功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700588"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 函式
此函數檢查原始程式碼管理外掛程式是否允許在檔上進行多次簽出。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>參數
 pContext

[在]原始程式碼管理外掛程式上下文結構。

 pb 多簽出

[出]指定是否為此項目啟用了多個簽出(非零表示支援多個簽出)。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|檢查成功。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|非特異性故障。|

## <a name="remarks"></a>備註
 IDE 進行兩次檢查,以確定是否可以由多個用戶同時簽出檔。 首先,原始程式碼管理系統必須支援多個簽出。 原始程式碼管理外掛程式可以`SCC_CAP_MULTICHECKOUT`透過指定 在初始化期間指定此功能。 此後,作為第二次檢查,IDE 調用此函數以確定當前專案是否支援多個簽出。 如果選取的項目支援多個簽出,外掛程式將傳回一個成功代碼,並將`pbMultiCheckout`其設定為非零`TRUE``FALSE`() 或 。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
