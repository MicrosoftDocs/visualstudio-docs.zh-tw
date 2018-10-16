---
title: 獨立模式 Shell 進入點參數 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f19165a5941f62fd5594a715c8812c065b371608
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247684"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Isolated 的 Shell 進入點參數 （c + +）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio shell 為基礎的應用程式啟動時，它會呼叫 Visual Studio shell 的啟動進入點。 下列設定可以覆寫的殼層啟動進入點的呼叫中。 如需每個設定的說明，請參閱[。Pkgdef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)。  
  
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
  
 Visual Studio Shell 獨立模式的範本會建立原始程式檔中， *solutionName*.cpp，其中*solutionName*是應用程式的方案名稱。 此檔案定義應用程式，_tWinMain 函式的主要進入點。 此函式會叫用 shell 的啟動進入點。  
  
 您可以藉由變更這些設定，應用程式啟動時變更應用程式的行為。  
  
## <a name="parameters"></a>參數  
 Visual Studio shell 的啟動進入點會定義五個參數。 不會變更的前四個參數。 第五個參數會設定覆寫清單。 殼層的啟動進入點是從應用程式的主要進入點呼叫。  
  
 殼層的起點項目具有下列簽章。  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 如果您不想要覆寫任何應用程式設定，請將保留設定的值覆寫參數為 null 指標。  
  
 若要覆寫一個或多個設定，請傳遞 Unicode 字串，包含要覆寫的設定。 字串是名稱 / 值組的分號分隔清單。 每一組包含要覆寫設定的名稱，後面接著等號 （=），後面接著要套用設定的值。  
  
> [!NOTE]
>  Unicode 字串中不包含空白字元。  
  
 如需布林值的設定，下列字串代表 true 值;所有其他字串代表 false 值。 這些字串是不區分大小寫。  
  
-   \+  
  
-   1  
  
-   -1  
  
-   於  
  
-   true  
  
-   是  
  
## <a name="example"></a>範例  
 若要停用增益集，並變更您的應用程式的預設專案位置，您可以設定 「 AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp 」 的最後一個參數。  
  
## <a name="see-also"></a>另請參閱  
 [自訂 Isolated 的 Shell](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgdef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)

