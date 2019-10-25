---
title: IDiaEnumFrameData::frameByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9889a4f4add318209728bb09ac5c469c1fa836fe
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744655"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
依虛擬位址（VA）傳回框架。

## <a name="syntax"></a>語法

```C++
HRESULT frameByVA( 
   ULONGLONG       virtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>參數
 virtualAddress

在相關框架的 VA。

 框架

脫銷傳回代表包含所提供位址之框架的[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果沒有框架資料符合指定的位址，則會傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)