---
title: Visual Studio 範本資訊清單架構參考 |Microsoft Docs
description: 此架構參考描述針對 Visual Studio 專案或專案範本所產生 Visual Studio 範本資訊清單檔的格式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5f251b4511e2bff5bc20172e4018560205a378e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925833"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio 範本資訊清單架構參考
此架構描述為 Visual Studio 專案或專案範本產生的 Visual Studio 範本資訊清單 (*vstman*) 檔案的格式。 此架構也會描述範本的位置和其他相關資訊。

 ：因為有個別的專案和專案範本目錄，所以資訊清單絕不會有專案和專案範本的混合。

> [!IMPORTANT]
> 從 Visual Studio 2017 開始，可以使用此資訊清單。

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest 元素
 資訊清單的根項目。

### <a name="attributes"></a>屬性

- **Version**：代表範本資訊清單版本的字串。 必要。

- **地區** 設定：代表範本資訊清單地區設定或地區設定的字串。 地區設定值會套用至所有範本。 您必須針對每個地區設定使用不同的資訊清單。 選擇性。

### <a name="child-elements"></a>子元素

- **VSTemplateContainer** 選。

- **VSTemplateDir** 選。

### <a name="parent-element"></a>父元素
 無。

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 範本資訊清單元素的容器。 資訊清單有一個範本容器，適用于它所定義的每個範本。

### <a name="attributes"></a>屬性
 **VSTemplateType**：指定範本類型 (`"Project"` 、 `"Item"` 或) 的字串值 `"ProjectGroup"` 。 必要

### <a name="child-elements"></a>子元素

- **RelativePathOnDisk**：磁片上範本檔案的相對路徑。 這個位置也會在 [ **新增專案** ] 或 [ **新增** 專案] 對話方塊所顯示的範本樹狀結構中定義範本的位置。 針對部署為目錄和個別檔案的範本，此路徑會參考包含範本檔案的目錄。 針對部署為 *.zip* 檔案的範本，此路徑應該是 *.zip* 檔案的路徑。

- * * VSTemplateHeader：描述標頭的 [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) 元素。

### <a name="parent-element"></a>父元素
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 描述範本所在的目錄。 資訊清單可以包含多個 **VSTemplateDir** 專案，以提供目錄的當地語系化名稱和排序次序，以控制其在範本類別目錄樹狀結構中的外觀。

 由於其設計的緣故， **VSTemplateDir** 專案應該只出現在非地區設定指定的資訊清單中。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

- **RelativePath**：範本的路徑。 每個路徑只能有一個專案，因此第一個專案會贏得所有資訊清單。

- **LocalizedName**：指定當地語系化名稱的 **NameDescriptionIcon** 元素。 選擇性。

- **SortOrder**：指定排序次序的字串。 選擇性。

- **ParentFolderOverrideName**：父資料夾的覆寫名稱。 選擇性。 這個元素有一個 **name** 屬性，它是指定名稱的字串值。

### <a name="parent-element"></a>父元素
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 指定可能當地語系化範本的名稱和描述。 請參閱上述 **LocalizedName** 。

### <a name="attributes"></a>屬性

- **封裝**：指定封裝的字串值。 選擇性。

- **識別碼**：指定識別碼的字串值。 選擇性。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-element"></a>父元素
 **LocalizedName**

## <a name="examples"></a>範例
 下列程式碼是專案範本 *vstman* 檔的範例。

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

 下列程式碼是專案範本 *vstman* 檔的範例。

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
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
