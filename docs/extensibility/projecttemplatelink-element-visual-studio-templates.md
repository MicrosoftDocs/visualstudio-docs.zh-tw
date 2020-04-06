---
title: 專案範本連結元素(視覺工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6d402b6605f2e01a20d400c2c33573c686a1cdd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701812"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink 元素 (Visual Studio 範本)
在多項目範本中指定一個專案的 *.vstemplate*檔案的路徑。

 \<VStemplate \<\<>模板内容\<>项目集合>项目模板链接>\<- 或\<\<-範本>\<範本內容> 專案集合>\<解決方案資料夾>專案範本連結>

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
|`ProjectName`|選擇性屬性。<br /><br /> 指定多專案範本中每一個別專案的名稱。 "**新項目**"對話框無法為各個專案分配名稱。|
|`CopyParameters`|可將主群組範本中的所有變數複製到每一個連結的範本。<br /><br /> 在連結之範本中的參數會有前置詞 `"$ext_*$"`。 `$projectname$`例如,如果在父組範本中參數具有值**範例Project1,** 當連結範本輪到執行時,它將從父組範`$ext_projectname$``$projectname$`本獲取 參數 ,該參數是參數的副本。<br /><br /> 這樣可讓連結的範本共用某些只有在父群組範本中才方便建立的通用參數。<br /><br /> 這個屬性是選擇性的，如果未包含，則它會自動預設為 `false`。<br /><br /> 已在 Visual Studio 2013 Update 2 中引入。 要參考正確的產品版本,請參閱[Visual Studio 2013 SDK 更新 2 中提供的參考程式集](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb)。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|指定多專案範本的組織和內容。|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|將多專案範本中的專案分組。|

## <a name="text-value"></a>文字值
 需要文字值。

 此文字指定範本的 *.vstemplate*檔案的路徑。

## <a name="remarks"></a>備註
 多專案範本是做為兩個以上專案的容器使用。 該`ProjectTemplateLink`元素用於指定範本中一個專案的 *.vstemplate*檔案的位置。 多專案範本的 *.vstemplate*檔包含範本中`ProjectTemplateLink`每個專案的一個元素。 有關多項目範本的詳細資訊,請參閱[如何:建立多專案範本](../ide/how-to-create-multi-project-templates.md)。

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
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
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
