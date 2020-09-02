---
title: ToggleHUD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb05bb6a424b5639e0ee98e96c80315c51081ace
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62848470"
---
# <a name="togglehud"></a>ToggleHUD
切換 [圖形診斷] *抬頭顯示器* (上層顯示) 重迭顯示或關閉。

## <a name="syntax"></a>語法

```C++
void ToggleHUD();
```

## <a name="remarks"></a>備註
 [圖形診斷] 抬頭顯示器會顯示在 [圖形診斷] 下執行之應用程式的左上角。 它會顯示應用程式的執行時間資訊，以及有關圖形資訊捕捉的執行時間資訊，以及藉由呼叫 [AddMessage](addmessage.md) 成員函式而加入的訊息。

 若要切換抬頭顯示器，您不需要主動捕捉圖形資訊，也就是可以透過類別的實例來切換 `VsgDbg` ，但不需要先呼叫 [Init](init.md) 成員函式。