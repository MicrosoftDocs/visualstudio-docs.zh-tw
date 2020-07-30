---
title: 一般 MSBuild 專案項目 | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 99ed79b1654057c4114ceb171b5cb1e1dfdb439f
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425390"
---
# <a name="common-msbuild-project-items"></a>一般 MSBuild 專案項目

在 MSBuild 中，專案是一個或多個檔案的名稱參考。 項目包含中繼資料，例如檔案名稱、路徑和版本號碼。 Visual Studio 中的所有專案類型都有共同的數個專案。 這些專案是在*microsoft.build.commontypes.xsd*檔案中定義。

## <a name="common-items"></a>共同項目

下列是所有共同專案項目的清單。

### <a name="reference"></a>參考

代表專案中的組件 (受管理) 參考。

|項目中繼資料名稱|描述|
|---------------|-----------------|
|提示路徑|選擇性字串。 組件的相對或絕對路徑。|
|名稱|選擇性字串。 組件的顯示名稱，例如，"System.Windows.Forms"。|
|融合名稱|選擇性字串。 指定項目的簡單或強式融合名稱。<br /><br /> 當這個屬性存在時，就可以節省時間，因為不需要開啟組件檔案就能取得融合名稱。|
|特定版本|選擇性布林值。 指定是否應僅參考融合名稱中的版本。|
|別名|選擇性字串。 參考的任何別名。|
|Private|選擇性布林值。 指定是否應將參考複製到輸出資料夾。 此屬性與 Visual Studio IDE 中參考的 [複製到本機]**** 屬性相符。|

### <a name="comreference"></a>COM 參考

代表專案中的 COM (未受管理) 元件參考。 此項目僅適用於 .NET 專案。

|項目中繼資料名稱|描述|
|---------------|-----------------|
|名稱|選擇性字串。 元件的顯示名稱。|
|Guid|必要字串。 元件的 GUID，格式為 {12345678-1234-1234-1234-1234567891234}。|
|VersionMajor|必要字串。 元件的版本號碼主要部分。 例如，如果完整版本號碼為"5.46"，則主要部分為 "5"。|
|VersionMinor|必要字串。 元件版本號碼的次要部分。 例如，如果完整版本號碼為"5.46"，則次要部分為 "46"。|
|LCID|選擇性字串。 元件的地區設定識別碼。|
|包裝函式工具|選擇性字串。 用於元件的包裝函式工具名稱，例如 "tlbimp"。|
|隔離式方案|選擇性布林值。 指定元件是否為免註冊元件。|

### <a name="comfilereference"></a>COM 檔案參考

代表傳遞給 [ResolveComReference](resolvecomreference-task.md) 目標之 `TypeLibFiles` 參數的類型程式庫清單。 此項目僅適用於 .NET 專案。

|項目中繼資料名稱|描述|
|---------------|-----------------|
|包裝函式工具|選擇性字串。 用於元件的包裝函式工具名稱，例如 "tlbimp"。|

### <a name="nativereference"></a>原生參考

代表原生的資訊清單檔案或是這類檔案的參考。

|項目中繼資料名稱|描述|
|---------------|-----------------|
|名稱|必要字串。 資訊清單檔案的基底名稱。|
|提示路徑|必要字串。 資訊清單檔案的相對路徑。|

### <a name="projectreference"></a>專案參考

代表另一個專案的參考。 `ProjectReference`目標會將專案轉換成[參考](#reference)專案 `ResolveProjectReferences` ，因此 `ProjectReference` ，如果轉換程式未覆寫，參考上的任何有效中繼資料可能會在上有效。

|項目中繼資料名稱|描述|
|---------------|-----------------|
|名稱|選擇性字串。 參考的顯示名稱。|
|隨附此逐步解說的專案|選擇性字串。 參考的 GUID，格式為 {12345678-1234-1234-1234-1234567891234}。|
|Package|選擇性字串。 所參考的專案檔路徑。|
|ReferenceOutputAssembly|選擇性布林值。 如果設定為 `false`，則不會將參考之專案的輸出，以[參考](#reference)的方式包含在此專案中，但仍然可確保其他專案會在此專案之前建置。 預設為 `true`。|

### <a name="compile"></a>編譯

代表編譯器的原始程式檔。

| 項目中繼資料名稱 | 描述 |
|-----------------------| - |
| 相依依據 | 選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案。 |
| 自動產生 | 選擇性布林值。 指出是否由 Visual Studio 整合式開發環境（IDE）為專案產生檔案。 |
| 連結 | 選擇性字串。 當檔案實際位於專案檔影響力之外時所顯示的標記路徑。 |
| 可見 | 選擇性布林值。 指出是否要在 Visual Studio 的**方案總管**中顯示檔案。 |
| 複製到輸出目錄 | 選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1. 永不<br />2. 一律<br />3. PreserveNewest |

### <a name="embeddedresource"></a>內嵌資源

代表要內嵌於所產生組件中的資源。

| 項目中繼資料名稱 | 描述 |
|-----------------------| - |
| 相依依據 | 選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案 |
| 產生器 | 必要字串。 在此項目上執行的任何檔案產生器名稱。 |
| 最後產生輸出 | 必要字串。 在此項目執行的任何檔案產生器所建立的檔案名稱。 |
| 自訂工具命名空間 | 必要字串。 在此項目上執行的任何檔案產生器應在其中建立程式碼的命名空間。 |
| 連結 | 選擇性字串。 如果檔案實際位於專案影響力之外，便會顯示標記路徑。 |
| 可見 | 選擇性布林值。 指出是否要在 Visual Studio 的**方案總管**中顯示檔案。 |
| 複製到輸出目錄 | 選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1. 永不<br />2. 一律<br />3. PreserveNewest |
| LogicalName | 必要字串。 內嵌資源的邏輯名稱。 |

### <a name="content"></a>內容

代表不會編譯到專案中，但可能內嵌或一起發行的檔案。

| 項目中繼資料名稱 | 描述 |
|-----------------------| - |
| 相依依據 | 選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案。 |
| 產生器 | 必要字串。 在此項目上執行的任何檔案產生器名稱。 |
| 最後產生輸出 | 必要字串。 在此項目執行的任何檔案產生器所建立的檔案名稱。 |
| 自訂工具命名空間 | 必要字串。 在此項目上執行的任何檔案產生器應在其中建立程式碼的命名空間。 |
| 連結 | 選擇性字串。 如果檔案實際位於專案影響力之外，便會顯示標記路徑。 |
| 發行狀態 | 必要字串。 內容的發行狀態，可以是：<br /><br /> -   預設值<br />-   包含<br />-   排除<br />-   資料檔<br />-   必要條件 |
| 為組件 | 選擇性布林值。 指定檔案是否為組件。 |
| 可見 | 選擇性布林值。 指出是否要在 Visual Studio 的**方案總管**中顯示檔案。 |
| 複製到輸出目錄 | 選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1. 永不<br />2. 一律<br />3. PreserveNewest |

### <a name="none"></a>無

代表在建置流程中應該沒有任何角色的檔案。

| 項目中繼資料名稱 | 描述 |
|-----------------------| - |
| 相依依據 | 選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案。 |
| 產生器 | 必要字串。 在此項目上執行的任何檔案產生器名稱。 |
| 最後產生輸出 | 必要字串。 在此項目執行的任何檔案產生器所建立的檔案名稱。 |
| 自訂工具命名空間 | 必要字串。 在此項目上執行的任何檔案產生器應在其中建立程式碼的命名空間。 |
| 連結 | 選擇性字串。 如果檔案實際位於專案影響力之外，便會顯示標記路徑。 |
| 可見 | 選擇性布林值。 指出是否要在 Visual Studio 的**方案總管**中顯示檔案。 |
| 複製到輸出目錄 | 選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1. 永不<br />2. 一律<br />3. PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata

表示要產生為的元件屬性 `[AssemblyMetadata(key, value)]` 。

| 項目中繼資料名稱 | 描述 |
|-----------------------| - |
| 包含 | 成為屬性（attribute）中的第一個參數（索引鍵） `AssemblyMetadataAttribute` 。 |
| 值 | 必要字串。 成為屬性（attribute）中的第二個參數（值） `AssemblyMetadataAttribute` 。 |

> [!NOTE]
> 這僅適用于使用 .NET Core SDK 的專案。

### <a name="baseapplicationmanifest"></a>基本應用程式資訊清單

表示組建的基本應用程式資訊清單，並包含 ClickOnce 部署安全性資訊。

### <a name="codeanalysisimport"></a>程式碼分析匯入

代表要匯入的 FxCop 專案。

### <a name="import"></a>匯入

表示 Visual Basic 編譯器應匯入其命名空間的元件。

## <a name="see-also"></a>另請參閱

- [一般 MSBuild 專案屬性](../msbuild/common-msbuild-project-properties.md)
- [.NET Core SDK 專案的 MSBuild 屬性](/dotnet/core/project-sdk/msbuild-props)
- [一般 MSBuild 專案中繼資料](common-msbuild-item-metadata.md)