---
title: " (c + +) 的隔離式 Shell 進入點參數 |Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839165"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>獨立模式 Shell 進入點參數 (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當 Visual Studio shell 型應用程式啟動時，它會呼叫 Visual Studio shell 的開始進入點。 下列設定可以在呼叫 shell 的開始進入點時覆寫。 如需每個設定的說明，請參閱 [。.Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)檔案。  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
- CommandLineLogo  
  
- DefaultHomePage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- HideSolutionConcept  
  
- NewProjDlgInstalledTemplatesHdr  
  
- NewProjDlgSlnTreeNodeTitle  
  
- SolutionFileCreatorIdentifier  
  
- SolutionFileExt  
  
- UserFilesSubFolderName  
  
- UserOptsFileExt  
  
  「Visual Studio Shell 隔離範本 *」會建立*原始程式*檔（solution*. .cpp），其中的解決方法是應用程式的解決方案名稱。 此檔案會定義應用程式的主要進入點，也就是 _tWinMain 函式。 此函式會叫用 shell 的開始進入點。  
  
  您可以在應用程式啟動時變更這些設定，以變更應用程式的行為。  
  
## <a name="parameters"></a>參數  
 Visual Studio shell 的開始進入點會定義五個參數。 請勿變更前四個參數。 第五個參數接受設定覆寫清單。 從應用程式的主要進入點呼叫 shell 的開始進入點。  
  
 Shell 的開始進入點具有下列簽章。  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 如果您不想要覆寫任何應用程式設定，請將 [設定覆寫] 參數的值保留為 null 指標。  
  
 若要覆寫一個或多個設定，請傳遞包含要覆寫之設定的 Unicode 字串。 字串是成對的名稱/值組清單（以分號分隔）。 每一組都包含要覆寫之設定的名稱，後面接著等號 (=) ，後面接著要套用至設定的值。  
  
> [!NOTE]
> 請勿在 Unicode 字串中包含空格。  
  
 若為布林值設定，下列字串代表 true 值。所有其他字串都代表 false 值。 這些字串不區分大小寫。  
  
- \+  
  
- 1  
  
- -1  
  
- on  
  
- true  
  
- 是  
  
## <a name="example"></a>範例  
 若要停用增益集並變更應用程式的預設專案位置，您可以將最後一個參數設定為 "AddinsAllowed = false; DefaultProjectsLocation =%USERPROFILE%\temp"。  
  
## <a name="see-also"></a>另請參閱  
 [自訂獨立模式 Shell](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgdef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
