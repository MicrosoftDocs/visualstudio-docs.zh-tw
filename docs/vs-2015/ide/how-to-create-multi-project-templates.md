---
title: 如何：建立多專案範本 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1de155b71e82bb7561030cae2e1d0d4d777c9586
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668065"
---
# <a name="how-to-create-multi-project-templates"></a>如何：建立多專案的範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

多專案範本是做為兩個以上專案的容器使用。 從 [新增專案]**** 對話方塊建立，根據多專案範本的專案時，範本中的每個專案都會新增至解決方案。

 多專案範本必須包含下列項目，且壓縮成 .zip 檔案：

- 整個多專案範本的根 .vstemplate 檔案。 這個根 .vstemplate 檔案中包含 [新增專案]**** 對話方塊顯示的中繼資料，並指定何處可找到此範本中之專案的 .vstemplate 檔案。 這個檔案必須位於 .zip 檔案的根目錄。

- 包含完整專案範本所需之檔案的一或多個資料夾。 這包括專案的所有程式碼檔案，以及專案的 .vstemplate 檔案。

  例如，有兩個專案的多專案範本 .zip 檔，可能有下列檔案和目錄：

  MultiProjectTemplate.vstemplate

  \Project1\Project1.vstemplate

  \Project1\Project1.vbproj

  \Project1\Class.vb

  \Project2\Project2.vstemplate

  \Project2\Project2.vbproj

  \Project2\Class.vb

  多專案範本的根 .vstemplate 檔案與單一專案範本在下列幾點有所不同：

- `VSTemplate` 項目的 `Type` 屬性包含值 `ProjectGroup`。 例如：

  ```
  <VSTemplate Version="2.0.0" Type="ProjectGroup"
      xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
  ```

- `TemplateContent` 項目包含 `ProjectCollection` 項目，它具有一或多個 `ProjectTemplateLink` 項目，後者會定義所包含專案的 .vstemplate 檔案路徑。 例如：

  ```
  <TemplateContent>
      <ProjectCollection>
          <ProjectTemplateLink>
              Project1\Project1.vstemplate
          </ProjectTemplateLink>
          <ProjectTemplateLink>
              Project2\Project2.vstemplate
          </ProjectTemplateLink>
      </ProjectCollection>
  </TemplateContent>
  ```

  多專案範本的行為也與一般範本不同。 多專案範本具有下列獨特的特性：

- 多專案範本中的個別專案不能由 [新增專案]**** 對話方塊來指派名稱。 請改用 `ProjectTemplateLink` 項目上的 `ProjectName` 屬性來指定每個專案的名稱。 如需詳細資訊，請參閱下節的第一個範例。

- 多專案範本可以包含以不同語言撰寫的專案，但整個範本本身只能使用 `ProjectType` 項目放在一個分類。

### <a name="to-create-a-multi-project-template"></a>建立多專案範本

1. 建立要包含在多專案範本的專案。

2. 建立每個專案的 .vstemplate 檔案。 如需詳細資訊，請參閱[如何：建立專案範本](../ide/how-to-create-project-templates.md)。

3. 建立根 .vstemplate 檔案來包含多專案範本的中繼資料。 如需詳細資訊，請參閱下節的第一個範例。

4. 選取要包含在範本中的檔案和資料夾，在選取項目上按一下滑鼠右鍵，按一下 [傳送到]****，然後按一下 [壓縮的 (zipped) 資料夾]****。 檔案和資料夾即會壓縮成 .zip 檔案。

5. 將 .zip 範本檔放在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案範本目錄中。 此目錄預設為 \My Documents\Visual Studio <版本>** \Templates\ProjectTemplates\\。

## <a name="example"></a>範例
 這個範例將示範基本的多專案根 .vstemplate 檔案。 在這個範例中，範本包含兩個專案 `My Windows Application` 和 `My Class Library`。 `ProjectName` 項目的 `ProjectTemplateLink` 屬性會設定 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的名稱，以指派此專案。 如果 `ProjectName` 屬性不存在，則 .vstemplate 檔案的名稱會做為專案名稱。

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

## <a name="see-also"></a>另請參閱
 [建立專案和專案範本](../ide/creating-project-and-item-templates.md) [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)[如何：建立專案範本](../ide/how-to-create-project-templates.md) [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md) [SolutionFolder 元素 (Visual Studio 範本) ](../extensibility/solutionfolder-element-visual-studio-templates.md) [ (範本 Visual Studio ProjectTemplateLink 元素](../extensibility/projecttemplatelink-element-visual-studio-templates.md)) 
