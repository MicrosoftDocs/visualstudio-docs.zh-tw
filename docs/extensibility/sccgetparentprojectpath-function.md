---
title: SccGetParentProjectPath 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f4234ac20f9c583d944ba6fdf8e52a6eb0db156
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639678"
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
  
### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容指標。  
  
 hWnd  
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 lpUser  
 [in、 out]使用者名稱 （最多 SCC_USER_SIZE，包括 NULL 結束字元)。  
  
 lpProjPath  
 [in]識別 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 的專案路徑的字串。  
  
 lpAuxProjPath  
 [in、 out]輔助的字串，識別 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 專案。  
  
 lpParentProjPath  
 [in、 out]識別父專案路徑 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 的輸出字串。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功取得父專案路徑。|  
|SCC_E_INITIALIZEFAILED|無法初始化專案。|  
|SCC_E_INVALIDUSER|使用者可能無法登入原始檔控制外掛程式。|  
|SCC_E_UNKNOWNPROJECT|專案不知道原始檔控制外掛程式。|  
|SCC_E_INVALIDFILEPATH|無效或無法使用的檔案路徑。|  
|SCC_E_NOTAUTHORIZED|若要執行這項作業不允許的使用者。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_PROJSYNTAXERR|無效的專案的語法。|  
|SCC_E_CONNECTIONFAILURE|存放區連接問題。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 這個函式會傳回成功或失敗的程式碼，或如果成功，會填滿變數`lpParentProjPath`指定專案的完整的專案路徑。  
  
 此函式會傳回父系的現有專案的專案路徑。 根專案，此函數會傳回傳入的專案路徑 （也就是相同的根專案路徑）。 請注意，專案路徑只對原始檔控制外掛程式有意義的字串。  
  
 IDE 已準備好要接受變更`lpUser`和`lpAuxProjPath`參數。 IDE 會保存這些字串，並將其傳遞給[SccOpenProject](../extensibility/sccopenproject-function.md)當使用者開啟此專案在未來。 因此，這些字串，就是提供方法的原始檔控制外掛程式，以便在需要與專案產生關聯的追蹤資訊。  
  
 此函數很相似[SccGetProjPath](../extensibility/sccgetprojpath-function.md)，不同之處在於它不會提示使用者選取的專案。 也永遠不會只與現有專案建立新的專案，但運作方式。  
  
 當`SccGetParentProjectPath`呼叫時，`lpProjPath`和`lpAuxProjPath`將為空白，且將會對應到有效的專案。 這些字串通常會收到由先前呼叫從 IDE`SccGetProjPath`函式。  
  
 `lpUser`引數是使用者名稱。 IDE 會在相同的使用者名稱，它必須從先前接收傳遞`SccGetProjPath`函式和原始檔控制外掛程式應該使用名稱做為預設值。 如果使用者已經有使用外掛程式的開啟連線，然後外掛程式應該嘗試排除任何提示，以確定函式會以無訊息模式運作。 不過，如果登入失敗時，外掛程式應該會提示使用者登入，當它收到有效的登入，傳遞回名稱`lpUser`。 因為外掛程式可能會變更此字串，IDE 一律會配置大小的緩衝區 (`SCC_USER_LEN`+ 1)。 如果字串變更時，新的字串必須是有效的登入名稱 （至少為有效舊字串形式）。  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject 和 SccGetParentProjectPath 的技術提示  
 已簡化方案和專案加入原始檔控制在 Visual Studio 中的系統會提示使用者在原始檔控制系統中選取位置的次數降到最低。 如果原始檔控制外掛程式支援這兩個新函數，這些變更會啟動 Visual Studio [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)而`SccGetParentProjectPath`函式。 不過，下列的登錄項目可用來停用這些變更並還原成先前的 Visual Studio (原始檔控制外掛程式 API 版本 1.1) 行為：  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]「 DoNotCreateSolutionRootFolderInSourceControl"= dword: 00000001**  
  
 如果此登錄項目不存在，或設為 dword:00000000，Visual Studio 會嘗試使用新的函式`SccCreateSubProject`和`SccGetParentProjectPath`。  
  
 如果登錄項目設定為 dword: 00000001，Visual Studio 不會嘗試使用這些新的函式，並加入原始檔控制中的運算運作方式如同在舊版的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)