---
title: 建立網站範本
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d121d9b970d8012aaf177c0a232cd21f6fe85d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645821"
---
# <a name="how-to-manually-create-web-templates"></a>如何：手動建立網站範本

建立網站範本與建立其他種類的範本不同。 因為 Web 專案範本出現在 [加入新網站] 對話方塊中，並且依程式語言分類 Web 專案項目，所以 *vstemplate* 檔案必須將範本指定為網站範本，並識別程式設計語言。

> [!NOTE]
> 網站範本必須包含空的 *webproj* 檔案，而且 *.vstemplate* 檔案必須在 `Project` 元素的 `File` 屬性中參考它。 雖然 Web 專案不需要 *.proj* 專案檔，但網站範本要正確運作就必須建立此虛設常式檔案。

## <a name="to-manually-create-a-web-template"></a>手動建立網站範本

1. 建立 Web 專案。

2. 修改或刪除專案中的檔案，或將新檔案新增至專案。

3. 在與專案相同的目錄中，使用 *vstemplate* 副檔名來建立並儲存 XML 檔案。 在 Visual Studio 中，請不要將它新增至專案。

4. 編輯 *vstemplate* XML 檔案，以提供專案範本中繼資料。 如需詳細資訊，請參閱[後續範例](#example)。

5. 找出 *vstemplate* 檔案中的 `ProjectType` 元素，並將文字值設為 `Web`。

6. 在 `ProjectType` 項目後面，新增 `ProjectSubType` 項目，並將文字值設為範本的程式設計語言。 程式設計語言可以是下列其中一個值：

   - CSharp
   - VisualBasic

     例如:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. 在包含 *vstemplate* 檔案的範本中選取檔案，並以滑鼠右鍵按一下選取項目，選擇 [傳送到] > [壓縮的 (zipped) 資料夾]。 檔案即會壓縮成 *.zip* 檔案。

8. 將 *.zip* 範本檔放在 Visual Studio 專案範本目錄中。 此目錄預設為 *%USERPROFILE%\Documents\Visual Studio \<版本\>\ProjectTemplates*。

## <a name="example"></a>範例

下列範例示範 Web 專案範本的基本 *vstemplate* 檔案：

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple web template</Description>
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

## <a name="see-also"></a>請參閱

- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md)
