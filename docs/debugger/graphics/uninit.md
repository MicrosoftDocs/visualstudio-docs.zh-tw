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
ms.openlocfilehash: 8165b2e1993a6ea52127536a058f662e1a3d92cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848728"
---
# <a name="uninit"></a>UnInit
完成的圖形記錄檔、 關閉，並釋出應用程式的作用中記錄的圖形資訊時所使用的資源。

## <a name="syntax"></a>語法

```C++
void UnInit();
```

## <a name="remarks"></a>備註
 `UnInit` 執行個體時自動呼叫`VsgDbg`終結類別之前。 如果`VsgDbg`執行個體所未主動記錄圖形資訊，這沒有任何作用。

 之後`UnInit`的執行個體上呼叫`VsgDbg`類別，新的圖形記錄檔可由呼叫`Init`並完成藉由呼叫`UnInit`。 您可以重複此步驟為您想要使用相同的多次`VsgDbg`來建立數個獨立的圖形記錄檔的執行個體。

## <a name="see-also"></a>另請參閱
- [Init](init.md)