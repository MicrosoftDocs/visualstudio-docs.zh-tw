---
title: FullClassName 項目 （Visual Studio 範本精靈擴充） |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7de1984a10d80e5136a9a01a1e1dae8ee5226f9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796762"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>FullClassName 項目 (Visual Studio 範本精靈擴充)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

實作的類別完整的名稱`IWizard`介面。  
  
 \<VSTemplate >  
 \<WizardExtension >  
 ...  
 \<FullClassName >  
  
## <a name="syntax"></a>語法  
  
```  
<FullClassName>ClassName</FullClassName>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|包含自訂範本精靈 的註冊項目。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此文字會指定實作的類別`IWizard`介面。 指定的類別必須存在於所指定的組件[組件](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)項目。  
  
## <a name="remarks"></a>備註  
 `FullClassName` 是 `WizardExtension` 的必要子項目。  
  
## <a name="example"></a>範例  
 下列範例說明的標準專案範本的中繼資料[!INCLUDE[csprcs](../includes/csprcs-md.md)]Windows 應用程式。  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [如何︰搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)

