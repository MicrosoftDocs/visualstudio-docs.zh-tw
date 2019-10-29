---
title: SharePoint 支援的 MSBuild 屬性 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5470160c6b0af1af39238a14319ad497e1541a43
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985168"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint 支援的 MsBuild 屬性
  在 VisualStudio 檔案、專案檔或專案使用者檔案中定義的任何 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 屬性，都可以在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 專案中使用。 除了專案所提供的一般 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 屬性以外，SharePoint 也會定義 SharePoint 專案特有的其他屬性。

 如需一般 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 屬性的清單，請參閱[一般 MSBuild 專案屬性](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100))。 如需程式設計語言所支援屬性的完整清單，請查看 *.targets*檔案、專案檔（ *.csproj*或 *. vbproj*），或專案使用者檔案（ *.csproj. user*或 *. vbproj. user*）。

## <a name="msbuild-properties-specific-to-sharepoint"></a>SharePoint 特有的 MsBuild 屬性
 下表列出特別適用于 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中 SharePoint 專案的 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 屬性。 有其他屬性存在，但它們是供內部使用。

|屬性名稱|描述|
|-------------------|-----------------|
|SharePointSiteUrl|表示 SharePoint 網站 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 的字串。|
|SandboxedSolution|布林值，指出方案是否為沙箱化方案。|
|ActiveDeploymentConfiguration|使用中的部署設定。|
|IncludeAssemblyInPackage|布林值，指出元件是否包含在封裝檔案中。|
|PreDeploymentCommand|字串值，表示要在預先部署命令步驟中執行的命令。|
|PostDeploymentCommand|字串值，表示要在部署後命令步驟中執行的命令。|
|CustomBeforeSharePointTargets|表示 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 目標檔案路徑的字串。 如果目標檔案存在且已定義，則會在任何 SharePoint 目標資料之前匯入該檔案。 這個屬性可讓您在不修改隨附的 SharePoint 目標檔案的情況下預先定義封裝相關的屬性來自訂封裝程式，但是目標檔案仍適用于所有 SharePoint 專案。|
|CustomAfterSharePointTargets|表示 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 目標檔案路徑的字串。 如果目標檔案存在且已定義，則會在所有 SharePoint 目標資料之後匯入該檔案。 這個屬性可讓您透過覆寫封裝相關的屬性和目標來自訂封裝程式，而不需要修改隨附的 SharePoint 目標檔案，但是目標檔案仍適用于所有 SharePoint 專案。|
|LayoutPath|字串，代表要封裝之每個檔案在加入 *.wsp*檔案之前，暫時放置的根目錄。 當您覆寫 BeforeLayout 和 AfterLayout 目標來新增、移除或修改要封裝的檔案時，這個路徑會很有用，因為您可以用它來改變 *.wsp*檔案的內容。|
|BasePackagePath|字串，表示放置封裝所在的資料夾。 這個值會使用專案的輸出目錄，例如 Bin\Debug。|
|PackageExtension|字串，表示要附加至封裝的副檔名。 預設值為 [wsp]。|
|Assemblydeploymenttarget 無效|字串，表示在 SharePoint 伺服器上部署專案元件的位置。 其值可以是 GlobalAssemblyCache （預設值）或 WebApplication。 這個屬性也可以在屬性視窗中設定。|
|Packagewithvalidation 無效|布林值，指定是否要在封裝之前執行驗證。 這個屬性可讓您在建立封裝時忽略驗證錯誤。|
|ValidatePackageDependsOn|字串，定義要在 ValidatePackage 目標之前執行的其他目標。|
|TokenReplacementFileExensions|字串，定義封裝期間取代其標記的檔案。|

## <a name="use-msbuild-properties-in-the-properties-page"></a>在屬性頁面中使用 MsBuild 屬性
 為了提供彈性，您可以使用 SharePoint 屬性做為引數，而不是在 [SharePoint 屬性] 頁面的 [**預先部署] 命令列**和**部署後命令列**方塊中使用硬式編碼的字串。 例如，您可以改為使用 `$(SharePointSiteUrl)`，而不是指定 SharePoint 網站的特定 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 字串。

> [!NOTE]
> 您可以使用 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 變數語法 `$(`*propertyname*`)` 或 `%`*propertyName*`%` 的環境變數語法來指定屬性。

## <a name="see-also"></a>請參閱

- [MSBuild 參考](../msbuild/msbuild-reference.md)