---
title: ProjectItem 項目 （Visual Studio 專案範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a7dfbfd03df24c2968dc9dae141ffc7a300e8be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142522"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem 項目 (Visual Studio 專案範本)
指定專案範本中所包含的檔案。  
  
> [!NOTE]
>  `ProjectItem`元素接受不同的屬性，根據範本是否為專案或項目。 本主題說明`ProjectItem`專案範本的項目。 如需說明`ProjectItem`項目，項目範本，請參閱[ProjectItem 項目 （Visual Studio 項目範本）](../extensibility/projectitem-element-visual-studio-item-templates.md)。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<專案項目 >  
  
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
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`TargetFileName`|選擇性屬性。<br /><br /> 從範本建立專案時，請指定專案項目的路徑與名稱。 這個屬性是用於建立目錄結構不同的目錄結構中範本的.zip 檔案，或使用來建立項目名稱的參數取代。|  
|`ReplaceParameters`|選擇性屬性。<br /><br /> 布林值，指定項目是否有從範本建立專案時，必須被取代的參數值。 預設值為 `false`。|  
|`OpenInEditor`|選擇性屬性。<br /><br /> 布林值，指定是否應該在其各自的編輯器中開啟項目[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]從範本建立專案時。<br /><br /> `OpenInWebBrowser`和`OpenInHelpBrowser`上的項目就會忽略屬性`OpenInEditor`值`true`。<br /><br /> 預設值是 `false`。|  
|`OpenInWebBrowser`|選擇性屬性。<br /><br /> 布林值，指定項目是否應該會開啟網頁瀏覽器從範本建立專案。<br /><br /> 僅 HTML 檔和文字檔的本機專案可以開啟網頁瀏覽器中。 無法開啟外部 Url，使用這個屬性。<br /><br /> 預設值是 `false`。|  
|`OpenInHelpBrowser`|選擇性屬性。<br /><br /> 布林值，指定是否開啟項目應該會說明檢視器中從範本建立專案時。<br /><br /> 僅 HTML 檔和文字檔的本機專案可以在說明瀏覽器中開啟。 無法開啟外部 Url，使用這個屬性。<br /><br /> 預設值是 `false`。|  
|`OpenOrder`|選擇性屬性。<br /><br /> 指定數字的值，表示項目，會在其各自的編輯器中開啟的順序。 所有的值必須是 10 的倍數。 具有更高項目`OpenOrder`值第一次開啟。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|指定要加入至專案目錄的檔案。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 A `string` ，表示範本的.zip 檔中的檔案的名稱或路徑。  
  
## <a name="remarks"></a>備註  
 `ProjectItem` 是選擇性的子系的`Project`。  
  
 `TargetFileName`屬性可以用來建立範本的.zip 檔案中的目錄結構與不同的目錄結構。 例如，如果檔案`MyFile.vb`存在根目錄中的範本的.zip 檔案，但您想要放置在目錄中名為的檔案`CustomFiles`在從範本建立的所有專案，您會使用下列 XML:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName`屬性也可用來重新命名檔案，其中包含在其檔案名稱中的國際字元。 比方說，樣板的.zip 檔案不能包含 Unicode 字元，檔案名稱，讓它可以壓縮成.zip 檔之前，必須重新命名檔案。 `TargetFileName`屬性可以用來將檔案名稱設回原始的 Unicode 檔案名稱。  
  
 `TargetFileName`屬性也可用來重新命名檔案使用的參數。 下列程序說明如何重新命名檔案`MyFile.vb`，位於範本的.zip 檔案，以根據專案名稱的檔案名稱的根目錄。  
  
### <a name="to-rename-files-with-parameters"></a>若要重新命名檔案使用的參數  
  
1.  .Vstemplate 檔案中使用下列 XML:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  開啟專案檔 (如.vbproj[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]專案) 中的文字編輯器或[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
3.  看起來類似下列的 XML 專案檔中尋找的那一行：  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  取代下列 XML 程式碼行：  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     檔案名稱從這個範本建立專案時，會根據使用者輸入的名稱**新專案**對話方塊中的，與所有 unsafe 字元和空格已移除。 如需詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。  
  
## <a name="example"></a>範例  
 下列範例會顯示專案範本的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]應用程式。  
  
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
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [範本參數](../ide/template-parameters.md)   
 [ProjectItem 元素 (Visual Studio 項目範本)](../extensibility/projectitem-element-visual-studio-item-templates.md)