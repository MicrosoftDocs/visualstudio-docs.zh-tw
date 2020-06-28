---
title: IDiaSectionContrib::get_uninitializedData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_uninitializedData method
ms.assetid: 39736f35-6c73-4f54-a092-517192e417ff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 934d2295d97d89b58704ada2eba58f0e2ec9aea1
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466088"
---
# <a name="idiasectioncontribget_uninitializeddata"></a>IDiaSectionContrib::get_uninitializedData
抓取表示區段是否包含未初始化資料的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_uninitializedData ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷`TRUE`如果區段包含未初始化的資料，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)