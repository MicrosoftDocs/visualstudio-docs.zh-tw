---
title: 可視化工作室範本清單架構參考 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697977"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>視覺化工作室範本清單架構參考
此架構描述為 Visual Studio 專案或專案範本生成的可視化工作室範本清單 *(.vstman*) 檔案的格式。 架構還描述了該範本的位置和其他相關信息。

 :因為有單獨的專案和專案範本目錄,因此清單不應混合使用物料和專案範本。

> [!IMPORTANT]
> 此清單可從 Visual Studio 2017 開始使用。

## <a name="vstemplatemanifest-element"></a>VSTemplate 清單項目
 清單的根元素。

### <a name="attributes"></a>屬性

- **版本**:表示範本清單版本的字串。 必要。

- **區域設定**:表示範本清單區域設定或區域設置的字串。 區域設置值適用於所有範本。 您必須為每個區域設置使用單獨的清單。 選擇性。

### <a name="child-elements"></a>子元素

- **VSTemplate 容器**選。

- **VSTemplateDir**選。

### <a name="parent-element"></a>父元素
 無。

## <a name="vstemplatecontainer"></a>VSTemplate 容器
 範本清單元素的容器。 清單為其定義的每個範本有一個範本容器。

### <a name="attributes"></a>屬性
 **VSTemplate 類型**:指定樣本型`"Project"`態`"Item"``"ProjectGroup"`( 或的字串值)。 必要

### <a name="child-elements"></a>子元素

- **相對路徑磁碟**:磁碟上範本檔的相對路徑。 此位置還定義範本在新**專案**或「**新項目**」對話框中顯示的範本樹中的位置。 對於作為目錄和單個檔部署的範本,此路徑引用包含範本檔的目錄。 對於作為 *.zip*檔部署的範本,此路徑應該是 *.zip*文件的路徑。

- *VSTemplate 標題:描述標頭的[範本資料](../extensibility/templatedata-element-visual-studio-templates.md)元素。

### <a name="parent-element"></a>父元素
 **VSTemplate 清單**

## <a name="vstemplatedir"></a>VSTemplateDir
 描述範本所在的目錄。 清單可以包含多個**VSTemplateDir**條目,以提供當地語系化的名稱和排序,以便目錄控制其在範本類別樹中的外觀。

 由於其設計 **,VSTemplateDir**條目應只出現在非區域設置指定的清單中。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

- **相對路徑**:範本的路徑。 每個路徑只能有一個條目,因此第一個條目將贏得所有清單。

- **本地化名稱**:指定本地化名稱**的名稱描述元素**。 選擇性。

- **排序順序**:指定排序順序的字串。 選擇性。

- **父資料夾覆蓋名稱**:父資料夾的重寫名稱。 選擇性。 此元素具有**Name**屬性,該屬性是指定名稱的字串值。

### <a name="parent-element"></a>父元素
 **VSTemplate 清單**

## <a name="namedescriptionicon"></a>名稱描述圖示
 指定名稱和說明,可能用於本地化範本。 請參考上面**的本地化名稱**。

### <a name="attributes"></a>屬性

- **套件**:指定套件的字串值。 選擇性。

- **ID**:指定 ID 的字串值。 選擇性。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-element"></a>父元素
 **本地化名稱**

## <a name="examples"></a>範例
 以下代碼是專案範本 *.vstman*檔的範例。

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

 以下代碼是項範本 *.vstman*檔的範例。

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
