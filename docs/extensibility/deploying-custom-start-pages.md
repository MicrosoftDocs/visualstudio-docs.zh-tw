---
title: 部署自訂起始頁 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6110be404ec7de9b52aef23fc9d1d77d1ae7e2c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-custom-start-pages"></a>部署自訂起始頁
使用 VSIX 部署，或將檔案複製到目標電腦上的正確位置，您可以部署自訂起始頁。  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>VSIX 部署使用起始頁專案範本  
 當您使用起始頁專案範本，建立起始頁，然後建置專案時，Visual Studio 會建立可散發.vsix 檔案。 包裝在.vsix 檔案中的起始頁，提供您部署，根據您的適用對象的下列選項：  
  
-   在網路共用或公用網站上，您可以將.vsix 檔案。 當其他人開啟檔案時，會自動安裝起始頁。  
  
-   您可以上傳.vsix 檔案[Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=123847)網站，使用者可以使用來安裝它**擴充管理員**。  
  
 起始頁專案範本會建立一份預設 Visual Studio 起始頁，讓您可以修改複本，並保留原始。  
  
 您可以使用來取得起始頁專案範本**擴充管理員**或從網站下載。  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>VSIX 部署，而不使用起始頁專案範本  
 成功的 VSIX 部署需要辨識 VSIX 註冊程序與資料夾中安裝擴充**擴充管理員**。 由於起始頁專案範本已指定正確的資料夾，因此我們建議您使用它每當您想要擴充功能的 VSIX 部署封裝。 不過，如果您有的案例，您無法使用範本，您可以建立 VSIX 部署而不需要使用它。  
  
 若要建立 VSIX 部署，而不使用起始頁專案範本，首先建立這兩種方式之一起始頁的.vsix 檔案：  
  
-   將自訂起始頁檔案加入至空白的 VSIX 專案。 如需詳細資訊，請參閱[VSIX 專案範本](../extensibility/vsix-project-template.md)。  
  
-   藉由手動建立.vsix 檔案。 若要手動建立.vsix 檔：  
    
    1.  Extension.vsixmanifest 檔案和 [Content_Types].xml 檔案在中建立新的資料夾。 如需詳細資訊，請參閱[VSIX 套件的剖析](/visualstudio/extensibility/anatomy-of-a-vsix-package)。  
  
    2.  在 Windows 檔案總管] 中，以滑鼠右鍵按一下包含兩個 XML 檔案的資料夾、 按一下 [傳送到，然後按一下壓縮 (zipped) 資料夾。 重新產生的.zip 檔案命名為 Filename.vsix，其中 Filename 是可轉散發檔案安裝封裝的名稱。  
  
 適用於 Visual Studio 辨識起始頁`Content Element`VSIX 資訊清單必須包含`CustomExtension Element`具有`Type`屬性設為`"StartPage"`。 使用 VSIX 部署已安裝的起始頁擴充功能會出現在**自訂起始頁**清單**啟動**選項頁面上為**[安裝延伸模組]***副檔名*。  
  
 如果您的起始頁封裝包含組件，您必須加入繫結路徑的登錄，以便他們可以使用 Visual Studio 啟動時。 若要這樣做，請確定您的封裝包含.pkgdef 檔具有下列資訊。  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>VSIX 部署的所有使用者  
 根據預設，在 VSIX 封裝中部署延伸模組安裝只針對目前的使用者。 您可以建立所有使用者部署，讓起始頁安裝目標電腦的所有使用者。  
  
##### <a name="to-create-an-all-users-deployment"></a>若要建立的所有使用者部署  
  
1.  在程式碼檢視中開啟 extension.vsixmanifest 檔案。  
  
2.  在`Identifier`加入 vsix 資訊清單的項目`AllUsers`具有值的項目`true`。  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     這會導致提示系統管理員權限，輸入，然後將檔案安裝到 \Common7\IDE\Extensions vsix 安裝程式。  
  
3.  開啟.pkgdef 檔。  
  
4.  修改來設定預設起始頁 HKLM 底下加入下列程式碼，.pkgdef 其中*MyStartPage.xaml*是包含您的起始頁的.xaml 檔案的名稱。  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     這會告訴 Visual 名人新起始頁的位置中尋找。  
  
## <a name="file-copy-deployment"></a>檔案複製部署  
 您沒有建立部署自訂起始頁的.vsix 檔案。 相反地，您可以直接將使用者的 \StartPages\ 資料夾複製標記和支援檔案。 **自訂起始頁**清單**啟動**選項 頁面會列出該資料夾，以及路徑的每個.xaml 檔案 — 例如，%USERPROFILE%\My Documents\Visual Studio *版本*\StartPages\\*檔案名稱*.xaml。 如果您的起始頁包含私用組件的參考，您必須將它們複製，並將它們貼 \PrivateAssemblies\ 資料夾中。  
  
 若要將起始頁，您建立封裝沒有它在.vsix 檔案中，我們建議，您使用基本檔案複製策略，例如，批次指令碼或任何其他部署技術，可讓您再將檔案放在所需的目錄。  
  
#### <a name="to-manually-install-a-custom-start-page"></a>若要手動安裝自訂起始頁  
  
1.  複製的.xaml 檔案，包含起始頁標記，以及任何支援的檔案以外的組件，並將其貼到使用者的 \StartPages\ 資料夾。  
  
2.  如果起始頁需要組件，請將它們複製和貼上在資料庫...\\ *Visual Studio 安裝資料夾*\Common7\IDE\PrivateAssemblies\\。  
  
3.  在**自訂起始頁**清單**啟動**選項頁面上，選取新起始頁。 如需詳細資訊，請參閱[自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)   
 [將使用者控制項加入至起始頁](../extensibility/adding-user-control-to-the-start-page.md)