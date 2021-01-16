---
title: 一般 MSBuild 專案項目 | Microsoft Docs
description: 瞭解一般 MSBuild 專案專案。 專案會命名為一或多個檔案的參考，而且會有檔案名、路徑和版本號碼等中繼資料。
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea072cf3e9a236fdc6a4ad66b1c0cf7ddcda1550
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533441"
---
# <a name="common-msbuild-project-items"></a>一般 MSBuild 專案項目

在 MSBuild 中，專案是一個或多個檔案的命名參考。 項目包含中繼資料，例如檔案名稱、路徑和版本號碼。 Visual Studio 中的所有專案類型都有共通的數個專案。 這些專案是在 *microsoft.build.commontypes.xsd* 中定義。

## <a name="common-items"></a>共同項目

下列是所有共同專案項目的清單。

### <a name="reference"></a>參考

代表專案中的組件 (受管理) 參考。

|項目中繼資料名稱|說明|
|---------------|-----------------|
|提示路徑|選擇性字串。 組件的相對或絕對路徑。|
|Name|選擇性字串。 組件的顯示名稱，例如，"System.Windows.Forms"。|
|融合名稱|選擇性字串。 指定項目的簡單或強式融合名稱。<br /><br /> 當這個屬性存在時，就可以節省時間，因為不需要開啟組件檔案就能取得融合名稱。|
|特定版本|選擇性布林值。 指定是否應僅參考融合名稱中的版本。|
|別名|選擇性字串。 參考的任何別名。|
|私人|選擇性布林值。 指定是否應將參考複製到輸出資料夾。 此屬性與 Visual Studio IDE 中參考的 [複製到本機] 屬性相符。|

### <a name="comreference"></a>COM 參考

代表專案中的 COM (未受管理) 元件參考。 此項目僅適用於 .NET 專案。

|項目中繼資料名稱|說明|
|---------------|-----------------|
|Name|選擇性字串。 元件的顯示名稱。|
|Guid|必要字串。 元件的 GUID，格式為 {12345678-1234-1234-1234-1234567891234}。|
|VersionMajor|必要字串。 元件的版本號碼主要部分。 例如，如果完整版本號碼為"5.46"，則主要部分為 "5"。|
|VersionMinor|必要字串。 元件版本號碼的次要部分。 例如，如果完整版本號碼為"5.46"，則次要部分為 "46"。|
|LCID|選擇性字串。 元件的地區設定識別碼。|
|包裝函式工具|選擇性字串。 用於元件的包裝函式工具名稱，例如 "tlbimp"。|
|隔離|選擇性布林值。 指定元件是否為免註冊元件。|

### <a name="comfilereference"></a>COM 檔案參考

代表傳遞給 [ResolveComReference](resolvecomreference-task.md) 目標之 `TypeLibFiles` 參數的類型程式庫清單。 此項目僅適用於 .NET 專案。

|項目中繼資料名稱|說明|
|---------------|-----------------|
|包裝函式工具|選擇性字串。 用於元件的包裝函式工具名稱，例如 "tlbimp"。|

### <a name="nativereference"></a>原生參考

代表原生的資訊清單檔案或是這類檔案的參考。

|項目中繼資料名稱|說明|
|---------------|-----------------|
|Name|必要字串。 資訊清單檔案的基底名稱。|
|提示路徑|必要字串。 資訊清單檔案的相對路徑。|

### <a name="projectreference"></a>專案參考

代表另一個專案的參考。 `ProjectReference` 專案會依目標轉換成 [參考](#reference) 專案 `ResolveProjectReferences` ，因此 `ProjectReference` ，如果轉換程式未覆寫，則參考上任何有效的中繼資料都可能有效。

|項目中繼資料名稱|說明|
|---------------|-----------------|
|Name|選擇性字串。 參考的顯示名稱。|
|GlobalPropertiesToRemove|選擇性的 `string[]`。 建立參考專案時要移除的屬性名稱，例如 `RuntimeIdentifier;PackOnBuild` 。 預設為空白。|
|Project|選擇性字串。 參考的 GUID，格式為 {12345678-1234-1234-1234-1234567891234}。|
|OutputItemType|選擇性字串。 要發出目標輸出的專案類型。 預設值為空白。 如果參考中繼資料設定為 "true" (預設值) 則目標輸出會成為編譯器的參考。|
|ReferenceOutputAssembly|選擇性布林值。 如果設定為 `false`，則不會將參考之專案的輸出，以[參考](#reference)的方式包含在此專案中，但仍然可確保其他專案會在此專案之前建置。 預設為 `true`。|
|SetConfiguration|選擇性字串。 設定參考專案的全域屬性 `Configuration` ，例如 `Configuration=Release` 。|
|SetPlatform|選擇性字串。 設定參考專案的全域屬性 `Platform` ，例如 `Platform=AnyCPU` 。|
|SetTargetFramework|選擇性字串。 設定參考專案的全域屬性 `TargetFramework` ，例如 `TargetFramework=netstandard2.0` 。|
|SkipGetTargetFrameworkProperties|選擇性布林值。 如果 `true` 為，則會建立參考的專案，而不會協調最相容的 `TargetFramework` 值。 預設為 `false`。|
|目標|選擇性的 `string[]`。 應建立之參考專案中的目標清單（以分號分隔）。 預設值是預設值 `$(ProjectReferenceBuildTargets)` 為空白，表示預設目標。|

### <a name="compile"></a>編譯

代表編譯器的原始程式檔。

| 項目中繼資料名稱 | 說明 |
|-----------------------| - |
| 相依依據 | 選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案。 |
| 自動產生 | 選擇性布林值。 指出 Visual Studio 整合式開發環境中是否為專案產生檔案 (IDE) 。 |
| 連結 | 選擇性字串。 當檔案實際位於專案檔影響力之外時所顯示的標記路徑。 |
| 可見 | 選擇性布林值。 指出是否要在 Visual Studio 的 **方案總管** 中顯示檔案。 |
| 複製到輸出目錄 | 選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1. 永不<br />2. 一律<br />3. PreserveNewest |

### <a name="embeddedresource"></a>內嵌資源

代表要內嵌於所產生組件中的資源。

| 項目中繼資料名稱 | 說明 |
|-----------------------| - |
| 相依依據 | 選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案 |
| Generator | 必要字串。 在此項目上執行的任何檔案產生器名稱。 |
| 最後產生輸出 | 必要字串。 在此項目執行的任何檔案產生器所建立的檔案名稱。 |
| 自訂工具命名空間 | 必要字串。 在此項目上執行的任何檔案產生器應在其中建立程式碼的命名空間。 |
| 連結 | 選擇性字串。 如果檔案實際位於專案影響力之外，便會顯示標記路徑。 |
| 可見 | 選擇性布林值。 指出是否要在 Visual Studio 的 **方案總管** 中顯示檔案。 |
| 複製到輸出目錄 | 選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1. 永不<br />2. 一律<br />3. PreserveNewest |
| LogicalName | 必要字串。 內嵌資源的邏輯名稱。 |

### <a name="content"></a>Content

代表不會編譯到專案中，但可能內嵌或一起發行的檔案。

| 項目中繼資料名稱 | 說明 |
|-----------------------| - |
| 相依依據 | 選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案。 |
| Generator | 必要字串。 在此項目上執行的任何檔案產生器名稱。 |
| 最後產生輸出 | 必要字串。 在此項目執行的任何檔案產生器所建立的檔案名稱。 |
| 自訂工具命名空間 | 必要字串。 在此項目上執行的任何檔案產生器應在其中建立程式碼的命名空間。 |
| 連結 | 選擇性字串。 如果檔案實際位於專案影響力之外，便會顯示標記路徑。 |
| 發行狀態 | 必要字串。 內容的發行狀態，可以是：<br /><br /> -   預設值<br />-   包含<br />-   排除<br />-   資料檔<br />-   必要條件 |
| 為組件 | 選擇性布林值。 指定檔案是否為組件。 |
| 可見 | 選擇性布林值。 指出是否要在 Visual Studio 的 **方案總管** 中顯示檔案。 |
| 複製到輸出目錄 | 選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1. 永不<br />2. 一律<br />3. PreserveNewest |

### <a name="none"></a>無

代表在建置流程中應該沒有任何角色的檔案。

| 項目中繼資料名稱 | 說明 |
|-----------------------| - |
| 相依依據 | 選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案。 |
| Generator | 必要字串。 在此項目上執行的任何檔案產生器名稱。 |
| 最後產生輸出 | 必要字串。 在此項目執行的任何檔案產生器所建立的檔案名稱。 |
| 自訂工具命名空間 | 必要字串。 在此項目上執行的任何檔案產生器應在其中建立程式碼的命名空間。 |
| 連結 | 選擇性字串。 如果檔案實際位於專案影響力之外，便會顯示標記路徑。 |
| 可見 | 選擇性布林值。 指出是否要在 Visual Studio 的 **方案總管** 中顯示檔案。 |
| 複製到輸出目錄 | 選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1. 永不<br />2. 一律<br />3. PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata

表示要產生的元件屬性 `[AssemblyMetadata(key, value)]` 。

| 項目中繼資料名稱 | 描述 |
|-----------------------| - |
| 包含 | 成為屬性函式中 (索引鍵) 的第一個參數 `AssemblyMetadataAttribute` 。 |
| 值 | 必要字串。 成為 (屬性函式中) 值的第二個參數 `AssemblyMetadataAttribute` 。 |

> [!NOTE]
> 此專案適用于使用 SDK for .NET 5 (和 .NET Core) 和更新版本的專案。

### <a name="internalsvisibleto"></a>InternalsVisibleTo

指定要發出為 `[InternalsVisibleTo(..)]` 元件屬性的元件。

| 項目中繼資料名稱 | 描述 |
|-----------------------| - |
| 包含 | 組件名稱。 |
| 答案 | 選擇性字串。 元件的公開金鑰。 |

> [!NOTE]
> 此專案適用于使用 SDK for .NET 5 (和 .NET Core) 和更新版本的專案。

### <a name="baseapplicationmanifest"></a>基本應用程式資訊清單

代表組建的基底應用程式資訊清單，並包含 ClickOnce 部署安全性資訊。

### <a name="codeanalysisimport"></a>程式碼分析匯入

代表要匯入的 FxCop 專案。

### <a name="import"></a>匯入

代表 Visual Basic 編譯器要匯入其命名空間的元件。

## <a name="see-also"></a>另請參閱

- [一般 MSBuild 專案屬性](../msbuild/common-msbuild-project-properties.md)
- [一般 MSBuild 項目中繼資料](common-msbuild-item-metadata.md)