---
title: VSIX 套件的剖析 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d811c1539dde655657331b7ca3511bbd4e80063f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX 封裝的結構
VSIX 封裝是.vsix 檔，其中包含一或多個 Visual Studio 擴充功能，以及 Visual Studio 會使用分類，並安裝擴充功能的中繼資料。 在 VSIX 資訊清單和 [Content_Types].xml 檔案中包含的中繼資料。 VSIX 封裝，也可能包含一或多個 Extension.vsixlangpack 檔案，提供當地語系化的安裝文字，而且可能包含其他 VSIX 封裝，以安裝相依項目。  
  
 VSIX 套件格式會遵循開放封裝慣例 (OPC) 標準。 封裝包含二進位檔和支援檔案，以及 [Content_Types].xml 檔案和.vsix 資訊清單檔案。 一個 VSIX 封裝可能包含多個專案或有自己的資訊清單的多個封裝的輸出。  
  
> [!NOTE]
>  VSIX 封裝中包含的檔案名稱必須不含空格，也不會保留在統一資源識別項 (URI)，做為字元定義下[ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339)。  
  
## <a name="the-vsix-manifest"></a>VSIX 資訊清單  
 VSIX 資訊清單包含要安裝的擴充功能，如下所示 VSX 結構描述的相關資訊。 如需詳細資訊，請參閱[VSIX 擴充功能結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。 如需範例 VSIX 資訊清單中，請參閱[PackageManifest 項目 （根項目、 VSX 結構描述）](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187)。  
  
 VSIX 資訊清單必須命名為`extension.vsixmanifest`包含.vsix 檔案中時。  
  
## <a name="the-content"></a>內容  
 VSIX 封裝可能包含範本、 工具箱項目、 Vspackage 或任何其他類型的延伸模組支援的 Visual Studio。  
  
## <a name="language-packs"></a>語言套件  
 VSIX 封裝可能包含一次或更多 Extension.vsixlangpack 檔案在安裝期間提供當地語系化的文字。 如需詳細資訊，請參閱[當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="dependencies-and-references"></a>相依性和參考  
 VSIX 封裝可能包含其他 VSIX 封裝，做為參考。 這些每個其他封裝必須包含自己的 VSIX 資訊清單。  
  
 如果使用者嘗試安裝具有相依性的擴充功能，安裝程式會確認使用者系統上已安裝的必要的組件。 如果找不到必要的組件，**擴充功能和更新**顯示遺漏的組件的清單。  
  
 如果擴充功能資訊清單包含一或多個[參考](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8)項目，**擴充功能和更新**相比較的擴充功能的系統上已安裝的每個參考的資訊清單，並安裝如果尚未安裝，請參考擴充功能。 如果已安裝較早版本的參考延伸，較新版本取代它。  
  
 多專案方案中的專案包含另一個專案的參考相同方案中，如果 VSIX 封裝會包含該專案的相依性。 您可以按一下參考內部的專案，然後在 覆寫這個行為**屬性**視窗中，設定**輸出群組包含在 VSIX**屬性`BuiltProjectOutputGroup`。  
  
 若要從參考的組件的附屬 Dll 包含在 VSIX 封裝中，加入`SatelliteDllsProjectOutputGroup`至**輸出群組包含在 VSIX**屬性。  
  
## <a name="installation-location"></a>安裝位置  
 在安裝期間，**擴充功能和更新**尋找資料夾之下的 %localappdata%\microsoft\visualstudio\14.0\extensions VSIX 封裝的內容。  
  
 根據預設，安裝只適用於目前的使用者，因為 %localappdata%是使用者專屬目錄。 不過，如果您設定[AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b)資訊清單的項目`True`，將會在安裝擴充功能...\\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions 並將提供給電腦的所有使用者。  
  
## <a name="contenttypesxml"></a>[Content_Types].xml  
 [Content_Types].xml 檔案識別展開的.vsix 檔案中的檔案類型。 Visual Studio 安裝套件時使用此檔案，但不會安裝該檔案本身。 如需有關這個檔案的詳細資訊，請參閱[[Content_types].xml 檔案的結構](the-structure-of-the-content-types-dot-xml-file.md)。  
  
 [Content_Types].xml 檔案必須由開放封裝慣例 (OPC) 標準。 如需有關 OPC 的詳細資訊，請參閱[OPC: 新標準為封裝資料](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN 網站上。