---
title: SccOpenProject 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a0bcb33ee214c11c369e17dc90bce138c0014fc6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768264"
---
# <a name="sccopenproject-function"></a>SccOpenProject 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會開啟現有的原始檔控制專案，或建立新的。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 lpUser  
 [in、 out]（不要超過 SCC_USER_SIZE，包括 NULL 結束字元） 的使用者名稱。  
  
 lpProjName  
 [in]識別專案的名稱的字串。  
  
 lpLocalProjPath  
 [in]專案的工作資料夾路徑。  
  
 lpAuxProjPath  
 [in、 out]選擇性的輔助字串，識別專案 （不要超過 SCC_AUXPATH_SIZE，包括 NULL 結束字元）。  
  
 lpComment  
 [in]註解至新的專案所建立。  
  
 lpTextOutProc  
 [in]若要顯示文字輸出從原始檔控制外掛程式的選擇性回呼函式。  
  
 dwFlags  
 [in]訊號是否新的專案必須先建立如果專案是未知的來源控制外掛程式。 值可以是組成`SCC_OP_CREATEIFNEW`和 `SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|在 開啟專案的成功。|  
|SCC_E_INITIALIZEFAILED|無法初始化專案。|  
|SCC_E_INVALIDUSER|使用者可能無法登入原始檔控制系統。|  
|SCC_E_COULDNOTCREATEPROJECT|專案不存在之前呼叫， `SCC_OPT_CREATEIFNEW`旗標已設定，但無法建立專案。|  
|SCC_E_PROJSYNTAXERR|無效的專案的語法。|  
|SCC_E_UNKNOWNPROJECT|專案是未知的原始檔控制外掛程式，而`SCC_OPT_CREATEIFNEW`未設定旗標。|  
|SCC_E_INVALIDFILEPATH|無效或無法使用的檔案路徑。|  
|SCC_E_NOTAUTHORIZED|若要執行這項作業不允許的使用者。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECFICERROR|不明確的失敗;未初始化原始檔控制系統。|  
  
## <a name="remarks"></a>備註  
 IDE 可能會傳入使用者名稱 (`lpUser`)，或它可能會直接傳遞指標設為空字串。 如果沒有使用者名稱，則原始檔控制外掛程式應該使用它做為預設值。 不過，如果沒有名稱傳遞，或如果具有指定名稱的登入失敗，外掛程式應該會提示使用者登入，會傳回有效的名稱，在`lpUser`當它收到有效的登入`.`因為外掛程式可能會變更使用者名稱字串IDE 一律會配置大小的緩衝區 (`SCC_USER_LEN`+ 1 或 SCC_USER_SIZE，其中包括 null 結束字元的空間)。  
  
> [!NOTE]
>  第一個 IDE 可能需要執行的動作可能會呼叫`SccOpenProject`函式或[SccGetProjPath](../extensibility/sccgetprojpath-function.md)。 基於這個理由，這兩者有相同`lpUser`參數。  
  
 `lpAuxProjPath` 並`lpProjName`讀取從方案檔，或從呼叫傳回`SccGetProjPath`函式。 這些參數會包含原始檔控制外掛程式將與專案相關聯的字串，並只對外掛程式有意義。 如果沒有這類字串是方案檔中，而且不瀏覽提示使用者 (這會傳回字串，以透過`SccGetProjPath`函式)，IDE 會將空字串傳遞兩個`lpAuxProjPath`和`lpProjName`，並預期這些值來更新根據外掛程式時，會傳回此函式。  
  
 `lpTextOutProc` 是的原始檔控制外掛程式用來顯示命令結果輸出至 IDE 所提供的回呼函式的指標。 此回呼函式中將詳細說明[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)。  
  
> [!NOTE]
>  如果原始檔控制外掛程式想要利用這一點，它必須已設定`SCC_CAP_TEXTOUT`中的旗標[SccInitialize](../extensibility/sccinitialize-function.md)。 如果未設定該旗標，或 IDE 不支援這項功能，如果`lpTextOutProc`會`NULL`。  
  
 `dwFlags`參數可控制結果，在開啟的專案目前不存在。 它包含兩種位元旗標`SCC_OP_CREATEIFNEW`和`SCC_OP_SILENTOPEN`。 如果已開啟的專案存在，函式只會開啟專案，並傳回`SCC_OK`。 如果專案不存在，而且如果`SCC_OP_CREATEIFNEW`旗標為開啟、 原始檔控制外掛程式可以在原始檔控制系統中建立專案、 開啟它，並傳回`SCC_OK`。 如果專案不存在，而且`SCC_OP_CREATEIFNEW`旗標為關閉，外掛程式應該然後檢查有無`SCC_OP_SILENTOPEN`旗標。 如果該旗標不在外掛程式可能會提示使用者輸入專案名稱。 如果該旗標會位於，外掛程式應該只傳回`SCC_E_UNKNOWNPROJECT`。  
  
## <a name="calling-order"></a>呼叫順序  
 中的事件，正常[SccInitialize](../extensibility/sccinitialize-function.md)會先呼叫，以開啟 原始檔控制工作階段。 工作階段可能是呼叫組成`SccOpenProject`，後面接著其他原始檔控制外掛程式 API 函式呼叫中，會呼叫終止[SccCloseProject](../extensibility/scccloseproject-function.md)。 這類工作階段可能會重複幾次之前[SccUninitialize](../extensibility/sccuninitialize-function.md)呼叫。  
  
 如果原始檔控制外掛程式的設定`SCC_CAP_REENTRANT`位元`SccInitialize`，則上述的工作階段順序可能會以平行方式重複許多次。 不同`pvContext`結構追蹤不同的工作階段，其中每一個`pvContext`一次是一個開啟的專案相關聯。 根據`pvContext`參數，此外掛程式可以判斷在任何特定的呼叫中參考的專案。 如果功能位元`SCC_CAP_REENTRANT`未設定，nonreentrant 原始檔控制外掛程式僅限於其能夠使用多個專案。  
  
> [!NOTE]
>  `SCC_CAP_REENTRANT` 1.1 版的原始檔控制外掛程式 API 中引進了位元。 未設定，或是在 1.0 版中，會忽略，而且所有 1.0 版原始檔控制外掛程式會假設 nonreentrant。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [字串長度限制](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)

