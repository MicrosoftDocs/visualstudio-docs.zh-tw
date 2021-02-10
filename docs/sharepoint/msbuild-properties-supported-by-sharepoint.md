---
title: SharePoint 支援的 MSBuild 屬性 |Microsoft Docs
description: 閱讀和所支援的 MSBuild 屬性名稱和描述的清單，這是 SharePoint 專用的清單。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 20458cc7047e913e13f4594380d4b4946b44ec17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938508"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint 支援的 MsBuild 屬性
  您 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 可以在 sharepoint 專案中使用 VisualStudio 檔案、專案檔或專案使用者檔案中定義的任何屬性 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 除了專案所提供的通用 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 屬性之外，sharepoint 也會定義 sharepoint 專案專屬的其他屬性。

 如需通用屬性的清單 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] ，請參閱 [一般 MSBuild 專案屬性](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100))。 如需程式設計語言所支援之屬性的完整清單，請查看 *.targets* 檔案、專案檔 (*.csproj* 或 *vbproj*) ，或專案使用者檔案 (*.csproj. user* 或 *vbproj. user*) 。

## <a name="msbuild-properties-specific-to-sharepoint"></a>SharePoint 專用的 MsBuild 屬性
 下表列出 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 在中特別適用于 SharePoint 專案的屬性 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 有其他屬性存在，但它們可供內部使用。

|屬性名稱|描述|
|-------------------|-----------------|
|SharePointSiteUrl|表示 SharePoint 網站的字串 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 。|
|SandboxedSolution|布林值，指出方案是否為沙箱化方案。|
|ActiveDeploymentConfiguration|主動式部署設定。|
|IncludeAssemblyInPackage|指出元件是否包含在封裝檔案中的布林值。|
|PreDeploymentCommand|字串值，表示要在預先部署命令步驟中執行的命令。|
|PostDeploymentCommand|字串值，表示要在部署後命令步驟中執行的命令。|
|CustomBeforeSharePointTargets|表示目標檔案路徑的字串 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 。 如果目標檔案存在且已定義，則會在任何 SharePoint 目標資料之前匯入。 這個屬性可讓您透過預先定義封裝相關屬性來自訂封裝程式，而不需修改隨附的 SharePoint 目標檔案，但目標檔案仍會套用至所有 SharePoint 專案。|
|CustomAfterSharePointTargets|表示目標檔案路徑的字串 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 。 如果目標檔案存在且已定義，則會在所有 SharePoint 目標資料之後匯入。 這個屬性可讓您藉由覆寫封裝相關的屬性和目標來自訂封裝程式，而不需要修改隨附的 SharePoint 目標檔案，但目標檔案仍會套用至所有 SharePoint 專案。|
|LayoutPath|字串，代表要封裝的每個檔案在新增至 *.wsp* 檔之前，會暫時放置的根目錄。 當您覆寫 BeforeLayout 和 AfterLayout 目標來新增、移除或修改要封裝的檔案時，這個路徑會很有用，因為您可以用它來改變 *.wsp* 檔的內容。|
|BasePackagePath|表示放置封裝之資料夾的字串。 這個值會使用專案的輸出目錄，例如 Bin\Debug。|
|PackageExtension|字串，表示要附加至封裝的副檔名。 預設值是 wsp。|
|AssemblyDeploymentTarget|字串，代表 SharePoint 伺服器上部署專案元件的位置。 其值為 GlobalAssemblyCache (預設) 或 WebApplication。 您也可以在屬性視窗中設定這個屬性。|
|PackageWithValidation|指定是否在封裝之前執行驗證的布林值。 這個屬性可讓您在建立封裝時忽略驗證錯誤。|
|ValidatePackageDependsOn|字串，定義要在 ValidatePackage 目標之前執行的其他目標。|
|TokenReplacementFileExensions|字串，定義封裝期間取代其標記的檔案。|

## <a name="use-msbuild-properties-in-the-properties-page"></a>在 [屬性] 頁面中使用 MsBuild 屬性
 為了提供彈性，而不是在 [SharePoint 屬性] 頁面上的 [ **預先部署命令列** ] 和 [ **部署後命令列** ] 方塊中使用硬式編碼的字串，您可以使用 sharepoint 屬性做為引數。 例如，您可以改為使用，而不是指定 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] SharePoint 網站的特定字串 `$(SharePointSiteUrl)` 。

> [!NOTE]
> 您可以使用 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 變數語法 `$(` *propertyname* `)` 或環境變數語法 `%` *propertyname* `%` 來指定屬性。

## <a name="see-also"></a>另請參閱

- [MSBuild 參考](../msbuild/msbuild-reference.md)