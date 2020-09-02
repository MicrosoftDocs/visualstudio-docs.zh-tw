---
title: " (Visual Studio 範本的 ProjectCollection 元素) |Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9457b1142c94658da489ce7401b7c22d28df903d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193928"
---
# <a name="projectcollection-element-visual-studio-templates"></a>ProjectCollection 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定多專案範本的組織和內容。  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
  
## <a name="syntax"></a>語法  
  
```  
<ProjectCollection>  
    <ProjectTemplateLink> ... </ProjectTemplateLink>  
    <SolutionFolder> ... </SolutionFolder>  
</ProjectCollection>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定多專案範本中的專案。|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 將多專案範本中的專案分組。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必要元素。<br /><br /> 指定範本的內容。|  
  
## <a name="remarks"></a>備註  
 多專案範本是做為兩個以上專案的容器使用。 `ProjectCollection`元素可用來指定要包含在範本中的專案。 如需多專案範本的詳細資訊，請參閱 [如何：建立多專案範本](../ide/how-to-create-multi-project-templates.md)。  
  
## <a name="example"></a>範例  
 這個範例將示範簡單的多專案根 .vstemplate 檔案。 在這個範例中，範本包含兩個專案 `My Windows Application` 和 `My Class Library`。 `ProjectName` 項目的 `ProjectTemplateLink` 屬性會設定 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的名稱，以指派此專案。 如果 `ProjectName` 屬性不存在，則 .vstemplate 檔案的名稱會做為專案名稱。  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和專案範本](../ide/creating-project-and-item-templates.md)   
 [如何：建立多專案的範本](../ide/how-to-create-multi-project-templates.md)
