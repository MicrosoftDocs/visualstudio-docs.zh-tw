---
title: Init | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b2ed132e072d9ca8a0b9c98bfc5be6e25931805
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734997"
---
# <a name="init"></a>Init
準備圖形診斷的應用程式內元件，以主動捕捉圖形資訊並將其記錄到圖形記錄檔。

## <a name="syntax"></a>語法

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>參數
 `vsgLogGetter` 可呼叫的實體（例如函式、函式指標、lambda 或函式物件），其會以 `wchar_t` 所組成的緩衝區長度和該緩衝區的指標做為參數，並傳回 `void`。 當叫用時，可呼叫實體會決定要用來記錄圖形資訊的檔案名，並將其寫入至指定的緩衝區，然後再傳回。

## <a name="remarks"></a>備註
 建立 `VsgDbg` 類別的實例時，會自動呼叫 `Init` 函式，方法是指定其參數化的 `bDefaultInit` 參數做為 `true`;否則，必須先明確呼叫 `Init`，才能主動捕捉和記錄圖形資訊。

 您可以藉由呼叫 `UnInit` 來完成和關閉現用圖形記錄檔，然後再次呼叫 `Init`，以將更多圖形資訊捕捉並記錄到新的圖形記錄檔。 您可以使用相同的 `VsgDbg` 實例，多次重複此動作，以建立數個獨立的圖形記錄檔。

## <a name="see-also"></a>請參閱
- [UnInit](init.md)