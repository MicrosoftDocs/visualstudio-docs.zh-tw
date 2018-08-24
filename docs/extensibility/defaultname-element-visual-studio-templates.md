---
title: DefaultName 項目 （Visual Studio 範本） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03513b786c17e5bef3d8fa1fff79c1c3e73fe6a0
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500315"
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName 項目 （Visual Studio 範本）
建立時，請指定 Visual Studio 專案系統會產生的專案或項目的名稱。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<DefaultName >  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此文字會指定預設名稱的專案或項目。  
  
## <a name="remarks"></a>備註  
 `DefaultName` 是選擇性項目。  
  
 針對專案，這個元素會指定儲存在磁碟的專案目錄的名稱。 項目，它會指定原始程式檔的檔案名稱。  
  
 當您建立專案或項目時，您可以使用下列方法修改預設名稱**名稱**選項，可從其中**新增專案** 對話方塊或**加入新項目** 對話方塊。  
  
 如果不想使用的專案系統產生的專案或項目的預設名稱，然後設定[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)項目`False`。  
  
## <a name="example"></a>範例  
 下列範例說明的標準項目範本的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]類別。  
  
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
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)