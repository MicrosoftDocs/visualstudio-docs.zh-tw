---
title: Init | Microsoft Docs
description: '使用 VsgDbg 的 Init ( # A1 方法來準備圖形診斷的應用程式內元件，以記錄圖形資訊。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 094f4f3c64570a0af5396e903541c70a919cc0d3
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996184"
---
# <a name="init"></a>Init
準備圖形診斷的應用程式內元件，以主動捕獲圖形資訊並將其記錄到圖形記錄檔。

## <a name="syntax"></a>語法

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>參數
 `vsgLogGetter` 可呼叫的實體（例如函式、函式指標、lambda 或函式物件），其會採用做為參數的緩衝區長度（由組成的緩衝區長度 `wchar_t` 和指向緩衝區的指標），然後傳回 `void` 。 叫用時，可呼叫實體會決定將用來記錄圖形資訊的檔案名，並在傳回之前將它寫入指定的緩衝區。

## <a name="remarks"></a>備註
 `Init`當建立類別的實例時，會自動呼叫 `VsgDbg` 函式 `bDefaultInit` `true` ，否則， `Init` 必須先明確呼叫函式，才能主動捕捉和記錄圖形資訊。

 您可以藉由呼叫來完成並關閉使用中的圖形記錄檔 `UnInit` ，然後再次呼叫，以將更多的圖形資訊提供給新的圖形記錄檔 `Init` 。 您可以重複這個動作，因為您想要使用相同的實例來建立數個獨立的圖形記錄檔 `VsgDbg` 。

## <a name="see-also"></a>另請參閱
- [UnInit](init.md)