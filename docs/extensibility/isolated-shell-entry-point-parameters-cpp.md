---
redirect_url: shell/isolated-shell-entry-point-parameters-cpp
title: "隔離 Shell 進入點參數 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f5392188a75b474528df92be0c835b5c60dc2891
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Isolated 的 Shell 進入點參數 （c + +）
Visual Studio shell 為基礎的應用程式啟動時，它會呼叫在 Visual Studio shell 項目起點。 下列設定會覆寫的殼層的開始項目點的呼叫中。 如需每個設定的說明，請參閱[。Pkgdef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)。  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   應用程式名稱  
  
-   CommandLineLogo  
  
-   DefaultHomePage  
  
-   DefaultProjectsLocation  
  
-   DefaultSearchPage  
  
-   DefaultUserFilesFolderRoot  
  
-   DisableOutputWindow  
  
-   HideMiscellaneousFilesByDefault  
  
-   HideSolutionConcept  
  
-   NewProjDlgInstalledTemplatesHdr  
  
-   NewProjDlgSlnTreeNodeTitle  
  
-   SolutionFileCreatorIdentifier  
  
-   SolutionFileExt  
  
-   UserFilesSubFolderName  
  
-   UserOptsFileExt  
  
 Visual Studio Shell 外掛式主控的範本會建立原始程式檔*solutionName*.cpp 其中*solutionName*是應用程式的方案名稱。 此檔案會定義應用程式，_tWinMain 函式的主要進入點。 此函式會叫用的殼層啟動進入點。  
  
 您可以藉由變更這些設定，應用程式啟動時變更應用程式的行為。  
  
## <a name="parameters"></a>參數  
 Visual Studio shell 項目起點定義五個參數。 請勿變更前四個參數。 第五個參數會設定覆寫清單。 殼層的開始進入點會從應用程式的主要進入點呼叫。  
  
 殼層的起點項目具有下列簽章。  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 如果您不想要覆寫任何應用程式設定，請將保留的設定值會覆寫參數為 null 指標。  
  
 若要覆寫一個或多個值，傳遞 Unicode 字串，其中包含覆寫設定。 字串為名稱 / 值組的分號分隔清單。 每個配對包含選定欲覆寫設定的名稱，後面接著等號 （=），後面接著要套用設定的值。  
  
> [!NOTE]
>  不要在 Unicode 字串中包含空白。  
  
 布林值的設定，下列字串代表在值為 true。所有其他字串代表其值為 false。 這些字串不區分大小寫。  
  
-   \+  
  
-   1  
  
-   -1  
  
-   於  
  
-   true  
  
-   是  
  
## <a name="example"></a>範例  
 若要停用增益集，並變更您的應用程式的預設專案位置，您可以設定 「 AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp 」 的最後一個參數。  
  
## <a name="see-also"></a>請參閱  
 [自訂 Isolated 的 Shell](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgdef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)