---
title: "SccCreateSubProject 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCreateSubProject"
helpviewer_keywords: 
  - "SccCreateSubProject 函式"
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# SccCreateSubProject 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式具有指定名稱所指定的現有父專案下建立子專案 `lpParentProjPath` 引數。  
  
## 語法  
  
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
  
#### 參數  
 pContext  
 \[\] in原始檔控制外掛程式的內容指標。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 lpUser  
 \[in、 out\]\(最多 SCC\_USER\_SIZE，包括 NULL 結束字元\) 使用者名稱。  
  
 lpParentProjPath  
 \[\] in識別父專案 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 結束字元\) 路徑的字串。  
  
 lpSubProjName  
 \[\] in建議的子專案名稱 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 結束字元\)。  
  
 lpAuxProjPath  
 \[in、 out\]識別 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 結束字元\) 專案輔助的字串。  
  
 lpSubProjPath  
 \[in、 out\]識別的路徑 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 結束字元\) 的子專案的輸出字串。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|已成功建立子專案。|  
|SCC\_E\_INITIALIZEFAILED|無法初始化父專案。|  
|SCC\_E\_INVALIDUSER|使用者可能無法登入原始檔控制系統。|  
|SCC\_E\_COULDNOTCREATEPROJECT|無法建立子專案。|  
|SCC\_E\_PROJSYNTAXERR|無效的專案的語法。|  
|SCC\_E\_UNKNOWNPROJECT|父專案不知道原始檔控制外掛程式。|  
|SCC\_E\_INVALIDFILEPATH|無效或無法使用的檔案路徑。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC\_E\_CONNECTIONFAILURE|發生原始檔控制外掛程式的連線問題。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|非特定的失敗。|  
  
## 備註  
 如果子專案名稱已經存在，可以變更預設名稱，建立唯一的例外，例如藉由加入"\< 編號 \> \_"。 呼叫者必須準備好接受變更 `lpUser`, ，`lpSubProjPath`, ，和 `lpAuxProjPath`。`lpSubProjPath` 和`lpAuxProjPath` 引數則用於呼叫 [SccOpenProject](../extensibility/sccopenproject-function.md)。 不應該被呼叫傳回時修改它們。 這些字串會提供方法的原始檔控制外掛程式，以追蹤需要與專案相關聯的資訊。 呼叫端 IDE 不會顯示傳回時，這兩個參數，因為外掛程式可以使用可能不適合檢視的格式化的字串。 函數會傳回成功或失敗的程式碼，而且如果成功，會填滿變數 `lpSubProjPath` 新專案的完整的專案路徑。  
  
 此函式是類似於 [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ，只不過它以無訊息模式會建立專案，而不會提示使用者選取其中一個。 當 `SccCreateSubProject` 函式呼叫時， `lpParentProjName` 和 `lpAuxProjPath` 不可為空白，將會對應到有效的專案。 這些字串通常會收到由先前呼叫從 IDE `SccGetProjPath` 函式或 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)。  
  
 `lpUser` 引數是使用者名稱。 IDE 會傳遞先前已從收到的相同使用者名稱 `SccGetProjPath`, ，和原始檔控制外掛程式應該使用名稱做為預設值。 如果使用者已使用外掛程式的開啟連線，然後外掛程式應該嘗試排除任何提示，確定函式會以無訊息模式運作。 不過，如果登入失敗時，外掛程式應該會提示使用者登入，並收到有效的登入名稱回復的階段 `lpUser`。 因為外掛程式可能會變更這個字串，IDE 一律會配置的緩衝區大小 \(SCC\_USER\_LEN \+ 1 或 SCC\_USER\_SIZE，其中包括 null 結束字元的空間\)。 如果變更字串時，新的字串必須是有效的登入名稱 \(至少為有效舊字串形式\)。  
  
## SccCreateSubProject 和 SccGetParentProjectPath 技術提示  
 方案和專案加入原始檔控制已簡化，在 Visual Studio 中的系統會提示使用者在原始檔控制系統中選取位置的次數降到最低。 如果原始檔控制外掛程式支援這兩個新的函式，這些變更會啟用 Visual Studio `SccCreateSubProject` 和 `SccGetParentProjectPath`。 不過，下列的登錄項目可以用於停用這些變更並還原為先前的 Visual Studio \(原始檔控制外掛程式 API 版本 1.1\) 行為:  
  
 \[\] HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl"DoNotCreateSolutionRootFolderInSourceControl"\= dword: 00000001  
  
 如果此登錄項目不存在，或設為 dword:00000000，Visual Studio 會嘗試使用新的函式， `SccCreateSubProject` 和 `SccGetParentProjectPath`。  
  
 登錄項目設定為 dword: 00000001 表示，如果 Visual Studio 不會嘗試使用這些新的函式，並在舊版的 Visual Studio 中所顯示的一樣運作的作業加入至原始檔控制。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)