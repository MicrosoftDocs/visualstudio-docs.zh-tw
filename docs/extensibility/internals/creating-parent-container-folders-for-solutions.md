---
title: 為解決方案建立父容器資料夾 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 531e1cbf3e8489fd68d2bbd94c9a66af3c817a00
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929935"
---
# <a name="create-parent-container-folders-for-solutions"></a>建立父容器之資料夾的解決方案
在原始檔控制外掛程式 API 版本 1.2，使用者可以指定方案中的所有 web 專案的單一根來源控制目的地。 此單一根稱為超級統一的根 (SUR)。  
  
 在 原始檔控制外掛程式 API 版本 1.1 中，如果使用者將多專案的方案加入原始檔控制已提示使用者指定每個 web 專案的一個原始檔控制目的地。  
  
## <a name="new-capability-flags"></a>新的功能旗標  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>新的函式  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 幾乎一律會 SUR 資料夾建立時將方案加入原始檔控制。 具體來說，它會在下列情況：  
  
-   專案是檔案共用的 web 專案。  
  
-   有不同的磁碟機，專案和方案檔。  
  
-   有不同的共用專案和方案檔。  
  
-   專案已加入個別 （在原始檔控制的方案）。  
  

在  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，建議 SUR 資料夾的名稱是不含副檔名的方案名稱相同。 下表摘要說明兩種版本的行為。  
  
|功能|原始檔控制外掛程式 API 版本 1.1|原始檔控制外掛程式 API 版本 1.2|  
|-------------| - | - |  
|將解決方案新增至 SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|將專案加入原始檔控制的方案|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **注意：** Visual Studio 假設解決方案的直接子系 SUR.|  
  
## <a name="examples"></a>範例  
 下表列出兩個範例。 在這兩種情況下，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]會提示使用者輸入之前的原始檔控制方案的目的地位置*user_choice*指定做為目的地。 指定 user_choice 時，會新增解決方案和兩個專案而不提示使用者輸入原始檔控制的目的地。  
  
|方案包含|在 磁碟位置|資料庫預設結構|  
|-----------------------|-----------------------|--------------------------------|  
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/Web2|  
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|  
  
 SUR 資料夾和子資料夾會建立不論作業已取消或因錯誤而失敗。 它們不會自動移除在取消或錯誤的情況。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 預設為 1.1 版的行為，如果原始檔控制外掛程式不會傳回`SCC_CAP_CREATESUBPROJECT`和`SCC_CAP_GETPARENTPROJECT`功能旗標。 此外，使用者[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以選擇藉由設定下列機碼來的值還原為 1.1 版行為*dword: 00000001*:  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 版本 1.2 中最新消息](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)