---
title: IDiaEnumFrameData::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8d083cea518032c121a5cb9e9213abbbd7eaaf8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640151"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
透過索引中擷取的畫面格的資料元素。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>參數
 索引

[in]索引[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)要擷取的物件。 索引是在範圍介於 0 到`count`-1，其中`count`會傳回[idiaenumframedata:: Get_count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)方法。

 section

[out]傳回[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件，表示所需的畫面格的資料元素。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)