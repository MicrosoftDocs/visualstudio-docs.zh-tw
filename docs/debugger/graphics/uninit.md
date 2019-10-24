---
title: UnInit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef809b646a0af58e46b8c68dc5a8cf7633692bcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734824"
---
# <a name="uninit"></a>UnInit
完成圖形記錄檔，將其關閉，並釋放應用程式主動記錄圖形資訊時所使用的資源。

## <a name="syntax"></a>語法

```C++
void UnInit();
```

## <a name="remarks"></a>備註
 當終結 `VsgDbg` 類別的實例時，會自動呼叫 `UnInit`。 如果 `VsgDbg` 實例並未主動記錄圖形資訊，就不會有任何作用。

 在 `VsgDbg` 類別的實例上呼叫 `UnInit` 之後，可以藉由呼叫 `Init` 來建立新的圖形記錄檔，並藉由呼叫 `UnInit` 來完成。 您可以多次重複此動作，因為您想要使用相同的 `VsgDbg` 實例來建立數個獨立的圖形記錄檔。

## <a name="see-also"></a>請參閱
- [Init](init.md)