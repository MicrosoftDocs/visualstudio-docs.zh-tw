---
title: 預設名稱元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92bd29824cf1d3b91a7bdaa7220479c583ad0f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712311"
---
# <a name="defaultname-element-visual-studio-templates"></a>預設名稱元素(視覺化工作室範本)
指定可視化工作室專案系統在創建專案或專案時將生成的名稱。

 \<VStemplate>\<範本資料>\<預設名稱>

## <a name="syntax"></a>語法

```
<DefaultName>
    Default Project Name
</DefaultName>
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

 此文字指定項目或項目的預設名稱。

## <a name="remarks"></a>備註
  是選擇性元素。

 對於專案,此元素指定將專案存儲在磁碟上的目錄的名稱。 對於項,它指定源檔的檔名。

 建立項目或專案時,可以使用"**名稱"** 選項修改預設名稱,該選項可從 **「新專案**」對話框或 **「添加新專案」** 對話方塊中提供。

 如果不希望項目系統為專案或專案產生預設名稱,則將[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)元素`False`設定為 。

## <a name="example"></a>範例
 下面的範例演示了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]類的標準項範本的元數據。

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
