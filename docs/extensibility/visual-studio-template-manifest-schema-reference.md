---
title: Visual Studio 範本資訊清單結構描述參考 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fa5d123048b819c2b0b92951582bd9348cbdbab6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713161"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio 範本資訊清單結構描述參考
此結構描述會描述 Visual Studio 範本資訊清單的格式 (*.vstman*) Visual Studio 專案或項目範本所產生的檔案。 結構描述也會說明的位置和範本的其他相關資訊。

 :因為有個別的項目和專案範本目錄中，資訊清單應該永遠不會有混合的項目和專案範本。

> [!IMPORTANT]
>  使用 Visual Studio 2017 中啟動此資訊清單。

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest 項目
 資訊清單的根項目。

### <a name="attributes"></a>屬性

-   **版本**:字串，表示範本資訊清單版本。 必要項。

-   **地區設定**:字串，表示範本資訊清單的地區設定的地區設定。 地區設定值套用至所有範本。 您必須使用不同的資訊清單，每個地區設定。 選擇性。

### <a name="child-elements"></a>子元素

-   **VSTemplateContainer**選擇性。

-   **VSTemplateDir**選擇性。

### <a name="parent-element"></a>父項目
 無。

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 樣板容器的資訊清單項目。 資訊清單有一個範本容器，它會定義每個範本。

### <a name="attributes"></a>屬性
 **VSTemplateType**:字串值，指定範本類型 (`"Project"`， `"Item"`，或`"ProjectGroup"`)。 必要

### <a name="child-elements"></a>子元素

-   **RelativePathOnDisk**:在磁碟上的範本檔案的相對路徑。 此位置也會定義範本的位置在範本樹狀目錄中所示**新的專案**或是**新項目**對話方塊。 如需部署為目錄和個別檔案的範本，此路徑會參考包含範本檔案的目錄。 針對做為部署範本 *.zip*檔案，這個路徑應該是路徑 *.zip*檔案。

-   **VSTemplateHeader:A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)描述標頭的項目。

### <a name="parent-element"></a>父項目
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 描述範本所在的目錄。 資訊清單可以包含多個**VSTemplateDir**提供當地語系化的名稱和排序順序的目錄來控制它們出現在範本類別目錄樹狀結構的項目。

 因為它們的設計，而**VSTemplateDir**只能在非地區設定指定的資訊清單中的項目應該會出現。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

-   **RelativePath**:範本的路徑。 因此第一個會贏得的所有資訊清單時，則可以是每個路徑，只有一個項目。

-   **LocalizedName**:A **NameDescriptionIcon**項目，指定當地語系化的名稱。 選擇性。

-   **SortOrder**:字串，指定排序次序。 選擇性。

-   **ParentFolderOverrideName**:覆寫的父資料夾的名稱。 選擇性。 這個項目具有**名稱**屬性，也就是指定名稱的字串值。

### <a name="parent-element"></a>父項目
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 指定的名稱和描述，可能是當地語系化的範本。 請參閱**LocalizedName**上方。

### <a name="attributes"></a>屬性

-   **封裝**:字串值，指定套件。 選擇性。

-   **識別碼**:字串值，指定識別碼。 選擇性。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-element"></a>父項目
 **LocalizedName**

## <a name="examples"></a>範例
 下列程式碼是專案範本的範例 *.vstman*檔案。

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 下列程式碼是項目範本的範例 *.vstman*檔案。

```xml
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```