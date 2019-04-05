---
title: ProjectItem 項目 （Visual Studio 專案範本） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e08d08e8ec68e684ced1972f277af9b04805c3e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945649"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem 項目 (Visual Studio 專案範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定專案範本中所包含的檔案。  
  
> [!NOTE]
>  `ProjectItem`元素接受不同的屬性，根據該範本是否為專案或項目。 本主題說明`ProjectItem`專案範本的項目。 如需說明`ProjectItem`項目，項目範本，請參閱[ProjectItem 項目 （Visual Studio 項目範本）](../extensibility/projectitem-element-visual-studio-item-templates.md)。  
  
 \<VSTemplate>  
 \<TemplateContent>  
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
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`TargetFileName`|選擇性屬性。<br /><br /> 從範本建立專案時，請指定專案項目的路徑與名稱。 這個屬性是用來建立目錄結構的目錄結構不同，在範本的.zip 檔案中，或使用參數取代建立項目名稱。|  
|`ReplaceParameters`|選擇性屬性。<br /><br /> 布林值，指定的項目是否有從範本建立專案時，必須被取代的參數值。 預設值為 `false`。|  
|`OpenInEditor`|選擇性屬性。<br /><br /> 布林值，指定是否應該在其各自的編輯器中開啟項目[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]從範本建立專案時。<br /><br /> `OpenInWebBrowser`並`OpenInHelpBrowser`屬性會被忽略的項目上`OpenInEditor`的值`true`。<br /><br /> 預設值為 `false`。|  
|`OpenInWebBrowser`|選擇性屬性。<br /><br /> 布林值，指定項目是否應該會開啟網頁瀏覽器從範本建立專案。<br /><br /> 僅 HTML 檔案和文字檔的本機專案可以在 Web 瀏覽器中開啟。 無法開啟外部 Url，以這個屬性。<br /><br /> 預設值為 `false`。|  
|`OpenInHelpBrowser`|選擇性屬性。<br /><br /> 布林值，指定項目應該會開啟說明檢視器中從範本建立專案時。<br /><br /> 僅 HTML 檔案和文字檔的本機專案可以在說明瀏覽器中開啟。 無法開啟外部 Url，以這個屬性。<br /><br /> 預設值為 `false`。|  
|`OpenOrder`|選擇性屬性。<br /><br /> 指定數值，表示項目將會開啟在其各自的編輯器中的順序。 所有的值必須是 10 的倍數。 使用更高項目`OpenOrder`值第一次開啟。|  
  
### <a name="child-elements"></a>子元素  
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
  
 `TargetFileName`屬性可用來建立範本的.zip 檔案中的目錄結構不同的目錄結構。 例如，如果檔案`MyFile.vb`存在根目錄中的範本.zip 檔案，但您想要放置在目錄中名為的檔案`CustomFiles`從範本建立的所有專案，在中，您會使用下列 XML:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName`屬性也可用來重新命名檔案，其中包含其檔名中的國際字元。 比方說，範本.zip 檔案不能包含 Unicode 字元的檔案名稱，因此它可以壓縮成.zip 檔案之前，必須重新命名檔案。 `TargetFileName`屬性可用來將檔案名稱設回原始的 Unicode 檔案名稱。  
  
 `TargetFileName`屬性也可用來重新命名具有參數檔案。 下列程序說明如何將檔案重新命名`MyFile.vb`，存在於範本.zip 檔案，以根據專案名稱的檔案名稱的根目錄中。  
  
### <a name="to-rename-files-with-parameters"></a>若要重新命名具有參數檔案  
  
1.  這個.vstemplate 檔案中使用下列 XML:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  開啟專案檔案 (如.vbproj[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]專案) 在文字編輯器或[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
3.  看起來類似下列的 XML 專案檔中找到的一行：  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  取代下列 XML 程式碼行：  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     檔案名稱從這個範本建立專案時，會根據使用者輸入的名稱**新的專案**對話方塊中，其中所有 unsafe 字元和空格移除。 如需詳細資訊，請參閱 <<c0> [ 範本參數](../ide/template-parameters.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示的專案範本的中繼資料[!INCLUDE[csprcs](../includes/csprcs-md.md)]應用程式。  
  
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
