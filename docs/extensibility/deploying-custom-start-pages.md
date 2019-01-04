---
title: 部署自訂起始頁 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: a350cb906d38baf3b82bf688b431718dab75b376
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865990"
---
# <a name="deploy-custom-start-pages"></a>部署自訂起始頁

使用 VSIX 部署，或將檔案複製到目標電腦上正確的位置，您可以部署自訂起始頁。

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>使用起始頁專案範本的 VSIX 部署

當您使用起始頁專案範本，建立起始頁，然後建置專案時，Visual Studio 會建立 *.vsix*可散發的檔案。 封裝中的 [入門] 頁面 *.vsix*檔案可讓您部署中，根據您的適用對象的下列選項：

-   您可以將放 *.vsix*公用網站或網路共用上的檔案。 當有人開啟檔案時，會自動安裝 [入門] 頁面。

-   您可以上傳 *.vsix*的檔案[Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=123847)網站，使用者可以使用來安裝它**擴充管理員**。

起始頁專案範本會建立一份預設 Visual Studio 起始頁，讓您可以修改複本，並保留原始。

您也可以使用來取得 「 起始頁專案範本**延伸模組管理員**或是從網站下載。

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>不使用起始頁專案範本的 VSIX 部署
 成功的 VSIX 部署需要 VSIX 註冊程序與辨識的資料夾中安裝擴充功能**延伸模組管理員**。 由於起始頁專案範本已經指定正確的資料夾，我們建議您使用，每當您想要封裝的 VSIX 部署擴充功能。 不過，如果您的案例中，您無法使用的範本，您可以建立 VSIX 部署而不使用它。

 若要建立 VSIX 部署，而不需使用起始頁專案範本，請先建立 *.vsix*這兩種方式其中一種方法中的 [入門] 頁面的檔案：

- 藉由將空的 VSIX 專案中的自訂起始頁檔案。 如需詳細資訊，請參閱 < [VSIX 專案範本](../extensibility/vsix-project-template.md)。

- 手動建立 *.vsix*檔案。 若要建立 *.vsix*手動檔案：

  1.  建立*extension.vsixmanifest*檔案並 *[Content_Types].xml*的新資料夾中的檔案。 如需詳細資訊，請參閱 < [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)。

  2.  在 Windows 檔案總管中，以滑鼠右鍵按一下包含兩個 XML 檔案的資料夾中，按一下**傳送到**，然後按一下 壓縮的 (zipped) 資料夾。 重新命名產生 *.zip*的檔案*Filename.vsix*，其中的檔案名稱是可轉散發檔案安裝封裝的名稱。

  Visual Studio 能夠辨識 [入門] 頁面中，如`Content Element`VSIX 資訊清單必須包含`CustomExtension Element`具有`Type`屬性設為`"StartPage"`。 使用 VSIX 部署已安裝的起始頁延伸模組會出現在**自訂起始頁**上列出**啟動**選項頁面中以 **[安裝延伸模組]***延伸模組名稱*。

  如果您的起始頁套件包含組件，您必須先新增繫結路徑註冊，以便 Visual Studio 啟動時可供使用。 若要這樣做，請確定您的套件，包含 *.pkgdef*具有下列資訊的檔案。

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>針對所有使用者的 VSIX 部署
 根據預設，部署 VSIX 封裝中的延伸模組會安裝僅適用於目前的使用者。 您可以建立所有使用者部署，在目標電腦的所有使用者進行的起始頁安裝。

### <a name="to-create-an-all-users-deployment"></a>若要建立的所有使用者部署

1.  開啟*extension.vsixmanifest*程式碼檢視中的檔案。

2.  在 `Identifier`加入 vsix 資訊清單的項目`AllUsers`項目，其值為`true`。

    ```
    <AllUsers>true</AllUsers>
    ```

     這會造成 vsix 安裝程式提示您輸入系統管理員權限，然後再安裝 檔案*\Common7\IDE\Extensions*。

3.  開啟 *.pkgdef*檔案。

4.  修改 *.pkgdef*來設定預設起始頁 HKLM 底下新增下列程式碼，其中*MyStartPage.xaml*名稱 *.xaml*檔案，其中包含您開始頁面。

     [$RootKey$ \StartPage\Default]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     這會告訴 Visual Studio 以查看新的起始頁位置。

## <a name="file-copy-deployment"></a>檔案複製部署
 您不需要建立 *.vsix*檔案來部署自訂起始頁。 相反地，您可以在其中複製標記，並直接在使用者的支援檔案<em>\StartPages\*資料夾。**自訂起始頁</em>* 上列出**啟動**選項頁面上列出每個 *.xaml*該資料夾，以及路徑中的檔案 — 比方說， *%USERPROFILE%\My Documents\Visual Studio {version} \StartPages\\{檔案名稱}.xaml*。 如果您的起始頁包含私用組件的參考，您必須將其複製並貼到 * \PrivateAssemblies\*資料夾。

 若要將您建立而不將它包裝在起始頁 *.vsix*檔案中，我們建議您使用基本的檔案複製策略，例如，批次指令碼，或其他部署技術，可讓您將檔案放在所需的目錄。

### <a name="to-manually-install-a-custom-start-page"></a>若要手動安裝自訂起始頁

1.  複製 *.xaml*檔案，包含起始頁的標記，以及任何支援的檔案以外的組件，並將它們貼在使用者的 * \StartPages\*資料夾。

2.  如果 [啟動] 頁面需要組件，請將其複製並貼到 *...\\{Visual Studio 安裝資料夾} \Common7\IDE\PrivateAssemblies\\*。

3.  在 **自訂起始頁**上列出**啟動**選項頁面上，選取新的 入門 頁面。 如需詳細資訊，請參閱 <<c0> [ 自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)
- [將使用者控制項加入至 [入門] 頁面](../extensibility/adding-user-control-to-the-start-page.md)