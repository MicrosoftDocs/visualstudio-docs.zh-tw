---
title: 可取代的參數 |Microsoft Docs
description: 檢查 (token 的可替換參數) ，其會在設計階段不知道其實際值的 SharePoint 方案專案中，指定專案檔內部的值。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload: office
ms.openlocfilehash: 3eb6e737a1f939e05e6a6be7f2c9ba950fc411d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889495"
---
# <a name="replaceable-parameters"></a>可替換的參數
  可以在專案檔內使用可取代的參數或 *權杖*，以提供在設計階段不知道其實際值的 SharePoint 方案專案的值。 它們類似于標準範本權杖的功能 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 如需詳細資訊，請參閱 [範本參數](../ide/template-parameters.md)。

## <a name="token-format"></a>權杖格式
 權杖的開頭和結尾都是貨幣符號 ($) 字元。 在部署時，任何使用的標記都會在專案封裝至 SharePoint 方案套件 (*.wsp* 檔) 時，取代為實際值。 例如，權杖 **$SharePoint. Package.Name $** 可能會解析為 "Test SharePoint Package" 字串。

## <a name="token-rules"></a>權杖規則
 下列規則適用于權杖：

- 您可以在行的任何位置指定標記。

- 權杖無法跨越多行。

- 相同的標記可在同一行和同一個檔案中指定一次以上。

- 您可以在同一行上指定不同的標記。

  未遵循這些規則的權杖會被忽略，且不會產生警告或錯誤。

  在資訊清單轉換之後，會立即完成以字串值取代權杖的程式。 這種取代可讓使用者編輯具有權杖的資訊清單範本。

### <a name="token-name-resolution"></a>標記名稱解析
 在大部分的情況下，權杖會解析為特定值，而不論其包含在哪裡。 不過，如果權杖與封裝或功能相關，則權杖的值取決於其包含的位置。 例如，如果功能位於封裝 A 中，則權杖會 `$SharePoint.Package.Name$` 解析為 "Package a" 值。 如果封裝 B 中的相同功能，則會 `$SharePoint.Package.Name$` 解析為 "Package b"。

## <a name="tokens-list"></a>標記清單
 下表列出可用的權杖。

|名稱|描述|
|----------|-----------------|
|$SharePoint. FileName $|包含專案檔的名稱，例如 *NewProj .csproj*。|
|$SharePoint. FileNameWithoutExtension $|包含沒有副檔名之專案檔的名稱。 例如，"NewProj"。|
|$SharePoint. AssemblyFullName $|包含專案的輸出元件 (強式名稱) 的顯示名稱。|
|$SharePoint. AssemblyFileName $|包含專案輸出元件的名稱。|
|$SharePoint. AssemblyFileNameWithoutExtension $|包含專案輸出元件的名稱，不含副檔名。|
|$SharePoint. AssemblyPublicKeyToken $|包含專案輸出元件的公開金鑰 token，轉換成字串。 "X2" 十六進位格式的 (16 個字元。 ) |
|$SharePoint. Package.Name $|包含封裝的名稱。|
|$SharePoint. FileName $|包含封裝之定義檔的名稱。|
|$SharePoint FileNameWithoutExtension $|名稱 (沒有包含套件定義檔的副檔名) 。|
|$SharePoint. Package.Id $|包含封裝的 SharePoint 識別碼。 如果有一個以上的封裝使用某項功能，則此值會變更。|
|$SharePoint. FileName $|包含功能的定義檔名稱，例如 *Feature1。*|
|$SharePoint FileNameWithoutExtension $|功能定義檔的名稱，不含副檔名。|
|$SharePoint DeploymentPath $|封裝中包含功能的資料夾名稱。 此標記等同于功能設計工具中的 [部署路徑] 屬性。 範例值為 "Project1_Feature1"。|
|$SharePoint. Feature.Id $|包含功能的 SharePoint 識別碼。 如同所有功能層級的權杖，此權杖只能由封裝中包含的檔案使用，而不會直接新增至功能以外的封裝。|
|$SharePoint. ProjectItem.Name $|專案專案的名稱 (不是) 的檔案名，如同從 **ISharePointProjectItem.Name** 取得的名稱。|
|$SharePoint，請輸入 \<GUID> 。AssemblyQualifiedName $|符合語彙基元的 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 之類型的組件限定名稱。 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 的格式為小寫且對應於 Guid.ToString("D") 格式 (也就是 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx)。|
|$SharePoint，請輸入 \<GUID> 。FullName $|符合標記中 GUID 的型別的完整名稱。 GUID 的格式為小寫，而且會對應至 Guid.empty ( "D" ) 格式 (也就是 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx) 。|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>將延伸模組新增至 token 取代副檔名清單
 雖然在理論上，任何屬於封裝所包含之 SharePoint 專案專案的檔案都可以使用權杖，但是根據預設， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 只會在封裝檔案、資訊清單檔以及具有下列副檔名的檔案中搜尋標記：

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- Webpart

- .DWP

  這些延伸模組是由 VisualStudio 檔案中的專案所定義 `<TokenReplacementFileExtensions>` ，位於 ... \\<program files \> \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools 資料夾。

  不過，您可以將其他副檔名新增至清單。 將 `<TokenReplacementFileExtensions>` 專案加入至 sharepoint 專案檔中的任何 PropertyGroup，該專案會在 \<Import> sharepoint 目標檔案的之前定義。

> [!NOTE]
> 由於標記取代是在編譯專案之後發生，因此您不應該為編譯的檔案類型（例如 *.cs*、 *.vb* 或 *.resx*）加入副檔名。 只有在未編譯的檔案中，才會取代權杖。

 例如，若要將副檔名 (*. myextension* 和 *. Yourextension*) 新增至 token 取代副檔名清單，請將下列內容新增至專案 (*.csproj*) 檔：

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

 您可以將擴充功能直接新增至 *目標 (目標) 檔。* 但是，加入延伸模組會改變所有封裝在本機系統上的 SharePoint 專案的延伸模組清單，而不只是您自己的副檔名。 當您是系統上的唯一開發人員，或您的大部分專案都需要此擴充功能時，此擴充功能可能會很方便。 不過，由於它是系統專屬的，此方法無法移植，因此建議您改為將任何延伸模組新增至專案檔。

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
