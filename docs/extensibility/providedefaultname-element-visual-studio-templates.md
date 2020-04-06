---
title: 提供預設名稱元素(視覺工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 192716198f605a5f6b4f62730e84dcf83b4229cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701710"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>提供預設名稱元素(視覺化工作室樣本)
指定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案系統是否會在「**新增新專案**」或「**新項目**」對話框中為範本生成預設名稱。

 \<>提供默认\<名稱>>\<的 VStemplate>模板数据

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須為`true``false`或 ,指示是否在 **「新增新專案**」或 **「新項目**」對話框中為範本生成預設名稱。

## <a name="remarks"></a>備註
  是選擇性元素。 預設值是 `true`。

 如果`ProvideDefaultName``false`元素為,**則「 新增新項目**」 與 **「新項目」** 對話框`<Enter_name>`**的名稱**。

 使用[預設名稱](../extensibility/defaultname-element-visual-studio-templates.md)元素在 **「新增新專案和****新項目**」對話框中指定專案或項目的預設名稱。 當`ProvideDefaultName`元素的值`true`為 時`DefaultName`,專案 元素的省略會用範本的名稱填充對話框,即[名稱](../extensibility/name-element-visual-studio-templates.md)元素中的值。

## <a name="example"></a>範例
 以下代碼範例將`ProvideDefaultName`元素設定`false`到 。

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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
