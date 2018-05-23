---
title: 可置換的參數 |Microsoft 文件
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
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86d6b08d209703f73901d7a839c731e1a9a63fdd
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="replaceable-parameters"></a>可置換的參數
  可置換的參數，或*語彙基元*，可以使用專案檔內，以提供其實際的值不在設計階段已知的 SharePoint 方案項目中的值。 其功能類似於標準 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 範本語彙基元。 如需詳細資訊，請參閱[範本參數](/visualstudio/ide/template-parameters)。  
  
## <a name="token-format"></a>權杖格式  
 語彙基元開頭和結尾是貨幣符號 （$） 字元。 在部署中，用任何的權杖會取代成實際值，在封裝專案至 SharePoint 方案套件 （.wsp 檔案）。 例如，語彙基元 **$SharePoint.Package.Name$** 可能會解析成字串 「 測試 SharePoint 封裝 」。  
  
## <a name="token-rules"></a>語彙基元的規則  
 下列規則適用於語彙基元：  
  
-   語彙基元可以指定行中的任何位置。  
  
-   語彙基元無法跨越多行。  
  
-   在同一行和相同的檔案中，相同的語彙基元可能指定多次。  
  
-   可在同一行上指定不同的語彙基元。  
  
 不符合這些規則的語彙基元會被忽略，但未提供警告或錯誤。  
  
 由字串值的語彙基元取代是資訊清單的轉換後立即完成。 這項取代可讓使用者編輯資訊清單範本語彙基元。  
  
### <a name="token-name-resolution"></a>語彙基元的名稱解析  
 在大部分情況下，權杖會解析為不論它包含特定值。 不過，如果語彙基元相關的封裝或功能，此語彙基元的值取決於包含它。 例如，如果功能在封裝，然後在語彙基元`$SharePoint.Package.Name$`解析 「 封裝 A 」 的值 如果相同的功能是在封裝 B 則`$SharePoint.Package.Name$`解析為 「 套件 B 」。  
  
## <a name="tokens-list"></a>語彙基元清單  
 下表列出可用的權杖。  
  
|名稱|描述|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|包含專案檔，例如"NewProj.csproj 」 的名稱。|  
|$SharePoint.Project.FileNameWithoutExtension$|包含專案檔不含副檔名的名稱。 例如，"NewProj"。|  
|$SharePoint.Project.AssemblyFullName$|包含專案的顯示名稱 （強式名稱） 的輸出組件。|  
|$SharePoint.Project.AssemblyFileName$|包含專案的名稱之輸出組件。|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|包含專案的名稱之輸出組件，但不包括檔案名稱副檔名。|  
|$SharePoint.Project.AssemblyPublicKeyToken$|包含專案的公開金鑰 token 的輸出組件中，轉換為字串。 (在"x2"16 個字元的十六進位格式。)|  
|$SharePoint.Package.Name$|包含封裝名稱。|  
|$SharePoint.Package.FileName$|包含的封裝定義檔的名稱。|  
|$SharePoint.Package.FileNameWithoutExtension$|包含的封裝定義檔的名稱 （不含副檔名）。|  
|$SharePoint.Package.Id$|包含封裝的 SharePoint ID。 如果多個封裝中使用的功能，這個值將會變更。|  
|$SharePoint.Feature.FileName$|包含的功能，例如，Feature1.feature 定義檔的名稱。|  
|$SharePoint.Feature.FileNameWithoutExtension$|不含副檔名的功能定義檔名稱。|  
|$SharePoint.Feature.DeploymentPath$|包含封裝中的功能的資料夾名稱。 這個語彙基元等同於功能設計工具中的 「 部署路徑 」 屬性。 範例值是"Project1_Feature1"。|  
|$SharePoint.Feature.Id$|包含功能的 SharePoint ID。 此語彙基元，所有功能層級語彙基元，可使用的功能，透過封裝中包含的檔案只能由不直接加入封裝之外的功能。|  
|$SharePoint.ProjectItem.Name$|專案項目的名稱及其 （不是檔案名稱），以取得從**ISharePointProjectItem.Name**。|  
|$SharePoint.Type。\<GUID >。AssemblyQualifiedName $|符合語彙基元的 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 之類型的組件限定名稱。 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 的格式為小寫且對應於 Guid.ToString("D") 格式 (也就是 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx)。|  
|$SharePoint.Type。\<GUID >。FullName $|比對之權杖中的 GUID 的類型完整名稱。 GUID 的格式為小寫且對應於 Guid.tostring 格式 (也就是 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx)。|  
  
## <a name="adding-extensions-to-the-token-replacement-file-extensions-list"></a>語彙基元替換加入延伸模組檔案的副檔名清單  
 雖然語彙基元理論上可供 SharePoint 專案項目包含在封裝中，依預設，屬於任何檔案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]搜尋在封裝檔案，資訊清單檔案，並具有下列副檔名的檔案中的語彙基元：  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Web 組件  
  
-   DWP  
  
 這些擴充功能由定義`<TokenReplacementFileExtensions>`項目在 Microsoft.VisualStudio.SharePoint.targets 檔案中，位於...\\< 程式檔案\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools 資料夾。  
  
 不過，您可以將其他檔案的副檔名加入清單。 新增`<TokenReplacementFileExtensions>`定義之前加入 SharePoint 專案檔中的任何 PropertyGroup 項目\<匯入 > 的 於 SharePoint 目標檔。  
  
> [!NOTE]  
>  編譯專案之後，就會發生 token 取代，因為您不應該新增編譯的檔案類型，例如.cs、.vb 或.resx 檔案副檔名。 語彙基元取代只在未編譯的檔案。  
  
 比方說，若要加入的語彙基元取代檔案名稱的副檔名清單中的檔案名稱副檔名".myextension"和".yourextension"，您可以加入下列命令以`.csproj`檔案：  
  
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
  
 擴充功能直接加入.targets 檔案。 不過，如此一來改變不只是封裝在本機系統上，所有 SharePoint 專案擴充功能清單自己。 當您在系統上唯一的開發人員，或大部分的專案需要它，這可能是很方便。 不過，因為它是特定系統，此方法不是高度可攜性，因此，建議您將任何擴充功能加入專案檔改為。  
  
## <a name="see-also"></a>另請參閱  
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  