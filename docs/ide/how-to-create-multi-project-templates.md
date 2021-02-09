---
title: 建立多重專案範本
description: 瞭解如何在 Visual Studio 中建立多專案範本，這些範本可同時作為許多專案的容器。
ms.custom: SEO-VS-2020
ms.date: 04/17/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: c4cfc7f51999056379acd73ec7ec3933c1f31a51
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875402"
---
# <a name="how-to-create-multi-project-templates"></a>如何：建立多專案範本

多專案範本是做為兩個以上專案的容器使用。 當您根據多專案範本建立專案時，範本中的每個專案都會新增至方案。

多專案範本有兩個或更多的專案範本，以及一個 **ProjectGroup** 類型的根範本。

多專案範本的行為與單一專案範本不同。 它們具有下列獨特的特性：

- 當範本用於建立新專案時，多專案範本中的個別專案不能指派名稱。 相反地，在 vstemplate 檔案的 **ProjectTemplateLink** 項目上使用 **ProjectName** 屬性，指定每個專案的名稱。

- 多專案範本可以包含不同語言的專案，但整個範本本身只能放在一個類別中。 在 vstemplate 檔案的 **ProjectType** 項目中指定範本類別。

多專案範本必須包含下列項目，且壓縮成 *.zip* 檔案：

- 整個多專案範本的根 *.vstemplate* 檔案。 此根 *vstemplate* 檔案包含您建立新專案所在之對話方塊中顯示的中繼資料。 也會指定何處可找到範本中專案的 *vstemplate* 檔案。 這個檔案必須位於 *.zip* 檔案的根目錄。

- 包含完整專案範本所需之檔案的兩個或多個資料夾。 這些資料夾包括專案的所有程式碼檔案，以及專案的 *.vstemplate* 檔案。

例如，有兩個專案的多專案範本 *.zip* 檔，可能有下列檔案和目錄：

- *MultiProjectTemplate.vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.vb*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.vb*

多專案範本的根 *.vstemplate* 檔案與單一專案範本的差異如下：

- **VSTemplate** 項目的 **Type** 屬性具有 **ProjectGroup** 值，而非 **Project**。 例如：

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- **TemplateContent** 項目包含 **ProjectCollection** 項目，它具有一或多個 **ProjectTemplateLink** 項目可定義所包含專案的 vstemplate 檔案路徑。 例如：

    ```xml
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink>
                Project1\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink>
                Project2\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
    ```

> [!TIP]
> 如果您只希望多專案範本顯示在新的 [專案] 對話方塊中而不是它包含的個別專案中，請將內部範本標記為 [[隱藏]](../extensibility/hidden-element-visual-studio-templates.md)。 例如：
>
> ```xml
> <VSTemplate Type="Project" ... >
>     <TemplateData>
>         ...
>         <Hidden>true</Hidden>
>     </TemplateData>
>     ...
> </VSTemplate>
> ```

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>從現有的解決方案中建立多專案範本

1. 建立解決方案並新增兩個或多個專案。

2. 自訂專案，直到它們可以匯出成範本為止。

   > [!TIP]
   > 如果您使用[範本參數](template-parameters.md)且您想要從父代範本參考變數，請在參數名稱加上前置詞 `ext_`。 例如： `$ext_safeprojectname$` 。 此外，請將 **ProjectTemplateLink** 元素的 **CopyParameters** 屬性設定為 **true**。
   >
   > ```xml
   > <ProjectTemplateLink ProjectName="MyProject" CopyParameters="true">...</ProjectTemplateLink>
   > ```

3. 選擇 [ **專案** ] 功能表上的 [ **匯出範本**]。

   [ **匯出範本]** 隨即開啟。

4. 在 [選擇範本類型] 頁面上，選取 [專案範本]。 選取其中一個您想要匯出至範本的專案，然後選擇 [下一步]。 (對解決方案中的每個專案重複這些步驟)。

5. 在 [選取範本選項] 頁面上，輸入範本的名稱和選擇性描述、圖示和預覽影像。 選擇 [完成]。

   專案會匯出為 *.zip* 檔案，放在指定的輸出位置。

   > [!NOTE]
   > 每個專案必須分別匯出成範本，所以請在解決方案中為每個專案重複上述的這些步驟。

6. 建立範本目錄，每個專案都有子目錄。

7. 將每個專案的 *.zip* 檔案內容解壓縮至您建立的對應子目錄。

8. 在基底目錄中，建立檔案副檔名為 *.vstemplate* 的 XML 檔案。 此檔案包含多專案範本的中繼資料。 請參閱接下來的檔案結構範例。 請務必指定每個專案的 *.vstemplate* 檔案的相對路徑。

9. 選取基底目錄中的所有檔案，然後從滑鼠右鍵功能表或操作功能表中，選擇 [**傳送到**  >  **壓縮 (壓縮的) 資料夾**。

   檔案和資料夾即會壓縮成 *.zip* 檔案。

10. 將 *.zip* 檔案複製到使用者專案範本目錄中。 此目錄預設為 *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates*。

11. 在 [Visual Studio 中 **，選擇 [** 檔案  >  **新**  >  **專案**]，並確認範本是否出現。

## <a name="two-project-example"></a>雙專案範例

此範例顯示基本的多專案根 *.vstemplate* 檔案。 在本範例中，範本有兩個專案：**My Windows Application** 和 **My Class Library**。 **ProjectTemplateLink** 項目上的 **ProjectName** 屬性會指定要提供給專案的名稱。

> [!TIP]
> 如果未指定 **ProjectName** 屬性，則請使用 vstemplate 檔案的名稱作為專案名稱。

```xml
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

## <a name="example-with-solution-folders"></a>具有解決方案資料夾的範例

本範例使用 **SolutionFolder** 項目將專案分割為兩個群組：**Math Classes** 和 **Graphics Classes**。 範本有四個專案，每個解決方案資料夾各包含兩個專案。

```xml
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

- [建立專案和專案範本](../ide/creating-project-and-item-templates.md)
- [如何：建立專案範本](../ide/how-to-create-project-templates.md)
- [Visual Studio 範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md)
- [ (Visual Studio 範本的 SolutionFolder 元素) ](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [ (Visual Studio 範本的 ProjectTemplateLink 元素) ](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
