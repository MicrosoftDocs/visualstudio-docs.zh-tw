---
title: MSBuild 已知的項目中繼資料 | Microsoft Docs
description: 瞭解建立時指派給每個專案的 MSBuild 中繼資料，以及您可以定義來控制組建行為的一些選擇性 MSBuild 中繼資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9ca2249e6119e27574791a2cbd9e8b09a9bde63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878178"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild 已知的項目中繼資料

專案中繼資料是附加至專案的值。 當專案建立時，MSBuild 會將某些專案指派給專案，但是您也可以定義您所需的任何中繼資料。 某些使用者定義的中繼資料值對 MSBuild、特定工作工作或 Sdk （例如 .NET SDK）具有意義。

本文中的第一個表格描述建立時指派給每個專案的中繼資料。 下表顯示一些具有 MSBuild 意義的選擇性中繼資料，您可以定義此中繼資料來控制組建行為。 每個範例都使用了下列項目宣告，以在專案中包含 *C:\MyProject\Source\Program.cs* 檔案。

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|項目中繼資料|Description|
|-------------------|-----------------|
|%(FullPath)|包含項目的完整路徑。 例如：<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|包含項目的根目錄。 例如：<br /><br /> *C：\\*|
|%(Filename)|包含項目的檔案名稱 (不含副檔名)。 例如：<br /><br /> *程式*|
|%(Extension)|包含項目的副檔名。 例如：<br /><br /> *.cs*|
|%(RelativeDir)|包含 `Include` 屬性中指定的路徑，直到最後一個反斜線 (\\) 為止。 例如：<br /><br /> *來源\\*<br /><br /> 如果 `Include` 屬性是完整路徑，則 `%(RelativeDir)` 以根目錄開頭 `%(RootDir)` 。  例如： <br /><br /> *C:\MyProject\Source\\*|
|%(Directory)|包含項目的目錄 (不含根目錄)。 例如：<br /><br /> *MyProject\\Source\\*|
|%(RecursiveDir)|如果 `Include` 屬性包含萬用字元 \*\*，此中繼資料會指定取代萬用字元的部分路徑。 如需萬用字元的詳細資訊，請參閱 [如何：選取要建立的](../msbuild/how-to-select-the-files-to-build.md)檔案。<br /><br /> 如果資料夾 *C:\MySolution\MyProject\Source \\* 包含 *Program.cs* 檔案，而且專案檔包含此專案：<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> 則 `%(MyItem.RecursiveDir)` 的值會是 *MySolution\MyProject\Source\\*。|
|%(Identity)|屬性中指定的專案 `Include` 。 例如：<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|包含上次修改項目時間的時間戳記。 例如：<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|包含項目建立時間的時間戳記。 例如：<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|包含上次存取項目時間的時間戳記。<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>另請參閱

- [一般 MSBuild 項目中繼資料](common-msbuild-item-metadata.md)
- [項目](../msbuild/msbuild-items.md)
- [批次處理](../msbuild/msbuild-batching.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
