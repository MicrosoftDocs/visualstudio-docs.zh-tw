---
title: 用戶端區塊攔截函式 |Microsoft Docs
description: 撰寫用戶端區塊攔截函式，以驗證或報告儲存在 _CLIENT_BLOCK 區塊中之資料的內容。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 720087e3c109c6dec4db06d993d0357dc1eddcd4
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729011"
---
# <a name="client-block-hook-functions"></a>用戶端區塊攔截函式
如果您要驗證或報告儲存在 `_CLIENT_BLOCK` 區塊裡的資料內容，您可以撰寫符合這個目的的函式。 您所撰寫的函式，必須與下列在 CRTDBG.H 裡定義的原型類似：

```cpp
void YourClientDump(void *, size_t)
```

 換句話說，攔截函式應該接受配置區塊一開頭的 **void** 指標，以及表示配置大小的 **size_t** 類型值，並且傳回 `void`。 除此之外，其他的內容則由您決定。

 當您使用 [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient) 來安裝攔截函式後，每一次 `_CLIENT_BLOCK` 區塊傾印時都會呼叫它。 然後您可以使用 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) 來取得傾印區塊的類型或子類型資訊。

 您傳入 `_CrtSetDumpClient` 的函式指標是定義在 CRTDBG.H 中的 **_CRT_DUMP_CLIENT** 類型：

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>請參閱

- [調試攔截函式寫入](../debugger/debug-hook-function-writing.md)
- [crt_dbg2 範例](/previous-versions/b31tft51(v=vs.100))
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)