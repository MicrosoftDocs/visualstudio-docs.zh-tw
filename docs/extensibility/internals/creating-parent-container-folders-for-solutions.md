---
title: "為方案建立的父容器資料夾 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b2aa63a0c55ad196edf6c209475a816c0c3c027c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-parent-container-folders-for-solutions"></a>建立方案的父容器的資料夾
在原始檔控制外掛程式 API 1.2 版，使用者可以指定針對方案中的所有 Web 專案的單一根來源控制目的地。 此單一根稱為超級統一的根 （南下）。  
  
 在 原始檔控制外掛程式 API 1.1 版，如果使用者將多專案方案加入原始檔控制已提示使用者指定每個 Web 專案的一個原始檔控制目的地。  
  
## <a name="new-capability-flags"></a>新的功能旗標  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>新的函式  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 幾乎一律會南下資料夾建立時將方案加入原始檔控制。 具體來說，它是在下列情況：  
  
-   專案是 Web 專案的檔案共用。  
  
-   有不同的磁碟機，專案和方案檔。  
  
-   有不同的共用專案和方案檔。  
  
-   專案已加入分開 （在原始檔控制的解決方案）。  
  
 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]建議南下資料夾的名稱是不含副檔名的方案名稱相同。 下表摘要說明兩種版本的行為。  
  
|功能|tSource 控制項外掛程式 API 版本 1.1|原始檔控制外掛程式 API 1.2 版|  
|-------------|----------------------------------------------|---------------------------------------------|  
|將方案加入至 SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|將專案加入原始檔控制方案|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()**附註：** Visual Studio 會假設解決方案的直接子系 SUR.|  
  
## <a name="examples"></a>範例  
 下表列出兩個範例。 在這兩種情況下，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]會提示使用者輸入之前的原始檔控制下的方案的目的地位置*user_choice*指定做為目的地。指定 user_choice 時，會加入解決方案和兩個專案而不提示使用者輸入原始檔控制項目的。  
  
|方案包含|在磁碟位置|資料庫預設的結構|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /D/web1<br /><br /> $/*user_choice*  /sln1/win1|  
  
 南下資料夾和子資料夾會建立不論作業已取消或因錯誤而失敗。 它們不會自動移除在取消或錯誤的情況。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]預設為 1.1 版的行為，如果原始檔控制外掛程式不會傳回`SCC_CAP_CREATESUBPROJECT`和`SCC_CAP_GETPARENTPROJECT`功能旗標。 此外，使用者的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以選擇要還原的下列索引鍵的值設為 dword: 00000001 1.1 版的行為：  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]「 DoNotCreateSolutionRootFolderInSourceControl"= dword: 00000001  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)