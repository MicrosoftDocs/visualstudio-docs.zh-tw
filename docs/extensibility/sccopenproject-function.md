---
title: SccOpenProject 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15d9cf6d5fa4533b5ee0ff65f8aeae86df3d571a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sccopenproject-function"></a>SccOpenProject 函式
此函式開啟現有的原始檔控制專案，或建立一個新。  
  
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
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 lpUser  
 [in、 out]使用者 （不要超過 SCC_USER_SIZE，包括 NULL 結束字元） 的名稱。  
  
 lpProjName  
 [in]識別專案名稱的字串。  
  
 lpLocalProjPath  
 [in]專案的工作資料夾路徑。  
  
 lpAuxProjPath  
 [in、 out]選擇性的輔助字串，識別專案 （不要超過 SCC_AUXPATH_SIZE，包括 NULL 結束字元）。  
  
 lpComment  
 [in]正在建立新專案為註解。  
  
 lpTextOutProc  
 [in]從原始檔控制外掛程式輸出的文字顯示選擇性的回呼函式。  
  
 將 dwFlags  
 [in]訊號是否需要如果專案是未知來源建立新的專案控制外掛程式。 值可以是組合`SCC_OP_CREATEIFNEW`和 `SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|在中開啟專案的成功。|  
|SCC_E_INITIALIZEFAILED|無法初始化專案。|  
|SCC_E_INVALIDUSER|使用者可能無法登入原始檔控制系統。|  
|SCC_E_COULDNOTCREATEPROJECT|專案不存在之前呼叫。 `SCC_OPT_CREATEIFNEW`旗標已設定，但無法建立專案。|  
|SCC_E_PROJSYNTAXERR|無效的專案的語法。|  
|SCC_E_UNKNOWNPROJECT|專案不知道原始檔控制外掛程式，而`SCC_OPT_CREATEIFNEW`未設定旗標。|  
|SCC_E_INVALIDFILEPATH|無效或無法使用的檔案路徑。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECFICERROR|不明確的失敗。未初始化原始檔控制系統。|  
  
## <a name="remarks"></a>備註  
 IDE，可以傳遞使用者名稱 (`lpUser`)，或它可能只需傳遞指標設為空字串。 如果沒有使用者名稱，原始檔控制外掛程式應該使用它做為預設值。 不過，如果未將名稱傳遞，或具有指定名稱的登入失敗，外掛程式應該會提示使用者登入，並將傳回中的有效名稱`lpUser`當它收到有效的登入`.`因為外掛程式可能會變更的使用者名稱的字串IDE 一律會配置大小的緩衝區 (`SCC_USER_LEN`+ 1 或 SCC_USER_SIZE，其中包括 null 結束字元的空間)。  
  
> [!NOTE]
>  第一個 IDE 可能需要執行的動作可能會呼叫`SccOpenProject`函式或[SccGetProjPath](../extensibility/sccgetprojpath-function.md)。 基於這個理由，兩者都有相同`lpUser`參數。  
  
 `lpAuxProjPath` 和`lpProjName`會讀取方案檔，或從呼叫傳回`SccGetProjPath`函式。 這些參數包含原始檔控制外掛程式將與專案相關聯的字串，並只對外掛程式都具有意義。 如果沒有這類字串中的方案檔，而且不瀏覽提示使用者 (這會傳回字串，以透過`SccGetProjPath`函式)，IDE 會將空字串傳遞兩個`lpAuxProjPath`和`lpProjName`，並且預期會更新這些值根據外掛程式時，此函式會傳回。  
  
 `lpTextOutProc` 為原始檔控制外掛程式用來顯示命令的結果輸出至 IDE 所提供的回呼函式的指標。 此回呼函式中將詳細說明[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)。  
  
> [!NOTE]
>  如果原始檔控制外掛程式想要利用這一點，它必須有設定`SCC_CAP_TEXTOUT`加上旗標[SccInitialize](../extensibility/sccinitialize-function.md)。 如果未設定該旗標，或 IDE 不支援這項功能，`lpTextOutProc`將`NULL`。  
  
 `dwFlags`參數控制結果，開啟專案目前不存在。 它包含兩位元旗標，`SCC_OP_CREATEIFNEW`和`SCC_OP_SILENTOPEN`。 如果已開啟的專案存在、 函式只需開啟專案，並傳回`SCC_OK`。 如果專案不存在，而且如果`SCC_OP_CREATEIFNEW`旗標是 on，原始檔控制外掛程式可以在原始檔控制系統中建立專案、 開啟它，並傳回`SCC_OK`。 如果專案不存在，而且如果`SCC_OP_CREATEIFNEW`旗標為關閉，外掛程式應然後檢查是否有`SCC_OP_SILENTOPEN`旗標。 如果該旗標不是在外掛程式可能會提示使用者輸入專案名稱。 如果該旗標會位於，外掛程式應該只傳回`SCC_E_UNKNOWNPROJECT`。  
  
## <a name="calling-order"></a>呼叫順序  
 在正常操作程序的事件， [SccInitialize](../extensibility/sccinitialize-function.md)會先呼叫，以開啟原始檔控制工作階段。 工作階段可能會包含呼叫`SccOpenProject`、 後面接著其他原始檔控制外掛程式 API 函式呼叫，並會終止，且呼叫[SccCloseProject](../extensibility/scccloseproject-function.md)。 這類工作階段可能會重複許多次之前[SccUninitialize](../extensibility/sccuninitialize-function.md)呼叫。  
  
 如果原始檔控制外掛程式設定`SCC_CAP_REENTRANT`位元`SccInitialize`，則上述的工作階段順序可能會以平行方式重複許多次。 不同`pvContext`結構追蹤不同的工作階段中，每位`pvContext`每次都與一個開啟的專案。 根據`pvContext`參數，此外掛程式可以判斷哪個專案參考的任何特定的呼叫。 如果位元功能`SCC_CAP_REENTRANT`未設定，nonreentrant 原始檔控制外掛程式會受限於他們能夠使用多個專案。  
  
> [!NOTE]
>  `SCC_CAP_REENTRANT`位元原始檔控制外掛程式 API 1.1 版中引進。 未設定，或在 1.0 版中，會被忽略，並假設為 nonreentrant 所有 1.0 版原始檔控制外掛程式。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [字串長度限制](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)