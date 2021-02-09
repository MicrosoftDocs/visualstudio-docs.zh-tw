---
title: 總覽 (Debug 介面存取 SDK) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a3fb8d56ca4df9912862346e5b096b2bb5414881
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862315"
---
# <a name="overview-debug-interface-access-sdk"></a>概觀 (偵錯介面存取 SDK)
使用 DIA SDK 來存取 Microsoft debug 資訊。 DIA SDK 提供以 COM 為基礎的 API 集，可讓您在 Microsoft 變更偵錯工具的格式時，不必重寫程式碼。 DIA SDK 也可讓您從一組選取的舊版偵錯工具資訊（位於 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 版本5.0 和更新版本中所產生的 .pdb 和 dbg 檔案）讀取。

 DIA SDK 中的每個介面都代表不同的 COM 物件，除非另有指定。 其他介面（以及其他的物件）則是透過明確的查詢（例如 [IDiaDataSource：： openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) 或 [IDiaSession：： findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)）來建立，而不是 `QueryInterface` 在現有的介面指標上呼叫。

## <a name="see-also"></a>另請參閱
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)