---
title: "SccGetProjPath 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetProjPath
helpviewer_keywords: SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2ce41826a3a0d778c5a417496d47f290e97806fb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 函式
此函數會提示使用者輸入專案路徑，也就是只對原始檔控制外掛程式有意義的字串。 使用者時，它會呼叫：  
  
-   建立新的專案  
  
-   將現有的專案加入至版本控制  
  
-   嘗試尋找現有的版本控制專案  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 lpUser  
 [in、 out]使用者名稱 （不要超過 SCC_USER_SIZE，包括 NULL 結束字元）  
  
 lpProjName  
 [in、 out]IDE 專案、 專案工作區中或 makefile （不要超過 SCC_PRJPATH_SIZE，包括 NULL 結束字元） 的名稱。  
  
 lpLocalPath  
 [in、 out]專案的工作路徑。 如果`bAllowChangePath`是`TRUE`，原始檔控制外掛程式可以修改此字串 （不要超過 _MAX_PATH，包括 null 結束字元）。  
  
 lpAuxProjPath  
 [in、 out]傳回的專案路徑 （不要超過 SCC_PRJPATH_SIZE，包括 NULL 結束字元） 的的緩衝區。  
  
 bAllowChangePath  
 [in]如果這是`TRUE`，提示您輸入原始檔控制外掛程式即可修改`lpLocalPath`字串。  
  
 pbNew  
 [in、 out]傳入的值會指出是否要建立新的專案。 傳回值會指出成功建立專案：  
  
|內送|解譯|  
|--------------|--------------------|  
|true|使用者可建立新的專案。|  
|false|使用者可能無法建立新的專案。|  
  
|傳出|解譯|  
|--------------|--------------------|  
|true|已建立新的專案。|  
|false|選取現有的專案。|  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功建立或擷取專案。|  
|SCC_I_OPERATIONCANCELED|已取消作業。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。|  
|SCC_E_CONNECTIONFAILURE|發生問題，嘗試連接到原始檔控制系統。|  
|SCC_E_NONSPECIFICERROR|發生未指定的錯誤。|  
  
## <a name="remarks"></a>備註  
 此函式的目的是要讓 IDE 來取得參數`lpProjName`和`lpAuxProjPath`。 原始檔控制外掛程式會提示使用者提供這項資訊之後，它便會將這些兩個字串傳遞至 IDE。 IDE 持續發生在其方案檔中的這些字串，並將它們以傳送[SccOpenProject](../extensibility/sccopenproject-function.md)每當使用者開啟此專案。 這些字串要啟用的外掛程式來追蹤與專案相關的資訊。  
  
 當第一次呼叫此函數時，`lpAuxProjPath`設為空字串。 `lProjName`也可能是空的或可能包含 IDE 專案名稱，可能會使用原始檔控制外掛程式，或忽略。 此函式成功傳回時，外掛程式會傳回兩個對應的字串。 IDE 不會假設這些字串，不會使用它們，而且不允許使用者對其進行修改。 如果使用者想要變更設定，會呼叫 IDE`SccGetProjPath`同樣地，在相同的值將它傳遞已的接收先前的時間。 這可讓外掛程式完整控制這些兩個字串。  
  
 如`lpUser`、 IDE 時，可以傳遞使用者名稱，或它可能只需傳遞指標設為空字串。 如果沒有使用者名稱，原始檔控制外掛程式應該使用它做為預設值。 不過，如果未將名稱傳遞，或具有指定名稱的登入失敗，外掛程式應該會提示使用者輸入登入和傳遞回名稱`lpUser`當它收到有效的登入。 因為外掛程式可能會變更這個字串，IDE 一律會配置大小的緩衝區 (`SCC_USER_LEN`+ 1)。  
  
> [!NOTE]
>  IDE 會執行的第一個動作可能會呼叫`SccOpenProject`函式或`SccGetProjPath`函式。 因此，兩者都有相同`lpUser`參數，可讓原始檔控制外掛程式，以便讓使用者登入兩次。 即使從函式傳回表示失敗，外掛程式必須在此字串填入具有有效的登入名稱。  
  
 `lpLocalPath`是，使用者會保留在專案的目錄。 它可能是空字串。 如果沒有目前定義 （如在嘗試下載的專案，從原始檔控制系統的使用者） 的目錄，而且`bAllowChangePath`是`TRUE`，原始檔控制外掛程式可以提示使用者輸入，或使用其他方法，讓它擁有字串插入`lpLocalPath`。 如果`bAllowChangePath`是`FALSE`，外掛程式不應該變更字串中，因為使用者已使用指定的目錄中。  
  
 如果使用者建立新的專案，將原始檔控制下，原始檔控制外掛程式可能無法實際建立它在原始檔控制系統時`SccGetProjPath`呼叫。 相反地，它會傳遞回字串沿著具有非零值給`pbNew`，表示在原始檔控制系統將會建立專案。  
  
 例如，如果使用者在**新專案**Visual Studio 中的精靈他或她將專案加入至原始檔控制、 Visual Studio 會呼叫這個函式，並外掛程式會決定是否可以在原始檔控制系統，若要建立新的專案包含 Visual Studio 專案。 如果使用者按一下**取消**之前正在完成精靈，永遠不會建立專案。 如果使用者按一下**確定**，Visual Studio 會呼叫`SccOpenProject`，並傳入`SCC_OPT_CREATEIFNEW`，和原始檔控制專案建立在該時間。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)