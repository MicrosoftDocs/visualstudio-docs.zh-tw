---
title: 建立網站範本
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 245b20dd9cad465129d6c79c38e53b6379c2c09c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591004"
---
# <a name="how-to-manually-create-web-templates"></a>如何：手動建立網站範本

建立網站範本與建立其他種類的範本不同。 由於 Web 專案範本顯示在 **"添加新網站"** 對話方塊中，並且 Web 專案項按程式設計語言進行分類，*因此 vstemplate*檔必須指定範本為 Web 範本並標識程式設計語言。

> [!NOTE]
> Web 範本必須包含空 *.webproj*檔，並且必須在元素`File`屬性中的*vstemplate*檔中引用該檔。 `Project` 雖然 Web 專案不需要 *.proj* 專案檔，但網站範本要正確運作就必須建立此虛設常式檔案。

## <a name="to-manually-create-a-web-template"></a>手動建立網站範本

1. 建立 Web 專案。

2. 修改或刪除專案中的檔案，或將新檔案新增至專案。

3. 創建 XML 檔，並將其與*vstemplate*檔案名副檔名一起保存在與專案相同的目錄中。 在 Visual Studio 中，請不要將它新增至專案。

4. 編輯*vstemplate* XML 檔以提供專案範本中繼資料。 如需詳細資訊，請參閱[後續範例](#example)。

5. 在`ProjectType` *vstemplate*檔中查找元素，並將文本值設置為`Web`。

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

7. 選擇範本中的檔（包括*vstemplate*檔），按右鍵所選內容，然後選擇"**發送到** > **壓縮（壓縮）"資料夾**。 檔被壓縮到 *.zip*檔中。

8. 將 *.zip*範本檔放在視覺化工作室專案範本目錄中。 預設情況下，此目錄是 *%USERPROFILE%%*文檔_視覺\<工作室\>版本 \ProjectTemplates*。

## <a name="example"></a>範例

下面的示例顯示了 Web 專案範本的基本*vstemplate*檔：

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

- [創建專案和專案範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本結構描述參考 (擴充性)](../extensibility/visual-studio-template-schema-reference.md)
