---
title: VSIX 封裝的剖析 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2a769b0d04f76a2a32c00e262ff03b400af02feb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852280"
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX 套件的結構
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX 封裝是一個包含一或多個 Visual Studio 延伸模組的 .vsix 檔案，以及 Visual Studio 用來分類及安裝延伸模組的中繼資料。 該中繼資料包含在 VSIX 資訊清單和 [Content_Types] .xml 檔案中。 VSIX 封裝也可以包含一或多個 vsixlangpack 檔案，以提供當地語系化的設定文字，而且可能包含其他 VSIX 套件來安裝相依性。  
  
 VSIX 封裝格式會遵循開放式封裝慣例的 (OPC) 標準。 封裝包含二進位檔和支援檔案，以及 [Content_Types] .xml 檔案和 .vsix 資訊清單檔。 一個 VSIX 封裝可能包含多個專案的輸出，或甚至是多個具有自己的資訊清單的封裝。  
  
> [!NOTE]
> VSIX 套件中包含的檔案名不能包含空格，也不能在統一資源識別項中保留的字元 (URI) ，如[ \[ RFC2396 \] ](https://go.microsoft.com/fwlink/?LinkId=90339)中所定義。  
  
## <a name="the-vsix-manifest"></a>VSIX 資訊清單  
 VSIX 資訊清單包含要安裝之延伸模組的相關資訊，並遵循 VSX 架構。 如需詳細資訊，請參閱 [VSIX 延伸架構1.0 參考](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。 如需 VSIX 資訊清單的範例，請參閱 [PackageManifest 元素 (根項目、VSX 架構) ](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)。  
  
 VSIX 資訊清單 `extension.vsixmanifest` 包含在 .vsix 檔案中時，必須命名為。  
  
## <a name="the-content"></a>內容  
 VSIX 封裝可能包含範本、工具箱專案、Vspackage，或 Visual Studio 所支援的任何其他延伸模組類型。  
  
## <a name="language-packs"></a>語言套件  
 VSIX 封裝可包含一或多個 vsixlangpack 檔案，以便在安裝期間提供當地語系化文字。 如需詳細資訊，請參閱 [當地語系化 VSIX 套件](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="dependencies-and-references"></a>相依性和參考  
 VSIX 封裝可能包含其他 VSIX 封裝作為參考。 這些其他封裝都必須包含自己的 VSIX 資訊清單。  
  
 如果使用者嘗試安裝具有相依性的擴充功能，安裝程式會驗證是否已在使用者系統上安裝必要的元件。 如果找不到必要的元件，[ **擴充功能和更新** ] 會顯示遺漏的元件清單。  
  
 如果延伸模組資訊清單包含一或多個 [參考](https://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) 專案， **擴充功能和更新** 會比較每個參考的資訊清單與系統上安裝的擴充功能，如果尚未安裝，則會安裝參考的擴充功能。 如果已安裝較舊版本的參考延伸模組，則較新的版本會取代它。  
  
 如果多專案方案中的專案包含相同方案中另一個專案的參考，則 VSIX 封裝會包含該專案的相依性。 您可以藉由按一下內部專案的參考來覆寫此行為，然後在 [ **屬性** ] 視窗中，將 [VSIX] 屬性 **中包含的輸出群組** 設定為 `BuiltProjectOutputGroup` 。  
  
 若要在 VSIX 封裝中包含參考元件的附屬 Dll，請加入 `SatelliteDllsProjectOutputGroup` vsix 屬性中 **包含的輸出群組** 。  
  
## <a name="installation-location"></a>安裝位置  
 在安裝期間， **擴充功能和更新** 會在%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions. 下的資料夾中尋找 VSIX 套件的內容  
  
 根據預設，安裝只會套用至目前的使用者，因為% LocalAppData% 是使用者特定的目錄。 但是，如果您將資訊清單的[AllUsers](https://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b)元素設定為 `True` ，此延伸模組會安裝在 \\ 底下。*VisualStudioInstallationFolder*\Common7\IDE\Extensions 將可供電腦的所有使用者使用。  
  
## <a name="content_typesxml"></a>[Content_Types] .xml  
 [Content_Types] .xml 檔案會識別擴充的 .vsix 檔中的檔案類型。 Visual Studio 在套件安裝期間使用此檔案，但不會安裝檔案本身。 如需此檔案的詳細資訊，請參閱 [Content_types \] .xml](../extensibility/the-structure-of-the-content-types-dot-xml-file.md)檔案的結構。  
  
 開放式封裝慣例 (OPC) standard 需要 [Content_Types] .xml 檔案。 如需 OPC 的詳細資訊，請參閱 [opc：將資料封裝](https://msdn.microsoft.com/magazine/cc163372.aspx) 在 MSDN 網站的新標準。
