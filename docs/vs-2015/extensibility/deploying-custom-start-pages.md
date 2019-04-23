---
title: 部署自訂起始頁 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1cdd172c2960024da8b12735764161d36498c4e2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039138"
---
# <a name="deploying-custom-start-pages"></a>部署自訂起始頁
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 VSIX 部署，或將檔案複製到目標電腦上正確的位置，您可以部署自訂起始頁。  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>使用起始頁專案範本的 VSIX 部署  
 當您使用起始頁專案範本，建立起始頁，然後建置專案時，Visual Studio 會建立可散發.vsix 檔案。 封裝在.vsix 檔案中的 [入門] 頁面可讓您部署中，根據您的適用對象的下列選項：  
  
- 您可以在公用網站或網路共用上放置.vsix 檔案。 當有人開啟檔案時，會自動安裝 [入門] 頁面。  
  
- 您可以上傳.vsix 檔案[Visual Studio Marketplace](https://marketplace.visualstudio.com/)網站，使用者可以使用來安裝它**延伸模組管理員**。  
  
  起始頁專案範本會建立一份預設 Visual Studio 起始頁，讓您可以修改複本，並保留原始。  
  
  您也可以使用來取得 「 起始頁專案範本**延伸模組管理員**或是從網站下載。  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>不使用起始頁專案範本的 VSIX 部署  
 成功的 VSIX 部署需要 VSIX 註冊程序與辨識的資料夾中安裝擴充功能**延伸模組管理員**。 由於起始頁專案範本已經指定正確的資料夾，我們建議您使用，每當您想要封裝的 VSIX 部署擴充功能。 不過，如果您的案例中，您無法使用的範本，您可以建立 VSIX 部署而不使用它。  
  
 若要建立 VSIX 部署，而不需使用起始頁專案範本，首先建立.vsix 檔案的 [入門] 頁面中的這兩種方式：  
  
- 藉由將空的 VSIX 專案中的自訂起始頁檔案。 如需詳細資訊，請參閱 < [VSIX 專案範本](../extensibility/vsix-project-template.md)。  
  
- 手動建立.vsix 檔案。 如需詳細資訊，請參閱[如何：手動封裝擴充功能 （VSIX 部署）](../misc/how-to-manually-package-an-extension-vsix-deployment.md)。  
  
  Visual Studio 能夠辨識 [入門] 頁面中，如`Content Element`VSIX 資訊清單必須包含`CustomExtension Element`具有`Type`屬性設為`"StartPage"`。 使用 VSIX 部署已安裝的起始頁延伸模組會出現在**自訂起始頁**上列出**啟動**選項頁面中以 **[安裝延伸模組]** *延伸模組名稱*。  
  
  如果您的起始頁套件包含組件，您必須先新增繫結路徑註冊，以便 Visual Studio 啟動時可供使用。 若要這樣做，請確定您的套件包含具有下列資訊的.pkgdef 檔。  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>針對所有使用者的 VSIX 部署  
 根據預設，部署 VSIX 封裝中的延伸模組會安裝僅適用於目前的使用者。 您可以建立所有使用者部署，在目標電腦的所有使用者進行的起始頁安裝。  
  
##### <a name="to-create-an-all-users-deployment"></a>若要建立的所有使用者部署  
  
1. 在程式碼檢視中開啟 extension.vsixmanifest 檔案。  
  
2. 在 `Identifier`加入 vsix 資訊清單的項目`AllUsers`項目，其值為`true`。  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     這會造成 vsix 安裝程式提示您輸入系統管理員權限，並接著將檔案安裝到 \Common7\IDE\Extensions。  
  
3. 開啟.pkgdef 檔。  
  
4. 修改以加入下列程式碼，來設定預設起始頁 HKLM 底下.pkgdef 所在*MyStartPage.xaml*是包含您的起始頁.xaml 檔的名稱。  
  
     [$RootKey$\StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     這會告訴 Visual 站要在新的起始頁位置中尋找。  
  
## <a name="file-copy-deployment"></a>檔案複製部署  
 您不必建立要部署自訂起始頁的.vsix 檔案。 相反地，您可以直接在使用者的 \StartPages\ 資料夾複製了標記和支援檔案。 **自訂起始頁**上列出**啟動**選項 頁面會列出在該資料夾中，路徑以及每個.xaml 檔案 — 比方說，%USERPROFILE%\My Documents\Visual Studio *版本*\StartPages\\*檔案名稱*.xaml。 如果您的起始頁包含私用組件的參考，您必須將其複製並貼到位於 \PrivateAssemblies\ 資料夾。  
  
 若要將起始頁，您建立沒有封裝在.vsix 檔案，我們建議，您使用基本的檔案複製策略，例如，批次指令碼或任何其他部署技術，可讓您再將檔案放在所需的目錄。  
  
#### <a name="to-manually-install-a-custom-start-page"></a>若要手動安裝自訂起始頁  
  
1. 複製的.xaml 檔案，包含啟動網頁標記中，以及組件以外的任何支援檔案，並將它們貼到使用者的 \StartPages\ 資料夾。  
  
2. 如果 [啟動] 頁面需要組件，請將其複製並貼到...\\ *Visual Studio 安裝資料夾*\Common7\IDE\PrivateAssemblies\\。  
  
3. 在 **自訂起始頁**上列出**啟動**選項頁面上，選取新的 入門 頁面。 如需詳細資訊，請參閱[自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)   
 [將使用者控制項加入至起始頁](../extensibility/adding-user-control-to-the-start-page.md)
