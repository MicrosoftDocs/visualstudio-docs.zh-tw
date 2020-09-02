---
title: " (Visual Studio 範本的 MaxFrameworkVersion 元素) |Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194322"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定範本所需之 .NET Framework 的最大版本。 它會根據 [**加入新專案**] 對話方塊的 [**目標 Framework 版本**] 方塊中所選取的值，判斷範本是否顯示在 [**加入新專案**] 對話方塊的 [**範本**] 區段中。  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
## <a name="syntax"></a>語法  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [ **新增專案** ] 或 [ **加入新** 專案] 對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此文字必須是範本所允許之 .NET Framework 的最高版本號碼。  
  
## <a name="remarks"></a>備註  
  是選擇性元素。 .Vstemplate 檔案之區段中的專案會當做 `TemplateData` [**加入新專案**] 對話方塊的 [**範本**] 區段的篩選準則。 `MaxFrameworkVersion`根據在 [**加入新專案**] 對話方塊的 [**目標 Framework 版本**] 方塊中選取的值，只會顯示其 .NET Framework 需求小於專案值的範本。 `MaxFrameworkVersion`除非必要，否則應該省略元素，如此一來，當範本與較新版本的 .NET Framework 搭配使用時，不會不慎出現範本。  
  
## <a name="example"></a>範例  
 下列範例說明標準類別範本的中繼資料 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 在此範例中，範本所需 .NET Framework 的最大版本 `MaxFrameworkVersion` 為3.5。 只有當您在 [**加入新專案**] 對話方塊的 [**目標 Framework 版本**] 方塊中選取 [3.0] 或 [3.5] 時，才會顯示上述範本。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
