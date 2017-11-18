---
title: "概觀 （偵錯介面存取 SDK） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4cd0206e402600cbe9002c931adb7ff6a2cc680
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="overview-debug-interface-access-sdk"></a>概觀 (偵錯介面存取 SDK)
使用 DIA SDK，來存取 Microsoft 偵錯資訊。 DIA SDK 提供 COM 為基礎的 API 集，就不需要重寫程式碼，每當 Microsoft 變更偵錯資訊格式。 DIA SDK 也可讓您從特定的舊版偵錯資訊，所產生的.pdb 和.dbg 檔案中的一組讀取[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]5.0 及更新版本。  
  
 DIA SDK 中的每個介面除了代表不同的 COM 物件，其中指明。 其他介面，因此其他物件，會建立和透過明確的查詢，例如[idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)或[idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)，而不是藉由呼叫`QueryInterface`上現有的介面指標。  
  
## <a name="see-also"></a>另請參閱  
 [Idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)