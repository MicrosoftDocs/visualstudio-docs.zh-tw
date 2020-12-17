---
title: LPTEXTOUTPROC |Microsoft Docs
description: 深入瞭解 LPTEXTOUTPROC 函式指標。 Visual Studio IDE 會實作用來顯示錯誤和狀態的函式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a04f47a6500c0cd2174d0567029a4f5c86d9f62d
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615723"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

當使用者從整合式開發環境內部執行原始檔控制作業時 (IDE) ，原始檔控制外掛程式可能會想要傳達與作業相關的錯誤或狀態訊息。 外掛程式可以針對此目的顯示自己的訊息方塊。 不過，若要進行更緊密的整合，外掛程式可以將字串傳遞至 IDE，然後以原生方式顯示狀態資訊。 這項機制是 `LPTEXTOUTPROC` 函數指標。 IDE 會 (更詳細地說明此函式，以顯示錯誤和狀態) 。

在呼叫 SccOpenProject 時，IDE 會將函式指標傳遞給此函式的函式指標，作為 `lpTextOutProc` 參數。 [](../extensibility/sccopenproject-function.md) 在 SCC 作業期間（例如，在呼叫涉及許多檔案的 [SccGet](../extensibility/sccget-function.md) 中間），外掛程式可以呼叫函式 `LPTEXTOUTPROC` ，定期傳遞要顯示的字串。 IDE 可以適當地在狀態列、輸出視窗或個別的訊息方塊中顯示這些字串。 IDE 可以選擇性地顯示具有 [ **取消** ] 按鈕的特定訊息。 這可讓使用者取消作業，並讓 IDE 能夠將這項資訊傳回外掛程式。

## <a name="signature"></a>簽章
 IDE 的 output 函數具有下列簽章：

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>參數

display_string

要顯示的文字字串。 這個字串不應以換行字元或換行字元來終止。

mesg_type

訊息的類型。 下表列出此參數支援的值。

|值|描述|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|訊息會被視為資訊、警告或錯誤。|
|`SCC_MSG_STATUS`|此訊息會顯示狀態，而且可以顯示在狀態列中。|
|`SCC_MSG_DOCANCEL`|未傳送任何訊息字串。|
|`SCC_MSG_STARTCANCEL`|開始顯示 [ **取消** ] 按鈕。|
|`SCC_MSG_STOPCANCEL`|停止顯示 [ **取消** ] 按鈕。|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|如果要取消背景作業，則詢問 IDE： `SCC_MSG_RTN_CANCEL` 如果作業已取消，則 ide 會傳回，否則會傳回 `SCC_MSG_RTN_OK` 。 `display_string`參數會轉換成[SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled)結構，此結構是由原始檔控制外掛程式所提供。|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|從版本控制抓取檔案之前，告訴 IDE 檔案。 `display_string`參數會轉換成[SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile)結構，此結構是由原始檔控制外掛程式所提供。|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|從版本控制中取出檔案之後，告訴 IDE 該檔案的相關資訊。 `display_string`參數會轉換成[SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile)結構，此結構是由原始檔控制外掛程式所提供。|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|告訴 IDE 目前的背景操作狀態。 `display_string`參數會轉換成[SccMsgDataOnMessage](#LinkSccMsgDataOnMessage)結構，此結構是由原始檔控制外掛程式所提供。|

## <a name="return-value"></a>傳回值

|值|描述|
|-----------|-----------------|
|SCC_MSG_RTN_OK|已顯示字串或作業已順利完成。|
|SCC_MSG_RTN_CANCEL|使用者想要取消操作。|

## <a name="example"></a>範例
 假設 IDE 以二十個檔案名來呼叫 [SccGet](../extensibility/sccget-function.md) 。 原始檔控制外掛程式想要防止在檔案取得的過程中取消作業。 取得每個檔案之後，它會呼叫 `lpTextOutProc` ，並將每個檔案的狀態資訊傳遞給它，並在 `SCC_MSG_DOCANCEL` 沒有要報告的狀態時傳送訊息。 如果外掛程式從 IDE 收到的傳回值 `SCC_MSG_RTN_CANCEL` ，則會立即取消 get 作業，如此就不會再抓取任何檔案。

## <a name="structures"></a>結構

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 此結構會隨訊息一起傳送 `SCC_MSG_BACKGROUND_IS_CANCELLED` 。 它是用來傳達已取消之背景作業的識別碼。

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 此結構會隨訊息一起傳送 `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` 。 它是用來傳達要抓取之檔案的名稱，以及執行抓取之背景作業的識別碼。

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 此結構會隨訊息一起傳送 `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` 。 它是用來傳達抓取指定檔案的結果，以及執行抓取之背景作業的識別碼。 請參閱 [SccGet](../extensibility/sccget-function.md) 的傳回值，以取得結果。

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 此結構會隨訊息一起傳送 `SCC_MSG_BACKGROUND_ON_MESSAGE` 。 它是用來傳達背景作業的目前狀態。 狀態會以 IDE 所顯示的字串表示，並 `bIsError` 指出訊息 (的嚴重性、 `TRUE` `FALSE` 警告或參考用訊息的訊息) 。 此外，也會提供傳送狀態之背景作業的識別碼。

## <a name="code-example"></a>程式碼範例
 以下是呼叫 `LPTEXTOUTPROC` 以傳送訊息的簡單範例 `SCC_MSG_BACKGROUND_ON_MESSAGE` ，顯示如何轉換該呼叫的結構。

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
- [IDE 所執行的回呼函數](../extensibility/callback-functions-implemented-by-the-ide.md)
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
