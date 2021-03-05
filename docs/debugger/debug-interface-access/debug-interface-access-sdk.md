---
description: Microsoft Debug Interface Access Software 開發工具組 (DIA SDK) 可讓您存取由 Microsoft postcompiler tools 產生的程式資料庫 ( .pdb) 檔案中所儲存的偵錯工具資訊。
title: Debug Interface Access SDK |Microsoft 檔
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbb7c9025094249715f1d69a8d58d8725d294107
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149300"
---
# <a name="debug-interface-access-sdk"></a>偵錯 (偵錯介面存取 SDK)

Microsoft Debug Interface Access Software 開發工具組 (DIA SDK) 可讓您存取由 Microsoft postcompiler tools 產生的程式資料庫 ( .pdb) 檔案中所儲存的偵錯工具資訊。 由於 postcompiler 工具所產生的 .pdb 檔案格式會進行不斷的修訂，所以公開格式並不實用。 您可以使用 DIA API 來開發應用程式，以搜尋和流覽儲存在 .pdb 檔案中的 debug 資訊。 例如，這類應用程式可以報告堆疊追蹤資訊，以及分析效能資料。

## <a name="in-this-section"></a>本節內容

[快速入門](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)

概述 DIA SDK 功能，並指定安裝 DIA SDK 的位置，以及所需的標頭檔和程式庫檔案。

[查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

提供有關如何使用 DIA API 來查詢 .pdb 檔案的指示。

[符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)

討論如何在 DIA API 中使用符號和符號標記。

[參考](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)

包含 DIA API 的介面、方法、列舉和結構。

[Dia2dump 範例](../../debugger/debug-interface-access/dia2dump-sample.md)

說明如何使用 DIA API 來搜尋和流覽 debug 資訊。
