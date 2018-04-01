---
title: CreateNewFolder 項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dab5b47904360fbc87b6799affe290cd3ab94398
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createnewfolder-element-visual-studio-templates"></a>CreateNewFolder 項目 (Visual Studio 範本)
決定是否要檢查建立專案的目標目錄是否不存在。 如果目錄不存在，則可為專案建立全新的目錄。 此設定通常會由 `NewProjectRequiresNewFolder(VsTemplate)` 登錄旗標 (`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`) 覆寫，所有一般專案類型都會使用此設定來決定是否要在新目錄中建立新專案。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<CreateNewFolder >  
  
## <a name="syntax"></a>語法  
  
```  
<CreateNewFolder>  
    true/false  
</CreateNewFolder>  
```  
  
## <a name="type"></a>類型  
 `Boolean`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 文字必須是 `true` 或 `false`，表示是否應該在從範本建立專案時建立新的容器資料夾。  
  
## <a name="remarks"></a>備註  
 `CreateNewFolder` 是選擇性項目。 預設值是 `true`。  
  
 僅在基礎專案系統支援時，`CreateNewFolder` 才會接受在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 項目中指定的值。  
  
## <a name="example"></a>範例  
 下列程式碼範例指定從範本建立專案時，不要建立新資料夾。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <CreateNewFolder>false</CreateNewFolder>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
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
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)