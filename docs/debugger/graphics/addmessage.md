---
title: AddMessage | Microsoft Docs
description: 使用 VsgDbg 類別的 AddMessage 方法，將自訂訊息新增至圖形診斷 Head-Up 顯示 (抬頭顯示器) 。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9d51e4415d9707b2df4bb0912290d4f5aa7825f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874635"
---
# <a name="addmessage"></a>AddMessage
將自訂訊息新增至 [圖形診斷] *抬頭顯示器* (上層顯示) 。

## <a name="syntax"></a>語法

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>參數
 `szMessage` 要加入至抬頭顯示器的訊息。

## <a name="remarks"></a>備註
 [圖形診斷] 抬頭顯示器會顯示在 [圖形診斷] 下執行之應用程式的左上角。 它會顯示應用程式的執行時間資訊，以及有關圖形資訊捕捉的執行時間資訊，以及藉由呼叫這個函式所加入的訊息。

 若要將訊息新增至抬頭顯示器，您不需要主動捕捉圖形資訊，也就是可以透過類別的實例加入訊息 `VsgDbg` ，但不會先呼叫 [Init](init.md) 成員函式。 訊息只會顯示在抬頭顯示器中，而不會記錄在圖形記錄檔中。