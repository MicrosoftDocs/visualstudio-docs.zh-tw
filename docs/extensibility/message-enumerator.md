---
title: 消息枚舉器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702512"
---
# <a name="message-enumerator"></a>訊息列舉器
以下標誌用於`TEXTOUTPROC`函數,該函數是IDE在調用[SccOpenProject](../extensibility/sccopenproject-function.md)時提供的回調函數(有關回調函數的詳細資訊,請參閱[LPTEXTOUTPROC)。](../extensibility/lptextoutproc.md)

 如果要求 IDE 取消進程,它可能會收到取消消息之一。 在這種情況下,原始程式碼管理外掛`SCC_MSG_STARTCANCEL`程式用於要求 IDE 顯示 **「取消」** 按鈕。 在此之後,可能會發送任何一組正常消息。 如果其中任何一個`SCC_MSG_RTN_CANCEL`返回,則外掛程式將退出該操作並返回。 外掛程式還會定期輪`SCC_MSG_DOCANCEL`詢 以確定使用者是否已取消該操作。 完成所有操作或使用者已取消操作後, 外掛程式`SCC_MSG_STOPCANCEL`會送出 。 SCC_MSG_WARNING`SCC_MSG_INFO`和SCC_MSG_ERROR類型用於顯示在消息滾動清單中的郵件。 `SCC_MSG_STATUS`是一種特殊類型,指示文本應顯示在狀態列或臨時顯示區域中。 它不會永久保留在清單中。

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
 SCC_MSG_RTN_CANCEL從回調返回以指示取消。

 SCC_MSG_RTN_OK從回調返回以繼續。

 SCC_MSG_INFO消息是資訊性的。

 SCC_MSG_WARNING消息是一個警告。

 SCC_MSG_ERROR消息是一個錯誤。

 SCC_MSG_STATUS消息用於狀態列。

 SCC_MSG_DOCANCEL 無文字;IDE`SCC_MSG_RTN_OK``SCC_MSG_RTN_CANCEL`傳回或 。

 SCC_MSG_STARTCANCEL啟動取消迴圈。

 SCC_MSG_STOPCANCEL 停止取消迴圈。

## <a name="see-also"></a>另請參閱
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
