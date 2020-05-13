---
title: SccOpen專案功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbf566e593bb1ddbc31c70de1570d746a14fbdcf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700576"
---
# <a name="sccopenproject-function"></a>SccOpenProject 函式
此函數將打開現有原始程式碼管理專案或創建新的原始程式碼管理專案。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccOpenProject (
   LPVOID        pvContext,
   HWND          hWnd,
   LPSTR         lpUser,
   LPCSTR        lpProjName,
   LPCSTR        lpLocalProjPath,
   LPSTR         lpAuxProjPath,
   LPCSTR        lpComment,
   LPTEXTOUTPROC lpTextOutProc,
   LONG          dwFlags
);
```

#### <a name="parameters"></a>參數
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 lpUser

[進出]使用者的名稱(不超過SCC_USER_SIZE,包括 NULL 終止符)。

 lpProjName

[在]識別專案名稱的字串。

 lpLocalProjPath

[在]專案工作資料夾的路徑。

 lpAuxProjPath

[進出]標識專案的可選輔助字串(不超過SCC_AUXPATH_SIZE,包括 NULL 終止符)。

 lpComment

[在]註釋正在創建的新專案。

 lpTextOutProc

[在]用於顯示源控制元件的文字輸出的可選回檔功能。

 dwFlags

[在]如果源控制外掛程式不知道專案,則指示是否需要創建新專案。 值可以是`SCC_OP_CREATEIFNEW`與`SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|成功打開專案。|
|SCC_E_INITIALIZEFAILED|無法初始化專案。|
|SCC_E_INVALIDUSER|使用者無法登錄到原始程式碼管理系統。|
|SCC_E_COULDNOTCREATEPROJECT|專案在調用之前不存在;因此,該專案在調用之前不存在。 已`SCC_OPT_CREATEIFNEW`設置標誌,但無法創建專案。|
|SCC_E_PROJSYNTAXERR|無效的專案語法。|
|SCC_E_UNKNOWNPROJECT|來源控制外掛程式不知道該專案`SCC_OPT_CREATEIFNEW`, 並且未設置標誌。|
|SCC_E_INVALIDFILEPATH|無效或無法使用的檔案路徑。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此操作。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_NONSPECFICERROR|非特異性故障;源控制系統未初始化。|

## <a name="remarks"></a>備註
 IDE 可能傳遞使用者名`lpUser`( ),也可以簡單地將指標傳遞到空字串。 如果存在使用者名,原始程式碼管理外掛程式應將其用作預設值。 但是,如果未傳遞名稱,或者登錄失敗,並且給定名稱失敗,外掛程式應提示使用者登錄,並在收到有效`lpUser``.`登錄 時返回有效名稱,因為外掛程式可能會更改使用者名字符串,IDE 將始終分配大小緩衝`SCC_USER_LEN`區(+1 或SCC_USER_SIZE,其中包括空終止符的空間)。

> [!NOTE]
> IDE 可能需要執行的第一個操作可能是`SccOpenProject`對 函數或[SccGetProjPath](../extensibility/sccgetprojpath-function.md)的調用。 因此,它們都有相同的`lpUser`參數。

 `lpAuxProjPath`並從`lpProjName`解決方案檔中讀取,或者從調用函數`SccGetProjPath`返回它們。 這些參數包含原始程式碼管理外掛程式與專案關聯字串,並且僅對外掛程式有意義。 如果解決方案檔中沒有此類字串,並且未提示用戶流覽(這將透過`SccGetProjPath`函數返回字串),則 IDE 將傳遞`lpAuxProjPath``lpProjName`和的空字串,並期望此函數返回時外掛程式會更新這些值。

 `lpTextOutProc`是 IDE 為顯示命令結果輸出而向原始程式碼管理外掛程式提供的回調函數的指標。 此回調函數在[LPTEXTOUTPROC 中](../extensibility/lptextoutproc.md)進行了詳細介紹。

> [!NOTE]
> 如果原始程式碼管理外掛程式打算利用這一點,它必須在[Scc 初始化](../extensibility/sccinitialize-function.md)中`SCC_CAP_TEXTOUT`設置了標誌。 沒有未設定這個旗標,或是 IDE 不支援`lpTextOutProc`此功能,`NULL`則會為 。

 如果`dwFlags`當前未打開的專案不存在,參數將控制結果。 它由兩個位標誌`SCC_OP_CREATEIFNEW`和`SCC_OP_SILENTOPEN`組成。 如果開啟的專案已存在,則函數只需開啟專案並返回`SCC_OK`。 如果專案不存在,並且`SCC_OP_CREATEIFNEW`標誌處於開啟狀態,原始程式碼管理外掛程式可以在原始程式碼管理系統中建立項目,開啟`SCC_OK`它,然後傳回 。 如果專案不存在,並且`SCC_OP_CREATEIFNEW`標誌已關閉,則外掛程式應`SCC_OP_SILENTOPEN`檢查該 標誌。 如果該標誌未打開,外掛程式可能會提示使用者輸入專案名稱。 如果該旗標處於開啟,外掛程式應`SCC_E_UNKNOWNPROJECT`僅返回 。

## <a name="calling-order"></a>呼叫訂單
 在正常事件過程中,將首先調用[Scc 初始化](../extensibility/sccinitialize-function.md)以打開原始程式碼管理工作階段。 會話可以包含對`SccOpenProject`的調用,然後是其他原始程式碼管理外掛程式 API 函數調用,並且將隨著對[SccCloseProject](../extensibility/scccloseproject-function.md)的調用而終止。 在調用[SccUn初始化](../extensibility/sccuninitialize-function.md)之前,可以重複多次此類會話。

 如果原始程式碼管理外掛`SCC_CAP_REENTRANT`程式將位`SccInitialize`設置在中,則上述會話序列可能會並行重複多次。 不同的`pvContext`結構跟蹤不同的會話,其中`pvContext`每個 會話一次與一個打開的項目相關聯。 根據參數`pvContext`,外掛程式可以確定任何特定調用中引用哪個專案。 如果未設置功能位`SCC_CAP_REENTRANT`,則非重新進入源控制外掛程式處理多個專案的能力受到限制。

> [!NOTE]
> 該`SCC_CAP_REENTRANT`位是在原始程式碼管理外掛程式 API 的 1.1 版中引入的。 它在版本 1.0 中未設置或被忽略,並且所有版本 1.0 原始程式碼管理外掛程式都假定為非重新進入。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [字串長度限制](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
