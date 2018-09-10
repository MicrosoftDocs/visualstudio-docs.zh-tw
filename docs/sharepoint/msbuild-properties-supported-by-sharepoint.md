---
title: SharePoint 支援的 MSBuild 屬性 |Microsoft Docs
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
ms.openlocfilehash: 1695a23ba9dddc27a37f23c714678fe6b779d328
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671143"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint 支援的 MsBuild 屬性
  任何[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]Microsoft.VisualStudio.SharePoint.targets 檔案、 專案檔或專案使用者檔案中定義的屬性可以用於[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 專案。 除了一般[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]專案中，SharePoint 所提供的屬性會定義 SharePoint 專案特有的其他屬性。  
  
 如需常見[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]屬性，請參閱[通用的 MSBuild 專案屬性](http://go.microsoft.com/fwlink/?LinkID=168687)。 針對您的程式語言所支援的屬性完整清單，查看 *.targets*檔案、 專案檔 (*.csproj*或是 *.vbproj*)，或專案使用者檔案 （*.csproj.user*或是 *.vbproj.user*)。  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>SharePoint 特有的 MsBuild 屬性
 下表列出[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]僅適用於 SharePoint 專案中的屬性[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 其他屬性存在，但它們僅供內部使用。  
  
|屬性名稱|描述|  
|-------------------|-----------------|  
|SharePointSiteUrl|字串，表示[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]至 SharePoint 網站。|  
|SandboxedSolution|布林值，指出解決方案是否為沙箱化方案。|  
|ActiveDeploymentConfiguration|現用部署組態。|  
|IncludeAssemblyInPackage|布林值，指出是否要將組件包含在封裝檔案中。|  
|PreDeploymentCommand|字串值，表示要在預先部署命令的步驟中執行的命令。|  
|PostDeploymentCommand|字串值，表示要在部署後命令步驟中執行的命令。|  
|CustomBeforeSharePointTargets|字串，表示路徑[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]目標檔案。 如果目標檔案存在，且已定義，它會匯入之前的任何 SharePoint 目標資料。 這個屬性可讓您依預先定義與封裝相關的屬性自訂封裝程序，而不需修改隨附的 SharePoint 目標檔，但目標檔案仍然會套用至所有 SharePoint 專案。|  
|CustomAfterSharePointTargets|字串，表示路徑[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]目標檔案。 如果目標檔案存在，且已定義，它是已匯入之後所有的 SharePoint 目標資料。 此屬性可讓您藉由覆寫封裝相關的屬性和目標，而不需要修改隨附的 SharePoint 目標檔，自訂套件的程序，但目標檔案仍然會套用至所有 SharePoint 專案。|  
|LayoutPath|字串，表示每個封裝檔案的暫時放置位置新增至之前的根目錄 *.wsp*檔案。 這個路徑可以是很有幫助您覆寫 BeforeLayout 和 AfterLayout 目標，來新增、 移除或修改要封裝的檔案，因為您可以用它來修改的內容 *.wsp*檔案。|  
|BasePackagePath|字串，表示封裝放在資料夾中。 這個值會使用專案中，例如 Bin\Debug 的輸出目錄。|  
|PackageExtension|字串，表示要附加至封裝的副檔名。 預設值是用於根據 wsp。|  
|AssemblyDeploymentTarget|字串，表示專案組件的 SharePoint 伺服器的部署所在的位置。 其值為 GlobalAssemblyCache （預設值） 或 WebApplication。 這個屬性也可以設定在 [屬性] 視窗中。|  
|PackageWithValidation|布林值，指定是否執行驗證的封裝之前。 這個屬性可讓您建置封裝時忽略驗證錯誤。|  
|ValidatePackageDependsOn|字串，定義 ValidatePackage 目標之前執行的其他目標。|  
|TokenReplacementFileExensions|字串，定義在封裝期間取代其權杖的檔案。|  
  
## <a name="use-msbuild-properties-in-the-properties-page"></a>在 [屬性] 頁面中使用 MsBuild 屬性
 取得彈性，而不是使用中的硬式編碼的字串**預先部署命令列**並**部署後命令列**方塊在 SharePoint 內容 頁面中，您可以使用 SharePoint做為引數的屬性。 比方說，而不是指定特定[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]字串的 SharePoint 網站，您可以改為使用`$(SharePointSiteUrl)`。  
  
> [!NOTE]  
>  您可以使用[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]變數語法`$(` *propertyName* `)`或環境變數語法`%` *propertyName* `%`指定的屬性。  
  
## <a name="see-also"></a>另請參閱
 [MSBuild 參考](/visualstudio/msbuild/msbuild-reference)  
  