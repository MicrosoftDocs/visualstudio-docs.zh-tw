---
title: "如何：建立多專案範本 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ac7701e3e4dc11bc5634436c3e6f831f6711e514
ms.sourcegitcommit: 03a74d29a1e0584ff4808ce6c9e812b51e774905
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2018
---
# <a name="how-to-create-multi-project-templates"></a>如何：建立多專案的範本
多專案範本是做為兩個以上專案的容器使用。 從 [新增專案] 對話方塊建立，根據多專案範本的專案時，範本中的每個專案都會新增至解決方案。  

 多專案範本是兩個以上之專案範本與類型 `ProjectGroup` 的根範本。

 多專案範本的行為也與一般範本不同。 多專案範本具有下列獨特的特性：  
  
-   多專案範本中的個別專案不能由 [新增專案] 對話方塊來指派名稱。 請改用 `ProjectTemplateLink` 項目上的 `ProjectName` 屬性來指定每個專案的名稱。 如需詳細資訊，請參閱下節的第一個範例。  
  
-   多專案範本可以包含以不同語言撰寫的專案，但整個範本本身只能使用 `ProjectType` 項目放在一個分類。  
  
### <a name="to-create-a-multi-project-template"></a>建立多專案範本  
  
1.  建立要包含在多專案範本中的專案：
    1.  建立專案。  
  
    > [!NOTE]
    >  在命名將會是範本來源的專案時，請您只使用有效的識別項字元。 從名稱含有無效字元之專案所匯出的範本，可能會導致未來根據該範本的專案發生編譯錯誤。 如需有效識別項字元的詳細資訊，請參閱[宣告項目名稱](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)。  
  
    2.  編輯專案，直到它準備好匯出成範本。  
  
    3.  適當地編輯程式碼檔案，指出要執行參數取代的地方。 如需參數取代的詳細資訊，請參閱[如何：替代範本中的參數](../ide/how-to-substitute-parameters-in-a-template.md)。  
  
    4.  按一下 [專案] 功能表上的 [匯出範本]。 [匯出範本精靈] 隨即開啟。  
  
    5.  按一下 [專案範本]。  
  
    6.  如果您目前的方案中有多個專案，請選取您想要匯出至範本的專案。  
  
    7.  按 [ **下一步**]。  
  
    8.  選取範本的圖示和預覽影像。 這些會出現在 [新增專案] 對話方塊。  
  
    9. 輸入範本名稱及描述。  
  
    10. 按一下 [ **完成**]。 您的專案會匯出成 .zip 檔案並放在指定的輸出位置，且如果選取，則會匯入到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
2.  將 .vstemplate 檔案從產生的 ZIP 檔案解壓縮到與用來匯出範本之專案檔相同的目錄。

3.  建立根 .vstemplate 檔案來包含多專案範本的中繼資料。 如需詳細資訊，請參閱下節的第一個範例。  
  
4.  選取要包含在範本中的檔案和資料夾，在選取項目上按一下滑鼠右鍵，按一下 [傳送到]，然後按一下 [壓縮的 (zipped) 資料夾]。 檔案和資料夾即會壓縮成 .zip 檔案。  
  
> [NOTE!] 多專案範本必須包含下列項目，且壓縮成 .zip 檔案：  
>   
> -   整個多專案範本的根 .vstemplate 檔案。 這個根 .vstemplate 檔案中包含 [新增專案] 對話方塊顯示的中繼資料，並指定何處可找到此範本中之專案的 .vstemplate 檔案。 這個檔案必須位於 .zip 檔案的根目錄。  
>   
> -   包含完整專案範本所需之檔案的一或多個資料夾。 這包括專案的所有程式碼檔案，以及專案的 .vstemplate 檔案。  
>   
> 例如，有兩個專案的多專案範本 .zip 檔，可能有下列檔案和目錄：  
>   
>  MultiProjectTemplate.vstemplate  
>   
>  \Project1\Project1.vstemplate  
>   
>  \Project1\Project1.vbproj  
>   
>  \Project1\Class.vb  
>   
>  \Project2\Project2.vstemplate  
>   
>  \Project2\Project2.vbproj  
>   
>  \Project2\Class.vb  
>   
>  多專案範本的根 .vstemplate 檔案與單一專案範本在下列幾點有所不同：  
>   
> -   `VSTemplate` 項目的 `Type` 屬性包含值 `ProjectGroup`。 例如：  
>   
>     ```  
>     <VSTemplate Version="2.0.0" Type="ProjectGroup"  
>         xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
>     ```  
>   
> -   `TemplateContent` 項目包含 `ProjectCollection` 項目，它具有一或多個 `ProjectTemplateLink` 項目，後者會定義所包含專案的 .vstemplate 檔案路徑。 例如:   
>   
>     ```  
>     <TemplateContent>  
>         <ProjectCollection>  
>             <ProjectTemplateLink>  
>                 Project1\Project1.vstemplate  
>             </ProjectTemplateLink>  
>             <ProjectTemplateLink>  
>                 Project2\Project2.vstemplate  
>             </ProjectTemplateLink>  
>         </ProjectCollection>  
>     </TemplateContent>  
>     ```  
>   
  
5.  將 .zip 範本檔放在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案範本目錄中。 此目錄預設為 \My Documents\Visual Studio <版本>\Templates\ProjectTemplates\\。  
  
## <a name="example"></a>範例  
 這個範例將示範基本的多專案根 .vstemplate 檔案。 在這個範例中，範本包含兩個專案 `My Windows Application` 和 `My Class Library`。 `ProjectName` 項目的 `ProjectTemplateLink` 屬性會設定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的名稱，以指派此專案。 如果 `ProjectName` 屬性不存在，則 .vstemplate 檔案的名稱會做為專案名稱。  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="example"></a>範例  
 這個範例會使用 `SolutionFolder` 項目將專案分成兩個群組，也就是 `Math Classes` 和 `Graphics Classes`。 範本包含四個專案，每個方案資料夾各包含兩個專案。  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>請參閱  
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [如何：建立專案範本](../ide/how-to-create-project-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder 項目 (Visual Studio 範本)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink 元素 (Visual Studio 範本)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
