---
title: 訊息列舉值 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a702e7eae6bc6bcdace62d61f27f78c23aeaa95f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349018"
---
# <a name="message-enumerator"></a>訊息的列舉值
下列旗標會用於`TEXTOUTPROC`函式，也就是 IDE 提供呼叫時的回呼函式[SccOpenProject](../extensibility/sccopenproject-function.md) (請參閱[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)如回呼的詳細資訊函式）。

 如果 IDE 會要求取消程序，它可能會取消訊息。 在此情況下，原始檔控制外掛程式會使用`SCC_MSG_STARTCANCEL`詢問顯示 IDE**取消** 按鈕。 在此之後，可能會傳送任何一組一般訊息。 如果任何這些傳回`SCC_MSG_RTN_CANCEL`，則外掛程式，則會結束作業，並傳回。 外掛程式也會輪詢`SCC_MSG_DOCANCEL`定期來判斷是否使用者已取消作業。 當所有作業完成都之後，或如果使用者已取消，外掛程式會傳送`SCC_MSG_STOPCANCEL`。 `SCC_MSG_INFO`，SCC_MSG_WARNING，並且 SCC_MSG_ERROR 類型用於捲動訊息清單中顯示的訊息。 `SCC_MSG_STATUS` 是一種特殊類型，指出文字應該出現在狀態列或暫存的顯示區域中。 它不會永久清單中。

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
 表示取消，從回呼傳回 SCC_MSG_RTN_CANCEL。

 SCC_MSG_RTN_OK，從繼續回呼傳回。

 SCC_MSG_INFO 訊息僅供參考。

 SCC_MSG_WARNING 訊息是警告。

 SCC_MSG_ERROR 訊息會產生錯誤。

 SCC_MSG_STATUS 訊息供狀態列。

 SCC_MSG_DOCANCEL 沒有文字;傳回 IDE`SCC_MSG_RTN_OK`或`SCC_MSG_RTN_CANCEL`。

 SCC_MSG_STARTCANCEL 啟動的 [取消] 執行迴圈。

 SCC_MSG_STOPCANCEL 停止取消迴圈。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)