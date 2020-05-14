---
title: 專案元素(可視化工作室專案範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: 11052d8e585f1d06f6d787402001cfbbe2b6810f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701845"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>專案項目元素(可視化工作室專案範本)
指定項目範本中包含的檔。

> [!NOTE]
> 元素`ProjectItem`接受不同的屬性,具體取決於範本是針對項目還是項。 本主題介紹專案`ProjectItem`範本的元素。 有關專案範本`ProjectItem`元素的說明,請參閱[專案專案元素(可視化工作室專案範本)。](../extensibility/projectitem-element-visual-studio-item-templates.md)

 \<樣本>\<範本內容>\<專案>\<專案項>

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
| `TargetFileName` | 選擇性屬性。<br /><br /> 指定從範本創建專案時專案項的名稱和路徑。 此屬性可用於創建不同於範本 *.zip*檔案中的目錄結構的目錄結構,或者使用參數替換創建項名稱。 |
| `ReplaceParameters` | 選擇性屬性。<br /><br /> 布爾值,用於指定項是否具有從範本創建項目時必須替換的參數值。 預設值為 `false`。 |
| `OpenInEditor` | 選擇性屬性。<br /><br /> Boolean 值,用於指定在從範本創建專案時是否應在其相應的編輯[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]器 中打開該專案。<br /><br /> 和`OpenInWebBrowser``OpenInHelpBrowser`屬性`OpenInEditor`在值為`true`的項上將被忽略。<br /><br /> 預設值是 `false`。 |
| `OpenInWebBrowser` | 選擇性屬性。<br /><br /> Boolean 值,用於指定在從範本建立專案時是否應打開 Web 瀏覽器。<br /><br /> 只能在 Web 瀏覽器開啟專案本地的 HTML 檔和文字檔。 無法使用此屬性打開外部 URL。<br /><br /> 預設值是 `false`。 |
| `OpenInHelpBrowser` | 選擇性屬性。<br /><br /> Boolean 值,用於指定在從範本創建專案時是否應在説明查看器中打開該專案。<br /><br /> 只能在幫助瀏覽器中打開專案本地的 HTML 檔和文字檔。 無法使用此屬性打開外部 URL。<br /><br /> 預設值是 `false`。 |
| `OpenOrder` | 選擇性屬性。<br /><br /> 指定表示專案將在其各自的編輯器中打開的順序的數值。 所有值必須為 10 的倍數。 首先打開值`OpenOrder`較高的項。 |

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[專案](../extensibility/project-element-visual-studio-templates.md)|指定要新增到專案的檔案或目錄。|

## <a name="text-value"></a>文字值
 需要文字值。

 表示`string`樣本 *.zip*檔案中檔案的名稱或路徑的 。

## <a name="remarks"></a>備註
 `ProjectItem`是`Project`的可選子項。

 該`TargetFileName`屬性可用於創建不同於範本 *.zip*檔案中的目錄結構的目錄結構。 例如,如果檔案*MyFile.vb*存在於樣本 *.zip*檔案的根目錄中,但您希望該檔放置在從範本建立的所有項目中名為*CustomFiles*的目錄中,則可以使用以下 XML:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 該`TargetFileName`屬性還可用於重新命名其檔名中包含國際字元的檔。 例如,範本 *.zip*檔不能包含具有 Unicode 字元的檔名,因此必須先重新命名該檔,然後才能將其壓縮為 *.zip*檔。 該`TargetFileName`屬性可用於將檔名設置為原始 Unicode 檔名。

 該`TargetFileName`屬性還可用於使用參數重新命名檔案。 以下過程說明如何將存在於範本 *.zip*檔案的根目錄中的檔*MyFile.vb*重新命名為基於專案名的檔名。

### <a name="to-rename-files-with-parameters"></a>使用參數重新命名檔案

1. 在 *.vstemplate*檔案中使用以下 XML:

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. 在文字編輯器或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)][!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中打開專案檔(專案的 *.vbproj)。*

3. 在專案檔中尋找類似 XML 的行:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. 將代碼行取代為以下 XML:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    使用此範本建立專案時,檔案名將基於使用者在 **「新建專案**」對話框中輸入的名稱,並刪除所有不安全字元和空格。 有關詳細資訊,請參閱[樣本參數](../ide/template-parameters.md)。

## <a name="example"></a>範例
 下面的範例顯示了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]應用程式的專案範本的元數據。

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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [範本參數](../ide/template-parameters.md)
- [ProjectItem 項目 (Visual Studio 項目範本)](../extensibility/projectitem-element-visual-studio-item-templates.md)
