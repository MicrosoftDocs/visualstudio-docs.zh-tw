---
title: 建立網站範本
description: 瞭解如何以手動方式建立網站範本，並識別範本所使用的程式設計語言。
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 430faba462075335bbc8a3aa6e89f1c7f348ffb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924635"
---
# <a name="how-to-manually-create-web-templates"></a>如何：手動建立網站範本

建立網站範本與建立其他種類的範本不同。 由於 Web 專案範本會出現在 [ **加入新網站** ] 對話方塊中，而 Web 專案專案會依程式設計語言分類，因此 *.vstemplate* 檔案必須將範本指定為 web 範本，並識別程式設計語言。

> [!NOTE]
> Web 範本必須包含空的 *.webproj* 檔案，而且必須在專案屬性的 *.vstemplate* 檔案中參考該檔案 `File` `Project` 。 雖然 Web 專案不需要 *.proj* 專案檔，但網站範本要正確運作就必須建立此虛設常式檔案。

## <a name="to-manually-create-a-web-template"></a>手動建立網站範本

1. 建立 Web 專案。

2. 修改或刪除專案中的檔案，或將新檔案新增至專案。

3. 使用 *.vstemplate* 副檔名來建立 XML 檔案，並將它儲存在與專案相同的目錄中。 在 Visual Studio 中，請不要將它新增至專案。

4. 編輯 *.Vstemplate* XML 檔案，以提供專案範本中繼資料。 如需詳細資訊，請參閱[後續範例](#example)。

5. `ProjectType`在 *.vstemplate* 檔案中尋找元素，並將文字值設為 `Web` 。

6. 在 `ProjectType` 項目後面，新增 `ProjectSubType` 項目，並將文字值設為範本的程式設計語言。 程式設計語言可以是下列其中一個值：

   - CSharp
   - VisualBasic

     例如：

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. 在您的範本中選取檔案 (這包括 *.vstemplate* 檔案) 、以滑鼠右鍵按一下選取範圍，然後選擇 [**傳送到**  >  **壓縮的 (壓縮的) 資料夾**]。 檔案會壓縮成 *.zip* 檔案。

8. 將 *.zip* 範本檔放在 Visual Studio 專案範本目錄中。 此目錄預設為 *%USERPROFILE%\Documents\Visual Studio \<Version\> \ProjectTemplates*。

## <a name="example"></a>範例

下列範例顯示 Web 專案範本的基本 *.vstemplate* 檔案：

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

## <a name="see-also"></a>另請參閱

- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md)
