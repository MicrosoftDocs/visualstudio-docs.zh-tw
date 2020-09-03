---
title: " (Visual Studio 範本的 DefaultName 元素) |Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bc3a18c47b78a312f3bca3762cc4ff3d658a70e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185293"
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定 Visual Studio 專案系統在建立專案或專案時，將為其產生的名稱。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<DefaultName>  
  
## <a name="syntax"></a>語法  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此文字會指定專案或專案的預設名稱。  
  
## <a name="remarks"></a>備註  
  是選擇性元素。  
  
 若為專案，這個專案會指定將專案儲存在磁片上的目錄名稱。 針對專案，它會指定原始程式檔的檔案名。  
  
 當您建立專案或專案時，可以使用 [**新增專案**] 對話方塊或 [**加入新**專案] 對話方塊中所提供的 [**名稱**] 選項來修改預設名稱。  
  
 如果您不想讓專案系統產生專案或專案的預設名稱，請將 [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) 元素設定為 `False` 。  
  
## <a name="example"></a>範例  
 下列範例說明類別標準專案範本的中繼資料 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 。  
  
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
 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
