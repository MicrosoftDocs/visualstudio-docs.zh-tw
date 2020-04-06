---
title: LPTEXTOUTPROC |微軟文件
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
ms.openlocfilehash: 38c3e8263b9a30058c2de019e5e92160b716aa71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702795"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

當使用者從整合式開發環境 (IDE) 內部執行原始程式碼管理操作時,原始程式碼管理外掛程式可能需要傳達與操作相關的錯誤或狀態訊息。 為此,外掛程式可以顯示自己的消息框。 但是,為了進行更無縫的集成,外掛程式可以將字串傳遞給IDE,IDE然後以本機方式顯示狀態資訊。 這是`LPTEXTOUTPROC`函數指標。 IDE 實現此函數(下面將詳細介紹),用於顯示錯誤和狀態。

調用`lpTextOutProc`[SccOpenProject](../extensibility/sccopenproject-function.md)時,IDE 將函數指標傳遞給此函數(作為參數)傳遞給原始程式碼管理外掛程式。 例如,在 SCC 操作期間,在調用涉及許多檔的[SccGet](../extensibility/sccget-function.md)時,外`LPTEXTOUTPROC`掛程式可以調用 該函數,定期傳遞字串以顯示。 IDE 可以根據需要在狀態列、輸出視窗中或單獨的消息框中顯示這些字串。 或者,IDE 可能可以使用 **"取消"** 按鈕顯示某些消息。 這使用戶能夠取消該操作,並使IDE能夠將此資訊傳回外掛程式。

## <a name="signature"></a>簽章
 IDE 的輸出函數具有以下簽署:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>參數

display_string

要顯示的文字字串。 不應使用回車符或換行符終止此字串。

mesg_type

訊息的類型。 下表列出了此參數的支援值。

|值|描述|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|該消息被視為資訊、警告或錯誤。|
|`SCC_MSG_STATUS`|該消息顯示狀態,可以顯示在狀態列中。|
|`SCC_MSG_DOCANCEL`|未送出消息字串。|
|`SCC_MSG_STARTCANCEL`|開始顯示 **「取消」** 按鈕。|
|`SCC_MSG_STOPCANCEL`|停止顯示 **「取消」** 按鈕。|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|詢問 IDE 是否要取消後台操作:如果操作`SCC_MSG_RTN_CANCEL`被取消 ,IDE 將返回;否則,傳`SCC_MSG_RTN_OK`回 。 該`display_string`參數被強制轉換為[SccMsgDataIsCanceled](#LinkSccMsgDataIsCancelled)結構,該結構由原始程式碼管理外掛程式提供。|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|在從版本控制器索檔之前,先向IDE介紹該檔。 該`display_string`參數被強制轉換為[SccMsgDataOnOnGetFile](#LinkSccMsgDataOnBeforeGetFile)結構,該結構由原始程式碼管理外掛程式提供。|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|從版本控制檢索檔後,向IDE告知該檔。 該`display_string`參數被強制轉換為[SccMsgDataOnOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile)結構,該結構由原始程式碼管理外掛程式提供。|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|告訴 IDE 後台操作的當前狀態。 該`display_string`參數被強制轉換為[SccMsgDataOnMessage](#LinkSccMsgDataOnMessage)結構,該結構由原始程式碼管理外掛程式提供。|

## <a name="return-value"></a>傳回值

|值|描述|
|-----------|-----------------|
|SCC_MSG_RTN_OK|顯示字串或操作已成功完成。|
|SCC_MSG_RTN_CANCEL|使用者希望取消該操作。|

## <a name="example"></a>範例
 假設 IDE 調用具有 20 個檔名[的 SccGet。](../extensibility/sccget-function.md) 原始程式碼管理外掛程式希望防止在檔案獲取中間取消操作。 取得每個檔後,它會調用`lpTextOutProc`,傳遞每個檔的狀態資訊,如果該檔沒有要報告`SCC_MSG_DOCANCEL`的狀態 ,則發送消息。 如果外掛程式在任何時候收到來自IDE`SCC_MSG_RTN_CANCEL`的返回值,它會立即取消get操作,以便不再檢索檔。

## <a name="structures"></a>結構

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDatais 已取消

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 此結構隨消息一`SCC_MSG_BACKGROUND_IS_CANCELLED`起發送。 它用於傳達已取消的背景操作的 ID。

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataon 之前取得檔案

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 此結構隨消息一`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`起發送。 它用於傳達要檢索的文件的名稱和執行檢索的後台操作的 ID。

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgdataon 後取得檔案

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 此結構隨消息一`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`起發送。 它用於傳達檢索指定檔的結果以及進行檢索的後台操作的 ID。 有關可以因此提供的內容,請參閱[SccGet](../extensibility/sccget-function.md)的返回值。

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataon訊息

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 此結構隨消息一`SCC_MSG_BACKGROUND_ON_MESSAGE`起發送。 它用於傳達後台操作的當前狀態。 狀態表示為 IDE 顯示的字串,`bIsError`並指示消息的嚴重性`TRUE`( 對於錯誤消息;`FALSE`用於警告或資訊性消息)。 還提供了發送狀態的後台操作的 ID。

## <a name="code-example"></a>程式碼範例
 下面是調用`LPTEXTOUTPROC`發送消息的簡`SCC_MSG_BACKGROUND_ON_MESSAGE`短 示例,演示如何為調用強制轉換結構。

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
- [IDE 實作的回檔](../extensibility/callback-functions-implemented-by-the-ide.md)
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
