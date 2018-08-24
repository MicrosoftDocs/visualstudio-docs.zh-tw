---
title: LPTEXTOUTPROC |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc89caf18523e57671a18884fdb6b2961d962b99
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638514"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
當使用者執行從原始檔控制作業，在整合式的開發環境 (IDE) 內時，原始檔控制外掛程式可能會想要傳達與作業相關的錯誤或狀態訊息。 此外掛程式可以針對此目的顯示自己的訊息方塊。 不過，進行更多的無縫整合，外掛程式可以傳遞字串給 IDE，然後顯示其原生方法來顯示狀態資訊。 這個機制是`LPTEXTOUTPROC`函式指標。 IDE 會實作此函式 （在下面詳細說明） 來顯示錯誤和狀態。  
  
 IDE 會傳遞至原始檔控制外掛程式函式指標，此函式，當成`lpTextOutProc`參數，呼叫時[SccOpenProject](../extensibility/sccopenproject-function.md)。 SCC 作業期間，例如，如果呼叫的中間[SccGet](../extensibility/sccget-function.md)牽涉到許多檔案，此外掛程式可以呼叫`LPTEXTOUTPROC`函式，定期傳遞要顯示的字串。 IDE 可能會在狀態列上，在 [輸出] 視窗中，或在個別的訊息方塊中，視需要顯示這些字串。 （選擇性） 在 IDE 可能是能夠顯示與特定訊息**取消** 按鈕。 這可讓使用者取消作業，並提供 IDE 能夠將此資訊傳回給外掛程式。  
  
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
 要顯示的文字字串。 此字串應該以換行的傳回或換行字元終止。  
  
 mesg_type  
 訊息的類型。 下表列出支援的值，這個參數。  
  
|值|描述|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|將訊息視為資訊、 警告或錯誤。|  
|`SCC_MSG_STATUS`|訊息會顯示狀態，且可以在狀態列中顯示。|  
|`SCC_MSG_DOCANCEL`|不傳送任何訊息字串。|  
|`SCC_MSG_STARTCANCEL`|開始顯示**取消** 按鈕。|  
|`SCC_MSG_STOPCANCEL`|會停止顯示**取消** 按鈕。|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|要求 IDE 在背景作業是否要取消： 傳回 IDE`SCC_MSG_RTN_CANCEL`作業已取消; 否則會傳回`SCC_MSG_RTN_OK`。 `display_string`參數會轉換為[SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled)原始檔控制外掛程式所提供的結構。|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|會指示 IDE 相關檔案，它會從版本控制之前。 `display_string`參數會轉換為[SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile)原始檔控制外掛程式所提供的結構。|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|會指示 IDE 相關檔案之後擷取從版本控制。 `display_string`參數會轉換為[SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile)原始檔控制外掛程式所提供的結構。|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|會告訴 IDE 的背景作業的目前狀態。 `display_string`參數會轉換為[SccMsgDataOnMessage](#LinkSccMsgDataOnMessage)原始檔控制外掛程式所提供的結構。|  
  
## <a name="return-value"></a>傳回值  
  
|值|描述|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|顯示的字串，或作業已順利完成。|  
|SCC_MSG_RTN_CANCEL|使用者想要取消作業。|  
  
## <a name="example"></a>範例  
 假設，IDE 會呼叫[SccGet](../extensibility/sccget-function.md)以 20 個檔案名稱。 原始檔控制外掛程式想要防止取消中間檔案 get 作業。 取得每個檔案之後, 它會呼叫`lpTextOutProc`、 每個檔案，在傳遞的狀態資訊，並將傳送`SCC_MSG_DOCANCEL`訊息是否報告任何狀態。 如果在任何階段外掛程式會收到傳回值`SCC_MSG_RTN_CANCEL`從 IDE，就會取消取得作業立即執行，以便擷取更多檔案。  
  
## <a name="structures"></a>結構  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 此結構會傳送具有`SCC_MSG_BACKGROUND_IS_CANCELLED`訊息。 它用來通訊已取消背景作業的識別碼。  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 此結構會傳送具有`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`訊息。 它用來傳達即將要擷取之檔案的名稱，以及擷取正在進行背景作業的識別碼。  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 此結構會傳送具有`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`訊息。 它用來通訊的結果擷取指定的檔案，以及未擷取背景作業的識別碼。 請參閱的傳回值[SccGet](../extensibility/sccget-function.md)的項目可以如此一來提供。  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 此結構會傳送具有`SCC_MSG_BACKGROUND_ON_MESSAGE`訊息。 它用來通訊的背景作業的目前狀態。 狀態會表示為字串，以顯示 ide，並`bIsError`指出訊息的嚴重性 (`TRUE`錯誤訊息;`FALSE`警告或參考用訊息)。 此外，也會給予傳送狀態背景作業的識別碼。  
  
## <a name="code-example"></a>程式碼範例  
 以下是呼叫的簡短範例`LPTEXTOUTPROC`傳送`SCC_MSG_BACKGROUND_ON_MESSAGE`訊息，顯示如何呼叫轉換的結構。  
  
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