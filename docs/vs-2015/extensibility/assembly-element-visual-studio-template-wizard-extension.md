---
title: 元件元素 (Visual Studio 範本 Wizard 擴充) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio Template Wizard Extension]
- <Assembly> element [Visual Studio Template Wizard Extension]
ms.assetid: 0c3dc280-1753-4ea2-a13c-d31d13b935b2
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d947c0f2996bcaaeff6c6dbf084151237f1fdb3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184725"
---
# <a name="assembly-element-visual-studio-template-wizard-extension"></a>組件項目 (Visual Studio 範本精靈擴充)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定執行介面之元件的名稱或強式名稱 `IWizard` 。  
  
 \<VSTemplate>  
\<WizardExtension>  
\<Assembly>  
  
## <a name="syntax"></a>語法  
  
```  
<Assembly>AssemblyName</Assembly>  
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|包含用於自訂範本 wizard 的註冊專案。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此文字會指定執行介面的元件 `IWizard` 。 此元件名稱必須指定為完整元件名稱。 例如： `MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom = null` 。  
  
## <a name="remarks"></a>備註  
 `Assembly` 是 `WizardExtension` 的必要子項目。  
  
## <a name="example"></a>範例  
 下列範例說明適用于 Windows 應用程式的標準專案範本中繼資料 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 。  
  
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
            <ProjectItem>Form1.cs</ProjectItem>  
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
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和專案範本](../ide/creating-project-and-item-templates.md)   
 [如何：搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)
