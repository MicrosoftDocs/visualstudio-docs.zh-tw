---
title: 列舉值的訊息 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bc945908ac61a0eaa4df49c76725b2291686eac3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="message-enumerator"></a>訊息的列舉值
下列旗標用於`TEXTOUTPROC`函式，也就是 IDE 提供呼叫時的回呼函式[SccOpenProject](../extensibility/sccopenproject-function.md) (請參閱[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)如需詳細資訊，回呼上函式）。  
  
 如果 IDE 會要求取消此程序，它可能會取消訊息。 在此情況下，原始檔控制外掛程式使用`SCC_MSG_STARTCANCEL`詢問要顯示在 IDE**取消** 按鈕。 在此之後，可能會傳送一般訊息的任何設定。 如果任何這些傳回`SCC_MSG_RTN_CANCEL`，然後外掛程式會結束作業並傳回。 外掛程式也輪詢`SCC_MSG_DOCANCEL`定期來判斷是否使用者已取消該作業。 當所有作業完成都後，或如果使用者已取消，此外掛程式就會傳送`SCC_MSG_STOPCANCEL`。 `SCC_MSG_INFO`，SCC_MSG_WARNING，和 SCC_MSG_ERROR 類型可用來取得訊息的捲動清單中顯示的訊息。 `SCC_MSG_STATUS` 是一種特殊類型，表示文字應該出現在狀態列上或暫存的顯示區域。 它不會不會維持永久清單中。  
  
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
 SCC_MSG_RTN_CANCEL  
 傳回從回呼來表示 [取消]。  
  
 SCC_MSG_RTN_OK  
 傳回從回呼，以繼續。  
  
 SCC_MSG_INFO  
 是參考訊息。  
  
 SCC_MSG_WARNING  
 訊息是一個警告。  
  
 SCC_MSG_ERROR  
 錯誤訊息。  
  
 SCC_MSG_STATUS  
 訊息是為了收集的狀態列。  
  
 SCC_MSG_DOCANCEL  
 沒有文字;傳回 IDE`SCC_MSG_RTN_OK`或`SCC_MSG_RTN_CANCEL`。  
  
 SCC_MSG_STARTCANCEL  
 啟動 [取消] 5d; 迴圈。  
  
 SCC_MSG_STOPCANCEL  
 取消迴圈就會停止。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)