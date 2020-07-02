---
title: '[專案] 元素（Visual Studio 專案範本） |Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 943f50823892e3cd942709bdcd4556b65c006b58
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770307"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>[專案] 元素（Visual Studio 專案範本）
指定專案範本中包含的檔案。

> [!NOTE]
> `ProjectItem`元素會根據範本是針對專案或專案來接受不同的屬性。 本主題說明 `ProjectItem` 專案範本的元素。 如需 `ProjectItem` 專案範本之元素的說明，請參閱 [專案][元素（Visual Studio 專案範本）](../extensibility/projectitem-element-visual-studio-item-templates.md)。

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<ProjectItem>

## <a name="syntax"></a>語法

```
<ProjectItem
    TargetFileName="TargetFileName.ext"
    ReplaceParameters="true/false"
    OpenInEditor="true/false"
    OpenInWebBrowser="true/false"
    OpenInHelpBrowser="true/false"
    OpenOrder="Value">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性

| 屬性 | 描述 |
|---------------------| - |
| `TargetFileName` | 選擇性屬性。<br /><br /> 指定從範本建立專案時，專案專案的名稱和路徑。 這個屬性可用來建立不同于範本 *.zip*檔案中目錄結構的目錄結構，或用於建立專案名稱的參數取代。 |
| `ReplaceParameters` | 選擇性屬性。<br /><br /> 布林值，指定專案是否具有必須在從範本建立專案時取代的參數值。 預設值為 `false`。 |
| `OpenInEditor` | 選擇性屬性。<br /><br /> 布林值，指定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 當從範本建立專案時，是否應該在其各自的編輯器中開啟專案。<br /><br /> `OpenInWebBrowser` `OpenInHelpBrowser` 值為的專案會忽略和屬性 `OpenInEditor` `true` 。<br /><br /> 預設值為 `false`。 |
| `OpenInWebBrowser` | 選擇性屬性。<br /><br /> 布林值，指定從範本建立專案時，是否要開啟 Web 瀏覽器的專案。<br /><br /> 只有專案本機的 HTML 檔案和文字檔可以在網頁瀏覽器中開啟。 無法使用這個屬性開啟外部 Url。<br /><br /> 預設值為 `false`。 |
| `OpenInHelpBrowser` | 選擇性屬性。<br /><br /> 布林值，指定從範本建立專案時，是否要在說明檢視器中開啟專案。<br /><br /> 只有專案本機的 HTML 檔案和文字檔可以在 [說明] 瀏覽器中開啟。 無法使用這個屬性開啟外部 Url。<br /><br /> 預設值為 `false`。 |
| `OpenOrder` | 選擇性屬性。<br /><br /> 指定數值，代表專案將在其各自的編輯器中開啟的順序。 所有的值都必須是10的倍數。 `OpenOrder`系統會先開啟具有較高值的專案。 |

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[專案](../extensibility/project-element-visual-studio-templates.md)|指定要加入至專案的檔案或目錄。|

## <a name="text-value"></a>文字值
 需要文字值。

 `string`，代表範本 *.zip*檔案中檔案的名稱或路徑。

## <a name="remarks"></a>備註
 `ProjectItem`是的選擇性子系 `Project` 。

 `TargetFileName`屬性可以用來建立不同于範本 *.zip*檔案中目錄結構的目錄結構。 例如，如果檔案*myfile.txt*存在於範本 *.zip*檔案的根目錄中，但是您想要將檔案放在從範本建立的所有專案中名為*CustomFiles*的目錄中，您會使用下列 XML：

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 `TargetFileName`屬性也可以用來重新命名檔案，其中包含其檔案名中的國際字元。 例如，範本 *.zip*檔案不能包含具有 Unicode 字元的檔案名，因此必須先重新命名檔案，才能將它壓縮成 *.zip*檔案。 `TargetFileName`屬性可以用來將檔案名設回原始的 Unicode 檔案名。

 `TargetFileName`屬性也可以用來重新命名具有參數的檔案。 下列程式說明如何將檔案*myfile.txt*（存在於範本 *.zip*檔案的根目錄中）重新命名為根據專案名稱的檔案名。

### <a name="to-rename-files-with-parameters"></a>以參數重新命名檔案

1. 在 *.vstemplate*檔案中使用下列 XML：

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. 在文字編輯器或中，開啟專案檔（專案的 *. vbproj* [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ） [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

3. 找出專案檔中看起來類似下列 XML 的那一行：

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. 以下列 XML 取代程式程式碼：

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    從這個範本建立專案時，檔案名會以使用者在 [**新增專案**] 對話方塊中輸入的名稱為基礎，並移除所有 unsafe 字元和空格。 如需詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。

## <a name="example"></a>範例
 下列範例會顯示應用程式之專案範本的中繼資料 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 。

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [範本參數](../ide/template-parameters.md)
- [ProjectItem 項目 (Visual Studio 項目範本)](../extensibility/projectitem-element-visual-studio-item-templates.md)
