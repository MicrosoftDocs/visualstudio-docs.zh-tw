---
title: "SccCreateSubProject 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 97993833d08479fbf518fb5b4852f46cc34f9bc3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject 函式
這個函式具有指定名稱所指定的現有父專案下建立子專案`lpParentProjPath`引數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 lpUser  
 [in、 out]（最多 SCC_USER_SIZE，包括 NULL 結束字元) 使用者名稱。  
  
 lpParentProjPath  
 [in]識別父專案 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 的路徑的字串。  
  
 lpSubProjName  
 [in]建議的子專案名稱 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元)。  
  
 lpAuxProjPath  
 [in、 out]識別 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 專案的輔助字串。  
  
 lpSubProjPath  
 [in、 out]識別 （最多 SCC_PRJPATH_SIZE，包括 NULL 結束字元) 的子專案的路徑輸出字串。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功建立子專案。|  
|SCC_E_INITIALIZEFAILED|無法初始化父專案。|  
|SCC_E_INVALIDUSER|使用者可能無法登入原始檔控制系統。|  
|SCC_E_COULDNOTCREATEPROJECT|無法建立子專案。|  
|SCC_E_PROJSYNTAXERR|無效的專案的語法。|  
|SCC_E_UNKNOWNPROJECT|父專案不知道原始檔控制外掛程式。|  
|SCC_E_INVALIDFILEPATH|無效或無法使用的檔案路徑。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_CONNECTIONFAILURE|時發生原始檔控制外掛程式的連線問題。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 如果子專案名稱已經存在，此函式可以變更預設名稱來建立唯一的例外，例如藉由加入"_\<數字 >"給它。 呼叫端必須準備好接受變更`lpUser`， `lpSubProjPath`，和`lpAuxProjPath`。 `lpSubProjPath`和`lpAuxProjPath`然後呼叫中使用引數[SccOpenProject](../extensibility/sccopenproject-function.md)。 不應該由傳回時呼叫端修改它們。 這些字串會提供方法的原始檔控制外掛程式，以便追蹤與專案產生關聯所需的資訊。 呼叫端 IDE 不會顯示傳回時，這兩個參數，因為外掛程式可以使用可能不適合檢視的格式化的字串。 函數會傳回成功或失敗的程式碼，而且如果成功，會填滿變數`lpSubProjPath`新專案的完整的專案路徑。  
  
 此函式是類似於[SccGetProjPath](../extensibility/sccgetprojpath-function.md)，不同之處在於它以無訊息模式會建立專案，而不會提示使用者選取其中一個。 當`SccCreateSubProject`函式呼叫時，`lpParentProjName`和`lpAuxProjPath`不能空白，而且會對應到有效的專案。 這些字串通常會接收由先前呼叫從 IDE`SccGetProjPath`函式或[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)。  
  
 `lpUser`引數是使用者名稱。 IDE 會在相同的使用者名稱，它已從先前接收傳遞`SccGetProjPath`，和原始檔控制外掛程式應該作為預設值的名稱。 如果使用者已經有使用外掛程式的開啟連線，然後外掛程式應該嘗試排除任何提示，以確定函式以無訊息模式運作。 不過，如果登入失敗時，外掛程式應提示使用者登入，當它收到有效登入名稱回復的階段`lpUser`。 因為外掛程式可能會變更這個字串，IDE 一律配置的緩衝區大小 （SCC_USER_LEN + 1 或 SCC_USER_SIZE，其中包括 null 結束字元的空間）。 如果字串已變更，新的字串必須是有效的登入名稱 （至少為有效舊的字串形式）。  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject 和 SccGetParentProjectPath 技術注意事項  
 已簡化方案和專案加入原始檔控制在 Visual Studio 中的次數，系統會提示使用者選取原始檔控制系統中的位置數目降至最低。 如果原始檔控制外掛程式支援這兩個新的函式，這些變更會啟動 Visual Studio`SccCreateSubProject`和`SccGetParentProjectPath`。 不過，下列的登錄項目可以用於停用這些變更並還原為先前的 Visual Studio (原始檔控制外掛程式 API 版本 1.1) 行為：  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]「 DoNotCreateSolutionRootFolderInSourceControl"= dword: 00000001  
  
 如果這個登錄項目不存在，或設為 dword: 00000000，Visual Studio 會嘗試使用新的函式，`SccCreateSubProject`和`SccGetParentProjectPath`。  
  
 如果登錄項目設為 dword: 00000001，Visual Studio 不會嘗試使用這些新的函式，並加入原始檔控制中的這些操作可在舊版的 Visual Studio 中所顯示的一樣。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)