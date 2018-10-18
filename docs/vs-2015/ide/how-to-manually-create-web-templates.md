---
title: 如何：手動建立網站範本 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d4496c42bfcc0baecd69770ff529c189d85da026
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220866"
---
# <a name="how-to-manually-create-web-templates"></a>如何：以手動方式建立網站範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

建立網站範本與建立其他種類的範本不同。 因為 Web 專案範本出現在 [新增網站] 對話方塊中，並且依程式語言分類 Web 專案項目，所以 .vstemplate 檔案必須將範本指定為網站範本，並識別程式設計語言。  
  
> [!NOTE]
>  網站範本必須包含使用 `Project` 項目的 `File` 屬性所指定的空 .webproj 檔案。 雖然 Web 專案不需要專案檔，但需要這個檔案，網站範本才能正常運作。  
  
### <a name="to-manually-create-a-web-template"></a>手動建立網站範本  
  
1.  建立 Web 專案。  
  
2.  修改或刪除專案中的檔案，或將新檔案新增至專案。  
  
3.  在與專案相同的目錄中，使用 .vstemplate 檔案副檔名來建立並儲存 XML 檔案。 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中，請不要將它新增至專案。  
  
4.  編寫 .vstemplate XML 檔案，以提供專案範本中繼資料。 如需詳細資訊，請參閱下節中的範例。  
  
5.  找出 .vstemplate 檔案中的 `ProjectType` 項目，並將文字值設為 `Web`。  
  
6.  在 `ProjectType` 項目後面，新增 `ProjectSubType` 項目，並將文字值設為範本的程式設計語言。 程式設計語言可以是下列其中一個值：  
  
    -   CSharp  
  
    -   VisualBasic  
  
     例如:   
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  在包含 .vstemplate 檔案的範本中選取檔案，並以滑鼠右鍵按一下選取範圍，再按一下 [傳送到]，然後按一下 [壓縮的 (zipped) 資料夾] 。 檔案即會壓縮成 .zip 檔案。  
  
8.  將 .zip 範本檔放在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案範本目錄中。 此檔案預設位於 \My Documents\Visual Studio <版本>\My Exported Templates\\。  
  
## <a name="example"></a>範例  
 下列範例示範 Web 專案範本的基本 .vstemplate 檔案。  
  
```  
<VSTemplate Version="2.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)



