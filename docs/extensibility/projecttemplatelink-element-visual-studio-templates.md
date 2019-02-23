---
title: ProjectTemplateLink 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc253967cf4f52d6e958b8b092f44f753bac2e9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698088"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink 項目 （Visual Studio 範本）
指定的路徑 *.vstemplate*多專案範本中的某個專案的檔案。

 \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<ProjectTemplateLink> -or- \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<SolutionFolder> \<ProjectTemplateLink>

## <a name="syntax"></a>語法

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`ProjectName`|選擇性屬性。<br /><br /> 指定多專案範本中每一個別專案的名稱。 **新的專案**對話方塊無法指派給個別專案的名稱。|
|`CopyParameters`|可將主群組範本中的所有變數複製到每一個連結的範本。<br /><br /> 在連結之範本中的參數會有前置詞 `"$ext_*$"`。 例如，如果在父群組範本參數`$projectname$`具有值**ExampleProject1**，當連結的範本取得輪到它執行，它會取得參數`$ext_projectname$`，這是一份`$projectname$`從父群組範本的參數。<br /><br /> 這樣可讓連結的範本共用某些只有在父群組範本中才方便建立的通用參數。<br /><br /> 這個屬性是選擇性的，如果未包含，則它會自動預設為 `false`。<br /><br /> 已在 Visual Studio 2013 Update 2 中引入。 若要參考正確的產品版本，請參閱[參考組件提供在 Visual Studio 2013 SDK Update 2](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb)。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|指定多專案範本的組織和內容。|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|將多專案範本中的專案分組。|

## <a name="text-value"></a>文字值
 需要文字值。

 此文字會指定的路徑 *.vstemplate*範本的檔案。

## <a name="remarks"></a>備註
 多專案範本是做為兩個以上專案的容器使用。 `ProjectTemplateLink`項目用以指定的位置 *.vstemplate*其中一個範本中的專案檔。 *.Vstemplate*檔案的多專案範本包含一個`ProjectTemplateLink`每個專案範本中的項目。 如需有關多專案範本的詳細資訊，請參閱[How to:建立多專案範本](../ide/how-to-create-multi-project-templates.md)。

## <a name="example"></a>範例
 此範例將示範簡單的多專案根 *.vstemplate*檔案。 在這個範例中，範本包含兩個專案 `My Windows Application` 和 `My Class Library`。 `ProjectName` 項目的 `ProjectTemplateLink` 屬性會設定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的名稱，以指派此專案。 如果`ProjectName`屬性不存在，名稱 *.vstemplate*檔案做為專案名稱。

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
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [如何：建立多專案範本](../ide/how-to-create-multi-project-templates.md)