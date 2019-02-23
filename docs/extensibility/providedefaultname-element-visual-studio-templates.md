---
title: ProvideDefaultName 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 056403fd0f1c90f53105c84f30fc2be2383900bf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696853"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName 項目 （Visual Studio 範本）
指定是否[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案系統會產生的範本中的預設名稱**加入新項目**或是**新專案** 對話方塊。

 \<VSTemplate> \<TemplateData> \<ProvideDefaultName>

## <a name="syntax"></a>語法

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須是`true`或`false`，指出是否要產生的範本中的預設名稱**加入新項目**或是**新專案** 對話方塊。

## <a name="remarks"></a>備註
 `ProvideDefaultName` 是選擇性項目。 預設值為 `true`。

 如果`ProvideDefaultName`項目是`false`，則**名稱**的方塊**加入新項目**並**新專案**對話方塊會包含值`<Enter_name>`。

 使用[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)來指定專案的預設名稱，或項目中的項目**加入新項目**並**新專案**對話方塊。 時的值`ProvideDefaultName`項目`true`，省略`DefaultName`專案項目範本的名稱，也就是從值對話方塊方塊中填入[名稱](../extensibility/name-element-visual-studio-templates.md)項目。

## <a name="example"></a>範例
 下列程式碼範例會設定`ProvideDefaultName`項目`false`。

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
