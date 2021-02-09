---
title: 建立解決方案的父容器檔案夾 |Microsoft Docs
description: 瞭解如何使用原始檔控制外掛程式 API 版本1.2，為方案中的所有 Web 專案指定單一根原始檔控制目的地。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 39e61e3566f848e23fdea7b4fb4d0ea5bc181370
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903146"
---
# <a name="create-parent-container-folders-for-solutions"></a>建立解決方案的父容器檔案夾
在原始檔控制外掛程式 API 版本1.2 中，使用者可以針對方案內的所有 Web 專案指定單一根原始檔控制目的地。 這個單一根目錄稱為 (SUR) 的超級統一根。

 在原始檔控制外掛程式 API 版本1.1 中，如果使用者將 multiproject 方案加入至原始檔控制，則會提示使用者為每個 Web 專案指定一個原始檔控制目的地。

## <a name="new-capability-flags"></a>新功能旗標
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>新的函式
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 將 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 方案加入至原始檔控制時，IDE 幾乎一律會建立 SUR 資料夾。 具體而言，它會在下列情況下執行：

- 專案是檔案共用 Web 專案。

- 專案和方案檔有不同的磁片磁碟機。

- 專案和方案檔有不同的共用。

- 在原始檔控制的方案) 中，個別 (新增專案。

在中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，建議 SUR 資料夾的名稱與沒有副檔名的解決方案名稱相同。 下表摘要說明這兩個版本中的行為。

|功能|原始檔控制外掛程式 API 版本1。1|原始檔控制外掛程式 API 版本1。2|
|-------------| - | - |
|將解決方案新增至 SCC|SccInitialize ( # A1<br /><br /> SccGetProjPath ( # A1<br /><br /> SccGetProjPath ( # A1<br /><br /> SccOpenProject ( # A1|SccInitialize ( # A1<br /><br /> SccGetProjPath ( # A1<br /><br /> SccCreateSubProject ( # A1<br /><br /> SccCreateSubProject ( # A1<br /><br /> SccOpenProject ( # A1|
|將專案加入至原始檔控制的解決方案|SccGetProjPath ( # A1<br /><br /> File.openproject ( # A1|SccGetParentProjectPath ( # A1<br /><br /> SccOpenProject ( # A1<br /><br />  **注意：**  Visual Studio 假設方案是 SUR 的直接子系。|

## <a name="examples"></a>範例
 下表列出兩個範例。 在這兩種情況下， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 系統會提示使用者在原始檔控制之下輸入方案的目的地位置，直到將  *user_choice* 指定為目的地。 當指定 user_choice 時，會加入方案和兩個專案，而不提示使用者輸入原始檔控制目的地。

|解決方案包含|磁片位置|資料庫預設結構|
|-----------------------|-----------------------|--------------------------------|
|*sln1 .sln*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot $ \Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/Web2|
|*sln1 .sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 無論作業是否因為錯誤而取消或失敗，都會建立 SUR 資料夾和子資料夾。 它們不會在取消或錯誤狀況中自動移除。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 如果原始檔控制外掛程式不會傳回 `SCC_CAP_CREATESUBPROJECT` 和 `SCC_CAP_GETPARENTPROJECT` 功能旗標，則預設為1.1 版的行為。 此外，使用者 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可以藉由將下列機碼的值設定為 *dword： 00000001*，來選擇還原為1.1 版的行為：

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl**  = *dword： 00000001*

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 版本1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
