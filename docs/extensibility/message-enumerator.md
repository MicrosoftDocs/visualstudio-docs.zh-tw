---
title: 訊息列舉值 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fb85f727f4059e76bf5b73c71c0514a4c8cfc24
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969781"
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
 SCC_MSG_RTN_CANCEL  
 傳回從回呼，指出 [取消]。  
  
 SCC_MSG_RTN_OK  
 傳回從回呼，以繼續。  
  
 SCC_MSG_INFO  
 是參考訊息。  
  
 SCC_MSG_WARNING  
 這是一個警告訊息。  
  
 SCC_MSG_ERROR  
 這是一個錯誤訊息。  
  
 SCC_MSG_STATUS  
 訊息是針對狀態列。  
  
 SCC_MSG_DOCANCEL  
 沒有文字;傳回 IDE`SCC_MSG_RTN_OK`或`SCC_MSG_RTN_CANCEL`。  
  
 SCC_MSG_STARTCANCEL  
 啟動 [取消] 迴圈。  
  
 SCC_MSG_STOPCANCEL  
 取消迴圈就會停止。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)