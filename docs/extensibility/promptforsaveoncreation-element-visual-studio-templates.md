---
title: PromptForSaveOnCreation 項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation
helpviewer_keywords:
- PromptForSaveOnCreation element [Visual Studio project templates]
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 92be0bc15542010cfeea8a9ee70e69ff52e14163
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="promptforsaveoncreation-element-visual-studio-templates"></a>PromptForSaveOnCreation 項目 (Visual Studio 範本)
指定是否會提示使用者輸入的儲存位置透過專案**新專案**對話方塊建立專案時。 如果這個項目設定為`true`，則會提示使用者輸入新的儲存位置; 如果`false`，則它們不會提示您。 （也就是會建立暫存的專案）。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<PromptForSaveOnCreation>  
  
## <a name="syntax"></a>語法  
  
```  
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此文字必須`true`或`false`，`true`指出將會提示使用者輸入儲存位置建立新專案時。  
  
## <a name="remarks"></a>備註  
 `PromptForSaveOnCreation` 是選擇性項目。 預設值是 `false`。  
  
 暫存專案是您可以建立和修改，而不將該專案的內容儲存在磁碟上。  
  
## <a name="example"></a>範例  
 下列範例會設定的值`PromptForSaveOnCreation`等於`false`，指定允許要建立為暫存專案的專案。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>  
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
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)