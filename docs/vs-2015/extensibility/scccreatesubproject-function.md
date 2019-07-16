---
title: SccCreateSubProject 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c2f28d8bb9ebc440db69085324becb6a96c19afe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200188"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

這個函式具有指定之名稱所指定的現有父專案底下建立子專案`lpParentProjPath`引數。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容指標。  
  
 hWnd  
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 lpUser  
 [in、 out]（最多 SCC_USER_SIZE，包括 NULL 結束字元) 使用者名稱。  
  
 lpParentProjPath  
 [in]識別父專案 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 的路徑的字串。  
  
 lpSubProjName  
 [in]建議的子專案名稱 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元)。  
  
 lpAuxProjPath  
 [in、 out]輔助的字串，識別 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 專案。  
  
 lpSubProjPath  
 [in、 out]識別的路徑 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 的子專案的輸出字串。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功建立子專案。|  
|SCC_E_INITIALIZEFAILED|無法初始化父專案。|  
|SCC_E_INVALIDUSER|使用者可能無法登入原始檔控制系統。|  
|SCC_E_COULDNOTCREATEPROJECT|無法建立子專案。|  
|SCC_E_PROJSYNTAXERR|無效的專案的語法。|  
|SCC_E_UNKNOWNPROJECT|父專案是未知的原始檔控制外掛程式。|  
|SCC_E_INVALIDFILEPATH|無效或無法使用的檔案路徑。|  
|SCC_E_NOTAUTHORIZED|若要執行這項作業不允許的使用者。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_CONNECTIONFAILURE|沒有原始檔控制外掛程式的連線問題。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 如果子專案名稱已經存在，函式可以變更預設名稱來建立唯一的帳戶，例如藉由加入 「 _\<數字 > 」 給它。 呼叫端必須準備好接受變更`lpUser`， `lpSubProjPath`，和`lpAuxProjPath`。 `lpSubProjPath`並`lpAuxProjPath`引數會用於呼叫[SccOpenProject](../extensibility/sccopenproject-function.md)。 它們不應該修改時傳回呼叫端。 這些字串會提供方法的原始檔控制外掛程式，以追蹤需要與專案產生關聯的資訊。 呼叫端的 IDE 不會顯示傳回時，這兩個參數，因為外掛程式可以使用可能不適合檢視的格式化的字串。 函式會傳回成功或失敗的程式碼，以及如果成功，會填滿變數`lpSubProjPath`新專案的完整的專案路徑。  
  
 此函數很相似[SccGetProjPath](../extensibility/sccgetprojpath-function.md)，只不過它以無訊息方式建立專案，而不是提示使用者選取其中一個。 當`SccCreateSubProject`函式呼叫時，`lpParentProjName`和`lpAuxProjPath`將為空白，且將會對應到有效的專案。 這些字串通常會收到由先前呼叫從 IDE`SccGetProjPath`函式或[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)。  
  
 `lpUser`引數是使用者名稱。 IDE 會在相同的使用者名稱，它必須從先前接收傳遞`SccGetProjPath`，和原始檔控制外掛程式應該做為預設值的名稱。 如果使用者已經有使用外掛程式的開啟連線，然後外掛程式應該嘗試排除任何提示，以確定函式會以無訊息模式運作。 不過，如果登入失敗時，外掛程式應該會提示使用者登入，當它收到有效的登入，傳遞回名稱`lpUser`。 因為外掛程式可能會變更此字串，IDE 一律會配置的緩衝區大小 （SCC_USER_LEN + 1 或 SCC_USER_SIZE，其中包括 null 結束字元的空間）。 如果字串變更時，新的字串必須是有效的登入名稱 （至少為有效舊字串形式）。  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject 和 SccGetParentProjectPath 的技術提示  
 已簡化方案和專案加入原始檔控制在 Visual Studio 中的系統會提示使用者在原始檔控制系統中選取位置的次數降到最低。 如果原始檔控制外掛程式支援這兩個新函數，這些變更會啟動 Visual Studio`SccCreateSubProject`和`SccGetParentProjectPath`。 不過，下列的登錄項目可用來停用這些變更並還原成先前的 Visual Studio (原始檔控制外掛程式 API 版本 1.1) 行為：  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]「 DoNotCreateSolutionRootFolderInSourceControl"= dword: 00000001  
  
 如果此登錄項目不存在，或設為 dword:00000000，Visual Studio 會嘗試使用新的函式`SccCreateSubProject`和`SccGetParentProjectPath`。  
  
 如果登錄項目設定為 dword: 00000001，Visual Studio 不會嘗試使用這些新的函式，並加入原始檔控制中的運算運作方式如同在舊版的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
