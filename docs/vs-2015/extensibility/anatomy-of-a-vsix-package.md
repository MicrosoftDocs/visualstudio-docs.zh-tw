---
title: VSIX 封裝的結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 207abbda08134c2a1e065cf73050fc2451d4eaab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181453"
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX 套件的結構
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX 封裝是.vsix 檔案，其中包含一或多個 Visual Studio 擴充功能，以及 Visual Studio 會使用分類，並安裝擴充功能的中繼資料。 該中繼資料包含在 VSIX 資訊清單和 [Content_Types].xml 檔案中。 VSIX 封裝也可能包含一或多個 Extension.vsixlangpack 檔，以提供當地語系化的安裝程式文字，而且可能包含其他的 VSIX 套件，以安裝相依項目。  
  
 VSIX 套件格式會遵循開放封裝慣例 (OPC) 標準。 套件包含二進位檔和支援檔案，以及 [Content_Types].xml 檔案和.vsix 資訊清單檔案。 一個 VSIX 封裝可能包含多個專案或甚至是多個套件有自己的資訊清單的輸出。  
  
> [!NOTE]
>  VSIX 封裝中包含的檔案名稱不得包含空格，也不下定義的保留在統一資源識別元 (URI)，做為字元[ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339)。  
  
## <a name="the-vsix-manifest"></a>VSIX 資訊清單  
 VSIX 資訊清單包含要安裝的延伸模組和如下所示 VSX 結構描述的相關資訊。 如需詳細資訊，請參閱 < [VSIX 延伸結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。 如需範例 VSIX 資訊清單中，請參閱 < [PackageManifest 項目 （根項目、 VSX 結構描述）](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187)。  
  
 VSIX 資訊清單必須命名為`extension.vsixmanifest`包含在.vsix 檔案時。  
  
## <a name="the-content"></a>內容  
 VSIX 封裝可能包含範本、 工具箱項目、 Vspackage 或任何其他類型的延伸模組支援的 Visual Studio。  
  
## <a name="language-packs"></a>語言套件  
 VSIX 封裝可能包含一次或更多的 Extension.vsixlangpack 檔，以在安裝期間提供當地語系化的文字。 如需詳細資訊，請參閱 <<c0> [ 當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="dependencies-and-references"></a>相依性和參考  
 VSIX 封裝可能包含其他 VSIX 封裝，做為參考。 這些每個其他封裝必須包括它自己的 VSIX 資訊清單。  
  
 如果使用者嘗試安裝具有相依性延伸模組，安裝程式會確認必要的組件會安裝在使用者系統上。 如果找不到必要的組件、**擴充功能和更新**顯示遺漏的組件的清單。  
  
 如果延伸模組資訊清單包含一或多個[參考](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8)項目**擴充功能和更新**比較的系統已安裝的擴充功能的每個參考的資訊清單，並安裝如果尚未安裝，請參考擴充功能。 如果已安裝較早版本的參考延伸模組，較新版本取代它。  
  
 如果多專案方案中的專案會包含相同的方案中另一個專案的參考，VSIX 封裝就會包含該專案的相依性。 您可以按一下參考內部的專案，然後在 覆寫這個行為**屬性**視窗中，設定**輸出群組包含在 VSIX**屬性設`BuiltProjectOutputGroup`。  
  
 若要從參考組件的附屬 Dll 包含在 VSIX 封裝中，新增`SatelliteDllsProjectOutputGroup`要**輸出群組包含在 VSIX**屬性。  
  
## <a name="installation-location"></a>安裝位置  
 在安裝期間，**擴充功能和更新**VSIX 中封裝的資料夾之下的 %localappdata%\microsoft\visualstudio\14.0\extensions 內容看起來。  
  
 根據預設，安裝只適用於目前的使用者，因為 %localappdata%是使用者專屬目錄。 不過，如果您設定[AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b)資訊清單的項目`True`，將會在安裝擴充功能...\\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions 和可供所有使用者的電腦。  
  
## <a name="contenttypesxml"></a>[Content_Types].xml  
 [Content_Types].xml 檔案識別展開的.vsix 檔案中的檔案類型。 Visual Studio 套件的安裝期間會使用這個檔案，但不會安裝檔案本身。 如需有關這個檔案的詳細資訊，請參閱 <<c0> [ 結構 Content_types\].xml 檔案](../extensibility/the-structure-of-the-content-types-dot-xml-file.md)。  
  
 [Content_Types].xml 檔案，才由開放封裝慣例 (OPC) 標準。 如需有關 OPC 的詳細資訊，請參閱 < [OPC: 新標準的封裝資料](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN 網站上。

