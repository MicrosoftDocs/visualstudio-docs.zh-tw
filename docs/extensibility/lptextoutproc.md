---
title: "LPTEXTOUTPROC |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 658193f526123d237ef9b90a05861492b9f007c9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
當使用者執行從原始檔控制作業，在整合式的開發環境 (IDE) 內時，原始檔控制外掛程式可能會想要傳達與作業相關的錯誤或狀態訊息。 外掛程式可以針對此用途顯示自己的訊息方塊。 不過，多個緊密整合，外掛程式可以傳遞字串給 IDE，並接著顯示在其原生方法來顯示狀態資訊。 這個機制是`LPTEXTOUTPROC`函式指標。 IDE 會實作此函式 （以下更詳細說明） 來顯示錯誤和狀態。  
  
 IDE 會傳遞至原始檔控制外掛程式函式指標，此函式，當成`lpTextOutProc`參數呼叫時[SccOpenProject](../extensibility/sccopenproject-function.md)。 SCC 作業期間，例如，中間呼叫[SccGet](../extensibility/sccget-function.md)涉及許多檔案，此外掛程式可以呼叫`LPTEXTOUTPROC`函式，定期傳遞要顯示的字串。 IDE 狀態列，在輸出視窗中，或在個別的訊息方塊中，視需要上可能會顯示這些字串。 （選擇性） 可能無法顯示特定訊息與 IDE**取消** 按鈕。 這可讓使用者取消作業，並讓 IDE 回到外掛程式傳遞這項資訊的能力。  
  
## <a name="signature"></a>簽章  
 IDE 的輸出函式具有下列簽章：  
  
```cpp  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>參數  
 display_string  
 若要顯示的文字字串。 這個字串不應該以歸位字元傳回或換行字元結尾。  
  
 mesg_type  
 訊息的類型。 下表列出支援的值，這個參數。  
  
|值|說明|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|訊息會視為資訊、 警告或錯誤。|  
|`SCC_MSG_STATUS`|訊息會顯示狀態，並可以在狀態列中顯示。|  
|`SCC_MSG_DOCANCEL`|不傳送任何訊息字串。|  
|`SCC_MSG_STARTCANCEL`|開始顯示**取消** 按鈕。|  
|`SCC_MSG_STOPCANCEL`|停止顯示**取消** 按鈕。|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|詢問 IDE 背景作業是否會取消： IDE 傳回`SCC_MSG_RTN_CANCEL`若作業已取消; 否則傳回`SCC_MSG_RTN_OK`。 `display_string`參數就會轉換為[SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled)結構，也就由原始檔控制外掛程式所提供。|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|擷取從版本控制之前，請告知 IDE 檔案的相關。 `display_string`參數就會轉換為[SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile)結構，也就由原始檔控制外掛程式所提供。|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|檔案的相關告知 IDE，它已從版本控制中擷取之後。 `display_string`參數就會轉換為[SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile)結構，也就由原始檔控制外掛程式所提供。|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|會告知在 IDE 的背景作業的目前狀態。 `display_string`參數就會轉換為[SccMsgDataOnMessage](#LinkSccMsgDataOnMessage)結構，也就由原始檔控制外掛程式所提供。|  
  
## <a name="return-value"></a>傳回值  
  
|值|說明|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|顯示字串，或該作業未順利完成。|  
|SCC_MSG_RTN_CANCEL|使用者想要取消作業。|  
  
## <a name="example"></a>範例  
 假設 IDE 呼叫[SccGet](../extensibility/sccget-function.md)與 20 個檔案名稱。 原始檔控制外掛程式想要防止取消中間檔案 get 作業。 取得之後每個檔案，它會呼叫`lpTextOutProc`、 每個檔案，在傳遞的狀態資訊並傳送`SCC_MSG_DOCANCEL`訊息有沒有狀態可以報告。 如果在任何時候外掛程式收到傳回值的`SCC_MSG_RTN_CANCEL`從 IDE 時，就會取消取得作業立即，以便擷取任何多個檔案。  
  
## <a name="structures"></a>結構  
  
###  <a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 此結構會傳送具有`SCC_MSG_BACKGROUND_IS_CANCELLED`訊息。 它用來通訊的背景作業已取消的識別碼。  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 此結構會傳送具有`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`訊息。 它用來傳達即將要擷取檔案的名稱，以及正在進行擷取，背景作業的識別碼。  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 此結構會傳送具有`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`訊息。 它用來通訊的結果擷取指定的檔案，以及未擷取背景作業的識別碼。 請參閱的傳回值[SccGet](../extensibility/sccget-function.md)的功能都可以獲得結果。  
  
###  <a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 此結構會傳送具有`SCC_MSG_BACKGROUND_ON_MESSAGE`訊息。 它用來通訊的背景作業的目前狀態。 狀態會表示為要顯示在 IDE 中的字串和`bIsError`表示訊息的嚴重性 (`TRUE`的錯誤訊息。`FALSE`警告或參考用訊息)。 也會指定傳送狀態的背景作業的識別碼。  
  
## <a name="code-example"></a>程式碼範例  
 以下是簡短的範例於呼叫`LPTEXTOUTPROC`傳送`SCC_MSG_BACKGROUND_ON_MESSAGE`訊息，顯示如何呼叫轉換的結構。  
  
```cpp  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
