---
title: 專案集合元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12a22ca28c90ed1df69529ed3004b417b5e04276
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701970"
---
# <a name="projectcollection-element-visual-studio-templates"></a>專案集合元素(可視化工作室範本)
指定多專案範本的組織和內容。

 \<VStemplate \<\<>模板内容>项目集合>

## <a name="syntax"></a>語法

```xml
<ProjectCollection>
    <ProjectTemplateLink> ... </ProjectTemplateLink>
    <SolutionFolder> ... </SolutionFolder>
</ProjectCollection>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 在多項目範本中指定專案。|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 將多專案範本中的專案分組。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必要元素。<br /><br /> 指定範本的內容。|

## <a name="remarks"></a>備註
 多專案範本是做為兩個以上專案的容器使用。 該`ProjectCollection`元素用於指定要包含在範本中的專案。 有關多項目範本的詳細資訊,請參閱[如何:建立多專案範本](../ide/how-to-create-multi-project-templates.md)。

## <a name="example"></a>範例
 此示例顯示一個簡單的多專案根 *.vstemplate*檔案。 在這個範例中，範本包含兩個專案 `My Windows Application` 和 `My Class Library`。 `ProjectName` 項目的 `ProjectTemplateLink` 屬性會設定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的名稱，以指派此專案。 如果該`ProjectName`屬性不存在,*則 .vstemplate*檔案的名稱將用作專案名稱。

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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [如何:建立多項目範本](../ide/how-to-create-multi-project-templates.md)
