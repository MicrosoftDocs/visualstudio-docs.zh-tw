---
title: 概觀 （偵錯介面存取 SDK） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e459d4429d712a9ca4c245d581c6be3578711cd6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855118"
---
# <a name="overview-debug-interface-access-sdk"></a>概觀 (偵錯介面存取 SDK)
使用 DIA SDK，來存取 Microsoft 偵錯資訊。 DIA SDK 提供 COM 為基礎的 API 集，就不需要重寫程式碼，每當 Microsoft 變更偵錯資訊格式。 DIA SDK 也可讓您從一組精選的舊版偵錯資訊，位於所產生的.pdb 和.dbg 檔案讀取[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]5.0 及更新版本的版本。

 DIA SDK 中的每個介面，將不同的 COM 物件，表示除了其中指明。 額外的介面，因此其他物件，建立明確的查詢，透過這類[idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)或是[idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)，而不是藉由呼叫`QueryInterface`現有的介面指標。

## <a name="see-also"></a>另請參閱
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)