---
title: MaxFrameworkVersion 元素 （Visual Studio 範本） |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7be6bf858130310f3b7a13078482746edf74a65a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497082"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[MaxFrameworkVersion 元素 （Visual Studio 範本）](https://docs.microsoft.com/visualstudio/extensibility/maxframeworkversion-element-visual-studio-templates)。  
  
指定最大值範本所需的.NET framework 版本。 它會判斷範本是否會顯示在**範本**一節**新增專案**對話方塊中，根據值中選取**目標 Framework 版本**  方塊**加入新的專案** 對話方塊。  
  
 \<VSTemplate >  
 \<MaxFrameworkVersion >  
  
## <a name="syntax"></a>語法  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，以及定義如何顯示在**新的專案**或**加入新項目** 對話方塊。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此文字必須是範本所允許的.NET framework 的最高版本號碼。  
  
## <a name="remarks"></a>備註  
 `MaxFrameworkVersion` 是選擇性項目。 中的項目`TemplateData`.vstemplate 檔案的區段做為篩選條件**範本**一節**加入新的專案** 對話方塊。 其.NET Framework 需求的範本小於`MaxFrameworkVersion`項目值將會顯示，根據值中選取**目標 Framework 版本**方塊**加入新的專案** 對話方塊。 `MaxFrameworkVersion`應該省略項目，除非它是必要項，來為未使用較新的.NET Framework 版本時，不會再顯示在無意間造成範本。  
  
## <a name="example"></a>範例  
 下列範例說明一種標準的中繼資料[!INCLUDE[csprcs](../includes/csprcs-md.md)]類別樣板。  
  
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
  
 在此範例中，最大版本的.NET Framework 所需的範本，以表示`MaxFrameworkVersion`，為 3.5。 只有當您選取 3.0 或 3.5 中的時，將會顯示上述的範本**目標 Framework 版本**方塊中**加入新的專案** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)

