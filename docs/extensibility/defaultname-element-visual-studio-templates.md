---
title: DefaultName 項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: 15
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6a20bd878e9c6f85e03ff0738ed2a92d274f6232
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName 項目 (Visual Studio 範本)
在建立時，請指定 Visual Studio 專案系統將產生的專案或項目的名稱。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<DefaultName >  
  
## <a name="syntax"></a>語法  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此文字會指定預設名稱的專案或項目。  
  
## <a name="remarks"></a>備註  
 `DefaultName` 是選擇性項目。  
  
 專案中，這個項目會指定儲存在磁碟專案目錄的名稱。 項目，它會指定來源檔案的檔案名稱。  
  
 當您建立專案或項目時，您可以修改預設名稱使用**名稱**選項，可從 **新專案**對話方塊或**加入新項目**對話方塊。  
  
 若不想使用專案系統產生的專案或項目的預設名稱，然後設定[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)元素`False`。  
  
## <a name="example"></a>範例  
 下列範例說明標準項目範本的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]類別。  
  
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
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)