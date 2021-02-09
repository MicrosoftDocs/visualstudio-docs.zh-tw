---
title: Item 項目 (MSBuild) | Microsoft Docs
description: 瞭解 MSBuild 如何使用 Item 元素來包含使用者定義的專案及其中繼資料。 每個專案都必須是 ItemGroup 元素的子系。
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59a0660bb78e966150a6ef8d17dc24512a901a26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913942"
---
# <a name="item-element-msbuild"></a>Item 項目 (MSBuild)

包含使用者定義的項目及其中繼資料。 MSBuild 專案中使用的每個專案都必須指定為元素的子系 `ItemGroup` 。

\<Project>
\<ItemGroup>
\<Item>

## <a name="syntax"></a>Syntax

```xml
<Item Include="*.cs"
        Exclude="MyFile.cs"
        Condition="'String A'=='String B'">
    <ItemMetadata1>...</ItemMetadata1>
    <ItemMetadata2>...</ItemMetadata2>
</Item>
```

## <a name="specify-metadata-as-attributes"></a>將中繼資料指定為屬性

在 MSBuild 15.1 或更新版本中，如果任何中繼資料的名稱未與目前的屬性清單衝突，您即可選擇將其表示為屬性。

例如，若要指定 NuGet 套件清單，您通常會使用類似下列的語法。

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

不過，您現在可以將 `Version` 中繼資料作為屬性傳遞，如下列語法所示：

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />
</ItemGroup>
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Include`|選擇性屬性。<br /><br /> 要包含在項目清單中的檔案或萬用字元。|
|`Exclude`|選擇性屬性。<br /><br /> 要從項目清單中排除的檔案或萬用字元。|
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|
|`Remove`|選擇性屬性。<br /><br /> 要從項目清單移除的檔案或萬用字元。<br /><br />|
|`KeepDuplicates`|選擇性屬性。<br /><br /> 指定項目如果與現有項目完全重複，是否應加入目標群組。 如果來源和目標項目具有相同的 `Include` 值，但中繼資料不同，則即使 `KeepDuplicates` 設定為 `false`，也會加入該項目。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。<br /><br /> 這個屬性只有在針對 `ItemGroup` 中的 `Target` 項目指定時才有效。|
|`KeepMetadata`|選擇性屬性。<br /><br /> 要加入目標項目之來源項目的中繼資料。 只有其名稱指定在分號分隔清單中的中繼資料，會從來源項目傳輸到目標項目。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。<br /><br /> 這個屬性只有在針對 `ItemGroup` 中的 `Target` 項目指定時才有效。|
|`RemoveMetadata`|選擇性屬性。<br /><br /> 不要傳輸到目標項目之來源項目的中繼資料。 所有中繼資料會從來源項目傳輸到目標項目，名稱包含在以分號分隔的名稱清單中之中繼資料除外。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。<br /><br /> 這個屬性只有在針對 `ItemGroup` 中的 `Target` 項目指定時才有效。|
|`Update`|選擇性屬性。 (僅適用於 Visual Studio 2017 或更新版本的 .NET Core 專案)。<br /><br /> 可讓您修改專案的中繼資料;通常用來在 intially 指定專案群組之後覆寫特定專案的預設中繼資料， (例如使用萬用字元) 。<br /><br /> 僅有當項目所在的 `ItemGroup` 不屬於 `Target` 時，針對該項目指定這個屬性才有效。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|使用者定義的項目中繼資料索引鍵，其中含有項目中繼資料值。 項目中可能有零個或多個 `ItemMetadata` 項目。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|項目的群組項目。|

## <a name="remarks"></a>備註

`Item` 項目定義建置系統的輸入，且會依據使用者定義的集合名稱，分組成為項目集合。 這些項目集合可以用來做為[工作](../msbuild/msbuild-tasks.md)的參數，工作會使用集合中個別的項目來執行建置程序的步驟。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

使用標記法 @ (\<myType>) 可將型別的專案集合 \<myType> ，展開為以分號分隔的字串清單，並傳遞至參數。 如果參數的類型是 `string`，則參數的值會是以分號分隔的項目清單。 如果參數是字串陣列 (`string[]`)，則每個項目都會根據分號的位置，插入到陣列中。 如果工作參數的類型是 <xref:Microsoft.Build.Framework.ITaskItem>`[]`，則值就是項目集合的內容再加上任何附加的中繼資料。 若要使用分號以外的字元來分隔每個項目，請使用語法 @(\<myType>, '\<separator>')。

MSBuild 引擎可以評估萬用字元（例如 `*` 和） `?` 以及遞迴萬用字元（例如 */ \* \* / \* .cs*）。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

## <a name="examples"></a>範例

下列程式碼範例示範如何宣告類型為 `CSFile` 的兩個項目。 第二個宣告項目包含 `MyMetadata` 設定為 `HelloWorld` 的中繼資料。

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

下列程式碼範例示範如何使用 `Update` 屬性，修改透過 Glob 隨附之 *somefile.cs* 檔案的中繼資料。 (僅適用於 Visual Studio 2017 或更新版本的 .NET Core 專案)。

```xml
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>另請參閱

- [項目](../msbuild/msbuild-items.md)
- [一般 MSBuild 專案項目](../msbuild/common-msbuild-project-items.md)
- [MSBuild 屬性](../msbuild/msbuild-properties.md)
- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
