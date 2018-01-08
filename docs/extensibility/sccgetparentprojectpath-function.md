---
title: "SccGetParentProjectPath 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetParentProjectPath
helpviewer_keywords: SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8395d73a48d4c8501ba834b2168b5bcbc8019b8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath 函式
此函式會判斷指定的專案的父專案路徑。 使用者加入原始檔控制的 Visual Studio 專案時，會呼叫此函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容指標。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 lpUser  
 [in、 out]使用者名稱 （最多 SCC_USER_SIZE，包括 NULL 結束字元)。  
  
 lpProjPath  
 [in]識別 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 的專案路徑的字串。  
  
 lpAuxProjPath  
 [in、 out]識別 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 專案的輔助字串。  
  
 lpParentProjPath  
 [in、 out]識別父專案路徑 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 的輸出字串。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功取得父專案路徑。|  
|SCC_E_INITIALIZEFAILED|無法初始化專案。|  
|SCC_E_INVALIDUSER|使用者可能無法登入原始檔控制外掛程式。|  
|SCC_E_UNKNOWNPROJECT|專案不知道原始檔控制外掛程式。|  
|SCC_E_INVALIDFILEPATH|無效或無法使用的檔案路徑。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_PROJSYNTAXERR|無效的專案的語法。|  
|SCC_E_CONNECTIONFAILURE|存放區連接問題。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 此函式會傳回成功或失敗的程式碼，和如果成功，會填滿變數`lpParentProjPath`指定專案的完整的專案路徑。  
  
 此函式會傳回父系的現有專案的專案路徑。 根專案中，此函數會傳回傳入的專案路徑 （也就是相同根專案路徑）。 請注意，專案路徑只對原始檔控制外掛程式有意義的字串。  
  
 IDE 已準備好要接受變更`lpUser`和`lpAuxProjPath`參數一併。 IDE 會保存這些字串，並將其傳遞給[SccOpenProject](../extensibility/sccopenproject-function.md)當使用者開啟此專案在未來。 這些字串，因此，提供一種原始檔控制外掛程式，以便在需要與專案產生關聯的追蹤資訊。  
  
 此函式是類似於[SccGetProjPath](../extensibility/sccgetprojpath-function.md)，不同之處在於它不會提示使用者選取的專案。 它也永遠不會會建立新的專案，但只能搭配現有的專案。  
  
 當`SccGetParentProjectPath`呼叫時，`lpProjPath`和`lpAuxProjPath`不能空白，而且會對應到有效的專案。 這些字串通常會接收由先前呼叫從 IDE`SccGetProjPath`函式。  
  
 `lpUser`引數是使用者名稱。 IDE 會在相同的使用者名稱，它已從先前接收傳遞`SccGetProjPath`函式和原始檔控制外掛程式應該使用名稱做為預設值。 如果使用者已經有使用外掛程式的開啟連線，然後外掛程式應該嘗試排除任何提示，以確定函式以無訊息模式運作。 不過，如果登入失敗時，外掛程式應提示使用者登入，當它收到有效登入名稱回復的階段`lpUser`。 因為外掛程式可能會變更這個字串，IDE 一律會配置大小的緩衝區 (`SCC_USER_LEN`+ 1)。 如果字串已變更，新的字串必須是有效的登入名稱 （至少為有效舊的字串形式）。  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject 和 SccGetParentProjectPath 技術注意事項  
 已簡化方案和專案加入原始檔控制在 Visual Studio 中的次數，系統會提示使用者選取原始檔控制系統中的位置數目降至最低。 如果原始檔控制外掛程式支援這兩個新的函式，這些變更會啟動 Visual Studio [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)和`SccGetParentProjectPath`函式。 不過，下列的登錄項目可以用於停用這些變更並還原成之前的 Visual Studio (原始檔控制外掛程式 API 版本 1.1) 行為：  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]「 DoNotCreateSolutionRootFolderInSourceControl"= dword: 00000001  
  
 如果這個登錄項目不存在，或設為 dword: 00000000，Visual Studio 會嘗試使用新的函式，`SccCreateSubProject`和`SccGetParentProjectPath`。  
  
 如果登錄項目設為 dword: 00000001，Visual Studio 不會嘗試使用這些新的函式，並加入原始檔控制中的這些操作可在舊版的 Visual Studio 中所顯示的一樣。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)