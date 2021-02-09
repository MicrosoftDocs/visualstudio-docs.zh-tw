---
title: 訊息列舉值 |Microsoft Docs
description: 此列舉值的成員會用於 TEXTOUTPROC 函式，此函式是 IDE 在呼叫 SccOpenProject 時所提供的回呼函數。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 00d6b3e27b87e4bac8cee196a60e7fc934f6187d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886739"
---
# <a name="message-enumerator"></a>訊息列舉值
下列旗標用於函式 `TEXTOUTPROC` ，這是 IDE 在呼叫 [SccOpenProject](../extensibility/sccopenproject-function.md) 時所提供的回呼函式 (如需回呼函式) 的詳細資訊，請參閱 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) 。

 如果系統要求您取消程式，它可能會取得其中一個取消訊息。 在此情況下，原始檔控制外掛程式會使用 `SCC_MSG_STARTCANCEL` 來要求 IDE 顯示 [ **取消** ] 按鈕。 在此之後，可能會傳送任何一般訊息集。 如果其中任何一項傳回，則外掛程式會結束作業 `SCC_MSG_RTN_CANCEL` 並傳回。 此外掛程式也會定期輪詢 `SCC_MSG_DOCANCEL` ，以判斷使用者是否已取消作業。 當所有作業完成，或使用者已取消時，即會傳送外掛程式 `SCC_MSG_STOPCANCEL` 。 `SCC_MSG_INFO`、SCC_MSG_WARNING 和 SCC_MSG_ERROR 類型用於顯示在訊息滾動清單中的訊息。 `SCC_MSG_STATUS` 是一種特殊類型，表示文字應顯示在狀態列或暫時顯示區域中。 它不會永久保留在清單中。

## <a name="syntax"></a>語法

```
enum { 
   SCC_MSG_RTN_CANCEL = -1, 
   SCC_MSG_RTN_OK = 0, 
   SCC_MSG_INFO = 1 
   SCC_MSG_WARNING, 
   SCC_MSG_ERROR, 
   SCC_MSG_STATUS, 
   SCC_MSG_DOCANCEL, 
   SCC_MSG_STARTCANCEL, 
   SCC_MSG_STOPCANCEL 
};
```

## <a name="members"></a>成員
 SCC_MSG_RTN_CANCEL 從回呼傳回以表示取消。

 SCC_MSG_RTN_OK 從回呼返回以繼續。

 SCC_MSG_INFO 訊息僅供參考。

 SCC_MSG_WARNING 訊息是警告。

 SCC_MSG_ERROR 訊息是錯誤。

 SCC_MSG_STATUS 訊息適用于狀態列。

 SCC_MSG_DOCANCEL 沒有文字;IDE 會傳回 `SCC_MSG_RTN_OK` 或 `SCC_MSG_RTN_CANCEL` 。

 SCC_MSG_STARTCANCEL 啟動取消迴圈。

 SCC_MSG_STOPCANCEL 停止取消迴圈。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
