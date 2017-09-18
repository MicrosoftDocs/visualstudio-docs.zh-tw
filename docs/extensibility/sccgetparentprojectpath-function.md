---
title: "SccGetParentProjectPath 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetParentProjectPath"
helpviewer_keywords: 
  - "SccGetParentProjectPath 函式"
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccGetParentProjectPath 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會指定專案的父專案路徑。 使用者會將 Visual Studio 專案加入至原始檔控制時，會呼叫此函數。  
  
## 語法  
  
```cpp#  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### 參數  
 pContext  
 \[\] in原始檔控制外掛程式的內容指標。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 lpUser  
 \[in、 out\]使用者名稱 \(最多 SCC\_USER\_SIZE，包括 NULL 結束字元\)。  
  
 lpProjPath  
 \[\] in識別 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 結束字元\) 專案路徑的字串。  
  
 lpAuxProjPath  
 \[in、 out\]識別 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 結束字元\) 專案輔助的字串。  
  
 lpParentProjPath  
 \[in、 out\]識別父專案路徑 \(最多 SCC\_PRJPATH\_SIZE，包括 NULL 結束字元\) 的輸出字串。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|成功取得父專案路徑。|  
|SCC\_E\_INITIALIZEFAILED|無法初始化專案。|  
|SCC\_E\_INVALIDUSER|使用者可能無法登入原始檔控制外掛程式。|  
|SCC\_E\_UNKNOWNPROJECT|專案是未知的原始檔控制外掛程式。|  
|SCC\_E\_INVALIDFILEPATH|無效或無法使用的檔案路徑。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC\_E\_PROJSYNTAXERR|無效的專案的語法。|  
|SCC\_E\_CONNECTIONFAILURE|存放區連接問題。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|非特定的失敗。|  
  
## 備註  
 此函數會傳回成功或失敗的程式碼，而且如果成功，會填滿變數 `lpParentProjPath` 指定專案的完整的專案路徑。  
  
 此函式會傳回現有專案的專案路徑的父系。 根專案中，函數會傳回傳入的專案路徑 \(也就是相同根專案路徑\)。 請注意，專案路徑只對原始檔控制外掛程式有意義的字串。  
  
 IDE 已準備好要接受變更 `lpUser` 和 `lpAuxProjPath` 參數。 IDE 會保存這些字串，並將其傳遞給 [SccOpenProject](../extensibility/sccopenproject-function.md) 當使用者開啟此專案在未來。 因此，這些字串，就是提供方法的原始檔控制外掛程式，以便在需要與專案相關聯的追蹤資訊。  
  
 此函式是類似於 [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ，但不會提示使用者選取的專案。 也不會只與現有專案建立新的專案，但運作。  
  
 當 `SccGetParentProjectPath` 呼叫時， `lpProjPath` 和 `lpAuxProjPath` 不可為空白，將會對應到有效的專案。 這些字串通常會收到由先前呼叫從 IDE `SccGetProjPath` 函式。  
  
 `lpUser` 引數是使用者名稱。 IDE 會傳遞先前已從收到的相同使用者名稱 `SccGetProjPath` 函式和原始檔控制外掛程式應該使用名稱做為預設值。 如果使用者已使用外掛程式的開啟連線，然後外掛程式應該嘗試排除任何提示，確定函式會以無訊息模式運作。 不過，如果登入失敗時，外掛程式應該會提示使用者登入，並收到有效的登入名稱回復的階段 `lpUser`。 因為外掛程式可能會變更這個字串，IDE 一律會配置大小的緩衝區 \(`SCC_USER_LEN`\+ 1\)。 如果變更字串時，新的字串必須是有效的登入名稱 \(至少為有效舊字串形式\)。  
  
## SccCreateSubProject 和 SccGetParentProjectPath 技術提示  
 方案和專案加入原始檔控制已簡化，在 Visual Studio 中的系統會提示使用者在原始檔控制系統中選取位置的次數降到最低。 如果原始檔控制外掛程式支援這兩個新的函式，這些變更會啟用 Visual Studio [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) 和 `SccGetParentProjectPath` 函式。 不過，下列的登錄項目可以用於停用這些變更並還原成之前的 Visual Studio \(原始檔控制外掛程式 API 版本 1.1\) 行為:  
  
 \[\] HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl"DoNotCreateSolutionRootFolderInSourceControl"\= dword: 00000001  
  
 如果此登錄項目不存在，或設為 dword:00000000，Visual Studio 會嘗試使用新的函式， `SccCreateSubProject`和`SccGetParentProjectPath`。  
  
 登錄項目設定為 dword: 00000001 表示，如果 Visual Studio 不會嘗試使用這些新的函式，並在舊版的 Visual Studio 中所顯示的一樣運作的作業加入至原始檔控制。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)