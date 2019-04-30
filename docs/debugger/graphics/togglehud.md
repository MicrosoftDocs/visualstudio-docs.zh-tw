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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848470"
---
# <a name="togglehud"></a>ToggleHUD
切換 圖形診斷*抬頭顯示器*（抬頭顯示器） 重疊或關閉。

## <a name="syntax"></a>語法

```C++
void ToggleHUD();
```

## <a name="remarks"></a>備註
 圖形診斷抬頭顯示器會顯示在圖形診斷下執行的應用程式的左上角。 它會顯示有關應用程式以及圖形資訊擷取，並由呼叫所加入的訊息，會產生執行階段資訊。 [AddMessage](addmessage.md)成員函式。

 若要切換抬頭顯示器，您不需要主動擷取圖形資訊 — 也就是透過執行個體的切換`VsgDbg`類別，但[Init](init.md)成員函式不需要先呼叫。