---
title: 可置換的參數 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload: office
ms.openlocfilehash: f6e311f7c0268cecb94498fffda702438ea921b0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118795"
---
# <a name="replaceable-parameters"></a>可置換的參數
  可置換的參數，或*語彙基元*，可以使用專案檔內，以提供其實際的值不在設計階段已知的 SharePoint 方案項目中的值。 它們是類似的函式中的標準[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]範本語彙基元。 如需詳細資訊，請參閱 <<c0> [ 範本參數](/visualstudio/ide/template-parameters)。  
  
## <a name="token-format"></a>權杖格式
 權杖會開始，並以貨幣符號 （$） 字元結尾。 在部署中，使用任何權杖實際值時取代 SharePoint 方案套件封裝專案時 (*.wsp*檔案)。 例如，語彙基元 **$SharePoint.Package.Name$** 可能會解析為 「 測試 SharePoint 套件 」 的字串。  
  
## <a name="token-rules"></a>語彙基元的規則
 下列規則適用於語彙基元：  
  
-   語彙基元可以指定行中的任何位置。  
  
-   權杖不能跨越多行。  
  
-   在同一行，並在相同的檔案，可能會多次指定相同的語彙基元。  
  
-   可在同一行上指定不同的語彙基元。  
  
 不遵守這些規則的語彙基元會忽略，而且不會導致警告或錯誤。  
  
 取代為字串值的語彙基元是資訊清單的轉換後立即完成。 這項取代可讓使用者編輯與權杖的資訊清單範本。  
  
### <a name="token-name-resolution"></a>語彙基元的名稱解析
 在大部分情況下，權杖會解析為不論其中會包含特定值。 不過，如果權杖與封裝或功能時，權杖的值會取決於包含它。 例如，如果一項功能在封裝，則語彙基元`$SharePoint.Package.Name$`值解析為 「 套件 a。 」 如果相同的功能是在封裝 B，則`$SharePoint.Package.Name$`會解析成 「 套件 B 」  
  
## <a name="tokens-list"></a>語彙基元清單
 下表列出可用的權杖。  
  
|名稱|描述|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|名稱包含專案檔，例如*NewProj.csproj*。|  
|$SharePoint.Project.FileNameWithoutExtension$|包含專案檔不含副檔名的名稱。 例如，"NewProj。 」|  
|$SharePoint.Project.AssemblyFullName$|包含專案的顯示名稱 （強式名稱） 的輸出組件。|  
|$SharePoint.Project.AssemblyFileName$|包含專案的名稱的輸出組件。|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|包含專案的名稱的輸出組件，但不包括檔案名稱副檔名。|  
|$SharePoint.Project.AssemblyPublicKeyToken$|包含專案的公開金鑰 token 的輸出組件，轉換成字串。 (在 「 x2"16 個字元的十六進位格式。)|  
|$SharePoint.Package.Name$|包含封裝的名稱。|  
|$SharePoint.Package.FileName$|包含的封裝定義檔的名稱。|  
|$SharePoint.Package.FileNameWithoutExtension$|包含的封裝定義檔的名稱 （不含副檔名）。|  
|$SharePoint.Package.Id$|SharePoint 包含的封裝識別碼。 如果一項功能會在多個套件，此值將會變更。|  
|$SharePoint.Feature.FileName$|定義檔的名稱包含功能，例如*Feature1.feature*。|  
|$SharePoint.Feature.FileNameWithoutExtension$|功能定義檔案，不含副檔名的名稱。|  
|$SharePoint.Feature.DeploymentPath$|包含的功能套件中的資料夾名稱。 此權杖等同於功能設計工具中的 「 部署路徑 」 屬性。 值的範例是，「 Project1_Feature1"。|  
|$SharePoint.Feature.Id$|包含的功能的 SharePoint 識別碼。 此語彙基元，為具有所有功能層級語彙基元，可供只包含一項功能，透過封裝中的檔案不直接新增至封裝之外的功能。|  
|$SharePoint.ProjectItem.Name$|專案項目的名稱及其 （不是檔案名稱），以取得從**ISharePointProjectItem.Name**。|  
|$SharePoint.Type。\<GUID >。AssemblyQualifiedName $|符合語彙基元的 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 之類型的組件限定名稱。 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 的格式為小寫且對應於 Guid.ToString("D") 格式 (也就是 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx)。|  
|$SharePoint.Type。\<GUID >。FullName $|比對權杖中的 GUID 型別的完整名稱。 GUID 的格式為小寫且對應於 Guid.tostring 格式 (也就是 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx)。|  
  
## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>語彙基元取代檔案延伸模組清單中加入延伸模組
 雖然權杖理論上可供 SharePoint 專案項目包含在封裝中，根據預設，屬於任何檔案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]搜尋在封裝檔案，資訊清單檔案，並具有下列副檔名的檔案中的權杖：  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Web 組件  
  
-   DWP  
  
 這些擴充功能由定義`<TokenReplacementFileExtensions>`項目在 Microsoft.VisualStudio.SharePoint.targets 檔案中，位於...\\< 程式檔案\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools 資料夾。  
  
 不過，您可以將其他副檔名加入清單。 新增`<TokenReplacementFileExtensions>`之前會定義 SharePoint 專案檔中的任何 PropertyGroup 項目\<匯入 > 的 於 SharePoint 目標檔。  
  
> [!NOTE]  
>  編譯專案之後，就會發生語彙基元取代，因為您不應該新增會進行編譯，這類的檔案類型的檔案副檔名 *.cs*， *.vb*或是 *.resx*。 Token 已被取代，只在未編譯的檔案。  
  
 例如，若要新增的檔案名稱副檔名 (*.myextension*並 *.yourextension*) 的語彙基元取代檔案名稱的副檔名清單，您會將下列內容新增至專案 (*.csproj*) 檔案：  
  
```xml  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 您可以直接對目標加入延伸模組 (*.targets*) 檔案。 不過，新增擴充功能會變更本機系統上封裝的所有 SharePoint 專案延伸模組清單，不只是您自己。 當您在系統上唯一的開發人員，或大部分的專案需要它，此延伸模組可能會很方便。 不過，因為它是特定的系統，這種方法不是可攜性，因此，建議您將任何延伸模組加入專案檔改為。  
  
## <a name="see-also"></a>另請參閱
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
