---
title: 專案範本 (Visual Studio 專案範本) |Microsoft Docs
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
ms.openlocfilehash: 84fb371460bc697660e176ca9df4c984d2b234bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838923"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem 項目 (Visual Studio 專案範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定包含在專案範本中的檔案。  
  
> [!NOTE]
> `ProjectItem`專案會根據範本是針對專案或專案而接受不同的屬性。 本主題說明 `ProjectItem` 專案範本的元素。 如需 `ProjectItem` 專案範本專案的說明，請參閱專案 [範本 (Visual Studio 專案範本 ](../extensibility/projectitem-element-visual-studio-item-templates.md)的 [專案] 元素) 。  
  
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
|`TargetFileName`|選擇性屬性。<br /><br /> 指定從範本建立專案時，專案專案的名稱和路徑。 這個屬性可用來建立與範本 .zip 檔中目錄結構不同的目錄結構，或是使用參數取代來建立專案名稱。|  
|`ReplaceParameters`|選擇性屬性。<br /><br /> 布林值，指定專案是否有在從範本建立專案時必須取代的參數值。 預設值為 `false`。|  
|`OpenInEditor`|選擇性屬性。<br /><br /> 布林值，指定在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 從範本建立專案時，是否應該在其各自的編輯器中開啟專案。<br /><br /> `OpenInWebBrowser` `OpenInHelpBrowser` 在值為的專案上，會忽略和屬性 `OpenInEditor` `true` 。<br /><br /> 預設值是 `false`。|  
|`OpenInWebBrowser`|選擇性屬性。<br /><br /> 布林值，指定從範本建立專案時，是否要開啟網頁瀏覽器的專案。<br /><br /> 只有專案本機的 HTML 檔案和文字檔可在網頁瀏覽器中開啟。 無法使用這個屬性開啟外部 Url。<br /><br /> 預設值是 `false`。|  
|`OpenInHelpBrowser`|選擇性屬性。<br /><br /> 布林值，指定當從範本建立專案時，是否應在說明檢視器中開啟專案。<br /><br /> 只有專案本機的 HTML 檔案和文字檔可以在 [說明瀏覽器] 中開啟。 無法使用這個屬性開啟外部 Url。<br /><br /> 預設值是 `false`。|  
|`OpenOrder`|選擇性屬性。<br /><br /> 指定表示專案將在其個別編輯器中開啟之順序的數位值。 所有值都必須是10的倍數。 `OpenOrder`系統會先開啟具有較高值的專案。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[專案](../extensibility/project-element-visual-studio-templates.md)|指定要加入至專案的檔案或目錄。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 `string`，代表範本 .zip 檔中檔案的名稱或路徑。  
  
## <a name="remarks"></a>備註  
 `ProjectItem` 是的選擇性子系 `Project` 。  
  
 `TargetFileName`屬性可以用來建立與範本 .zip 檔中目錄結構不同的目錄結構。 例如，如果檔案存在於 `MyFile.vb` 範本 .zip 檔案的根目錄中，但您想要將檔案放在 `CustomFiles` 從範本建立之所有專案中的命名目錄中，您可以使用下列 XML：  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName`屬性也可以用來重新命名在其檔案名中包含國際字元的檔案。 例如，範本 .zip 檔案不能包含 Unicode 字元的檔案名，因此必須重新命名檔案，才能將它壓縮成 .zip 檔案。 `TargetFileName`屬性可以用來將檔案名設回原始的 Unicode 檔案名。  
  
 `TargetFileName`屬性也可以用來以參數重新命名檔案。 下列程式說明如何將檔案 `MyFile.vb` （存在於範本 .zip 檔案的根目錄中）重新命名為根據專案名稱的檔案名。  
  
### <a name="to-rename-files-with-parameters"></a>使用參數重新命名檔案  
  
1. 在 .vstemplate 檔案中使用下列 XML：  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]在文字編輯器或中開啟專案) 的專案檔 ( [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vbproj。  
  
3. 在專案檔中尋找類似下列 XML 的行：  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4. 以下列 XML 取代程式程式碼：  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     從這個範本建立專案時，檔案名會以使用者在 [ **新增專案** ] 對話方塊中輸入的名稱為依據，並移除所有不安全的字元和空格。 如需詳細資訊，請參閱 [範本參數](../ide/template-parameters.md)。  
  
## <a name="example"></a>範例  
 下列範例會顯示應用程式專案範本的中繼資料 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 。  
  
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
 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和專案範本](../ide/creating-project-and-item-templates.md)   
 [範本參數](../ide/template-parameters.md)   
 [專案範本 (Visual Studio 專案範本) ](../extensibility/projectitem-element-visual-studio-item-templates.md)
