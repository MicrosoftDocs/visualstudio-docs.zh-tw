---
title: 一般 MSBuild 專案項目 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 900241a25fabc259fb19ffa2b75f2fa12ad6e517
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152551"
---
# <a name="common-msbuild-project-items"></a>一般 MSBuild 專案項目
在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中，項目是一個或多個檔案的具名參考。 項目包含中繼資料，例如檔案名稱、路徑和版本號碼。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的所有專案類型都有共同的數個項目。 這些項目會在 *Microsoft.Build.CommonTypes.xsd* 檔案中定義。  
  
## <a name="common-items"></a>共同項目  
 下列是所有共同專案項目的清單。  
  
### <a name="reference"></a>參考資料  
 代表專案中的組件 (受管理) 參考。  
  
|項目中繼資料名稱|描述|  
|---------------|-----------------|  
|提示路徑|選擇性字串。 組件的相對或絕對路徑。|  
|名稱|選擇性字串。 組件的顯示名稱，例如，"System.Windows.Forms"。|  
|融合名稱|選擇性字串。 指定項目的簡單或強式融合名稱。<br /><br /> 當這個屬性存在時，就可以節省時間，因為不需要開啟組件檔案就能取得融合名稱。|  
|特定版本|選擇性布林值。 指定是否應僅參考融合名稱中的版本。|  
|別名|選擇性字串。 參考的任何別名。|  
|Private|選擇性布林值。 指定是否應將參考複製到輸出資料夾。 此屬性與 Visual Studio IDE 中參考的 [複製到本機] 屬性相符。|  
  
### <a name="comreference"></a>COM 參考  
 代表專案中的 COM (未受管理) 元件參考。  
  
|項目中繼資料名稱|描述|  
|---------------|-----------------|  
|名稱|選擇性字串。 元件的顯示名稱。|  
|Guid|選擇性字串。 元件的 GUID，格式為 {12345678-1234-1234-1234-1234567891234}。|  
|VersionMajor|選擇性字串。 元件的版本號碼主要部分。 例如，如果完整版本號碼為"5.46"，則主要部分為 "5"。|  
|VersionMinor|選擇性字串。 元件版本號碼的次要部分。 例如，如果完整版本號碼為"5.46"，則次要部分為 "46"。|  
|LCID|選擇性字串。 元件的地區設定識別碼。|  
|包裝函式工具|選擇性字串。 用於元件的包裝函式工具名稱，例如 "tlbimp"。|  
|隔離|選擇性布林值。 指定元件是否為免註冊元件。|  
  
### <a name="comfilereference"></a>COM 檔案參考  
 代表饋送至 ResolvedComreference 目標的類型程式庫清單。  
  
|項目中繼資料名稱|描述|  
|---------------|-----------------|  
|包裝函式工具|選擇性字串。 用於元件的包裝函式工具名稱，例如 "tlbimp"。|  
  
### <a name="nativereference"></a>原生參考  
 代表原生的資訊清單檔案或是這類檔案的參考。  
  
|項目中繼資料名稱|描述|  
|---------------|-----------------|  
|名稱|必要的字串。 資訊清單檔案的基底名稱。|  
|提示路徑|必要的字串。 資訊清單檔案的相對路徑。|  
  
### <a name="projectreference"></a>專案參考  
 代表另一個專案的參考。  
  
|項目中繼資料名稱|描述|  
|---------------|-----------------|  
|名稱|選擇性字串。 參考的顯示名稱。|  
|專案|選擇性字串。 參考的 GUID，格式為 {12345678-1234-1234-1234-1234567891234}。|  
|Package|選擇性字串。 所參考的專案檔路徑。|  
|ReferenceOutputAssembly|選擇性布林值。 如果設定為 `false`，則不會將參考之專案的輸出，以[參考](#Reference)的方式包含在此專案中，但仍然可確保其他專案會在此專案之前建置。 預設值為 `true`。|
  
### <a name="compile"></a>編譯  
 代表編譯器的原始程式檔。  
  
|項目中繼資料名稱|描述|  
|---------------|-----------------|  
|相依依據|選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案。|  
|自動產生|選擇性布林值。 指出是否已透過 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 為專案產生檔案。|  
|連結|選擇性字串。 當檔案實際位於專案檔影響力之外時所顯示的標記路徑。|  
|可見|選擇性布林值。 指出是否要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的方案總管中顯示檔案。|  
|複製到輸出目錄|選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1.永不<br />2.永遠<br />3.保留最新的|  
  
### <a name="embeddedresource"></a>內嵌資源  
 代表要內嵌於所產生組件中的資源。  
  
|項目中繼資料名稱|描述|  
|---------------|-----------------|  
|相依依據|選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案|  
|Generator|必要的字串。 在此項目上執行的任何檔案產生器名稱。|  
|最後產生輸出|必要的字串。 在此項目執行的任何檔案產生器所建立的檔案名稱。|  
|自訂工具命名空間|必要的字串。 在此項目上執行的任何檔案產生器應在其中建立程式碼的命名空間。|  
|連結|選擇性字串。 如果檔案實際位於專案影響力之外，便會顯示標記路徑。|  
|可見|選擇性布林值。 指出是否要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的方案總管中顯示檔案。|  
|複製到輸出目錄|選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1.永不<br />2.永遠<br />3.保留最新的|  
|邏輯名稱|必要的字串。 內嵌資源的邏輯名稱。|  
  
### <a name="content"></a>內容  
 代表不會編譯到專案中，但可能內嵌或一起發行的檔案。  
  
|項目中繼資料名稱|描述|  
|---------------|-----------------|  
|相依依據|選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案。|  
|Generator|必要的字串。 在此項目上執行的任何檔案產生器名稱。|  
|最後產生輸出|必要的字串。 在此項目執行的任何檔案產生器所建立的檔案名稱。|  
|自訂工具命名空間|必要的字串。 在此項目上執行的任何檔案產生器應在其中建立程式碼的命名空間。|  
|連結|選擇性字串。 如果檔案實際位於專案影響力之外，便會顯示標記路徑。|  
|發行狀態|必要的字串。 內容的發行狀態，可以是：<br /><br /> -   預設值<br />-   包含<br />-   排除<br />-   資料檔<br />-   必要條件|  
|為組件|選擇性布林值。 指定檔案是否為組件。|  
|可見|選擇性布林值。 指出是否要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的方案總管中顯示檔案。|  
|複製到輸出目錄|選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1.永不<br />2.永遠<br />3.保留最新的|  
  
### <a name="none"></a>無  
 代表在建置流程中應該沒有任何角色的檔案。  
  
|項目中繼資料名稱|描述|  
|---------------|-----------------|  
|相依依據|選擇性字串。 指定這個檔案必須倚賴才能正確編譯的檔案。|  
|Generator|必要的字串。 在此項目上執行的任何檔案產生器名稱。|  
|最後產生輸出|必要的字串。 在此項目執行的任何檔案產生器所建立的檔案名稱。|  
|自訂工具命名空間|必要的字串。 在此項目上執行的任何檔案產生器應在其中建立程式碼的命名空間。|  
|連結|選擇性字串。 如果檔案實際位於專案影響力之外，便會顯示標記路徑。|  
|可見|選擇性布林值。 指出是否要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的方案總管中顯示檔案。|  
|複製到輸出目錄|選擇性字串。 決定是否要將檔案複製到輸出目錄。 值為：<br /><br /> 1.永不<br />2.永遠<br />3.保留最新的|  
  
### <a name="baseapplicationmanifest"></a>基本應用程式資訊清單  
 代表組建的基本應用程式資訊清單，並包含 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署安全性資訊。  
  
### <a name="codeanalysisimport"></a>程式碼分析匯入  
 代表要匯入的 FxCop 專案。  
  
### <a name="import"></a>匯入  
 代表應該由 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 編譯器匯入命名空間的組件。  
  
## <a name="see-also"></a>另請參閱  
 [一般 MSBuild 專案屬性](../msbuild/common-msbuild-project-properties.md)
