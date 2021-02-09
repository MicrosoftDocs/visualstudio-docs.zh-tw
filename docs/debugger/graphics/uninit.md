---
title: UnInit | Microsoft Docs
description: '使用 VsgDbg 的 UnInit ( # A1 方法來完成和關閉圖形記錄檔，並釋放記錄資源。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cead2d7c1c98e4f481e6057c9ab79c8dc908683
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905008"
---
# <a name="uninit"></a>UnInit
完成圖形記錄檔、將其關閉，並釋放應用程式主動記錄圖形資訊時所使用的資源。

## <a name="syntax"></a>語法

```C++
void UnInit();
```

## <a name="remarks"></a>備註
 `UnInit` 當終結類別的實例時，會自動呼叫 `VsgDbg` 。 如果 `VsgDbg` 實例未主動記錄圖形資訊，則不會有任何作用。

 在 `UnInit` 類別的實例上呼叫之後，您 `VsgDbg` 可以藉由呼叫來建立新的圖形記錄檔， `Init` 並藉由呼叫來完成 `UnInit` 。 您可以重複這個動作，因為您想要使用相同的 `VsgDbg` 實例來建立數個獨立的圖形記錄檔。

## <a name="see-also"></a>另請參閱
- [Init](init.md)