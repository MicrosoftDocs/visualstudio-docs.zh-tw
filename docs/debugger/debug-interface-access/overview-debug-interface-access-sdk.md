---
title: 總覽（Debug Interface Access SDK） |Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a403a8d3ddec82ce7e051e545687511c2421fa9
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461165"
---
# <a name="overview-debug-interface-access-sdk"></a>概觀 (偵錯介面存取 SDK)
使用 DIA SDK 來存取 Microsoft debug 資訊。 DIA SDK 提供以 COM 為基礎的 API 集，只要 Microsoft 變更了修訂資訊的格式，就不需要重寫程式碼。 DIA SDK 也可讓您從一組選取的舊版偵錯工具（位於 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 版本5.0 和更新版本所產生的 .pdb 和 dbg 檔案）中進行讀取。

 除非另有指示，否則 DIA SDK 中的每個介面都代表不同的 COM 物件。 其他介面（也就是其他物件）則是透過明確查詢來建立，例如[IDiaDataSource：： openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)或[IDiaSession：： findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)，而不是 `QueryInterface` 在現有介面指標上呼叫。

## <a name="see-also"></a>另請參閱
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)