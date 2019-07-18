---
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01d004491feedff26c350cd7d40c544bc6b6de0f
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "64783743"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
符號設定對應的可執行檔載入位址，此符號存放區中。

## <a name="syntax"></a>語法

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>參數
 `NewVal`

[in]載入的可執行檔的位址。

## <a name="remarks"></a>備註
 符號虛擬位址 (VA) 屬性會使用此方法的值來計算。 除非此屬性將設為非零，才會計算虛擬位址。

> [!NOTE]
> 您必須先呼叫這個方法，當您取得[IDiaSession](../../debugger/debug-interface-access/idiasession.md)物件，並開始使用的物件，如果您需要使用任何虛擬屬性上符號之前。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)