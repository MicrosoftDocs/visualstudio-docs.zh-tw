---
title: SharePoint 所支援的 MSBuild 屬性 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1e60843119ee72f1164288f50b27116cdda31e9b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint 支援的 MSBuild 屬性
  任何[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]Microsoft.VisualStudio.SharePoint.targets 檔案、 專案檔或專案使用者檔案中定義的屬性可用於[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 專案。 除了一般[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]專案中，SharePoint 所提供的屬性定義的 SharePoint 專案特定的額外屬性。  
  
 如需常見的清單[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]屬性，請參閱[一般 MSBuild 專案屬性](http://go.microsoft.com/fwlink/?LinkID=168687)。 針對您的程式語言所支援之屬性的完整清單，查看.targets 檔案、 專案檔 （.csproj 或.vbproj） 或專案使用者檔案 (副檔名為.csproj.user 或.vbproj.user)。  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>MSBuild 屬性特有的 SharePoint  
 下表列出[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]特別適用於 SharePoint 專案中的屬性[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 其他屬性，但它們僅供內部使用。  
  
|屬性名稱|描述|  
|-------------------|-----------------|  
|SharePointSiteUrl|字串，代表[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]至 SharePoint 網站。|  
|SandboxedSolution|布林值，指出是否方案為沙箱化方案。|  
|ActiveDeploymentConfiguration|現用部署組態。|  
|IncludeAssemblyInPackage|布林值，指出是否要將組件包含在封裝檔案中。|  
|PreDeploymentCommand|字串值，表示要預先部署命令步驟中執行的命令。|  
|PostDeploymentCommand|字串值，表示要在部署後命令步驟中執行的命令。|  
|CustomBeforeSharePointTargets|字串，表示路徑[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]目標檔案。 如果目標檔案存在且已定義，它會匯入 SharePoint 為目標的任何資料之前。 這個屬性可讓您依預先定義與封裝相關的屬性自訂封裝程序，而不需修改隨附的 SharePoint 目標檔，但目標檔案仍適用於所有 SharePoint 專案。|  
|CustomAfterSharePointTargets|字串，表示路徑[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]目標檔案。 如果目標檔案存在，且定義中，則已匯入在所有的 SharePoint 為目標資料。 這個屬性可讓您藉由覆寫封裝相關的屬性和目標，而不需要修改隨附的 SharePoint 目標檔，自訂封裝程序，但目標檔案仍適用於所有 SharePoint 專案。|  
|LayoutPath|字串，表示要將其封裝之檔案的每個暫時放置會新增至.wsp 檔案的根目錄。 這個路徑可以是很有幫助您覆寫 BeforeLayout 和 AfterLayout 目標，以新增、 移除或修改檔案以進行封裝，因為您可以用它來修改.wsp 檔案的內容時。|  
|BasePackagePath|字串，代表用來放置封裝的資料夾。 這個值會使用專案中，例如 Bin\Debug 的輸出目錄。|  
|PackageExtension|字串，代表要附加至封裝檔案的副檔名。 預設值是用於根據 wsp。|  
|AssemblyDeploymentTarget|字串，代表專案的組件在 SharePoint 伺服器的部署所在的位置。 其值為 GlobalAssemblyCache （預設值） 或 WebApplication。 這個屬性也可以設定在 [屬性] 視窗中。|  
|PackageWithValidation|布林值，指定是否要將驗證執行封裝之前。 這個屬性可讓您建立封裝時忽略驗證錯誤。|  
|ValidatePackageDependsOn|字串，定義要 ValidatePackage 目標之前執行的其他目標。|  
|TokenReplacementFileExensions|字串，定義在封裝期間被取代的語彙基元的檔案。|  
  
## <a name="using-msbuild-properties-in-the-properties-page"></a>在 [屬性] 頁面中使用 MSBuild 屬性  
 取得彈性，而非使用中的硬式編碼字串**預先部署命令列**和**部署後命令列**方塊在 SharePoint 內容 頁面中，您可以使用 SharePoint做為引數的屬性。 例如，而不要指定特定[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]字串在 SharePoint 網站，您可以改為使用`$(SharePointSiteUrl)`。  
  
> [!NOTE]  
>  您可以使用[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]變數語法`$(` *propertyName* `)`或環境變數語法`%` *propertyName* `%`指定的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild 參考](/visualstudio/msbuild/msbuild-reference)  
  
  