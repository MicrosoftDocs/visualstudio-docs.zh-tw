---
title: 部署自訂起始頁 |Microsoft Docs
description: 瞭解如何使用 VSIX 部署來部署自訂起始頁，或將檔案複製到目的電腦上的正確位置。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: a356fe3dadaf0eca4f0b4d0f2a7d17f0b475acfb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061403"
---
# <a name="deploy-custom-start-pages"></a>部署自訂起始頁

您可以使用 VSIX 部署或將檔案複製到目的電腦上的正確位置，以部署自訂起始頁。

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>使用起始頁專案範本進行 VSIX 部署

當您使用起始頁專案範本建立起始頁，然後建立專案時，Visual Studio 會建立可散發的 *.vsix* 檔案。 將起始頁封裝在 *.vsix* 檔案中，會根據您的目標物件提供下列部署選項：

- 您可以將 *.vsix* 檔案放在網路共用或公用網站上。 當有人開啟檔案時，就會自動安裝 [開始] 頁面。

- 您可以將 *.vsix* 檔上傳至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 的網站，讓使用者可以使用 [ **擴充管理員**] 進行安裝。

起始頁專案範本會建立預設 Visual Studio 起始頁的複本，讓您可以修改複製並保留原始的複本。

您可以使用 [ **擴充管理員** ] 或從網站下載起始頁專案範本，來取得該範本。

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>不使用起始頁專案範本進行 VSIX 部署
 成功的 VSIX 部署需要將擴充功能安裝在 VSIX 登錄程式和 **延伸模組管理員** 所能辨識的資料夾中。 由於起始頁專案範本已指定正確的資料夾，因此當您想要封裝 VSIX 部署的擴充功能時，建議您使用它。 但是，如果您無法使用範本，您可以在不使用範本的情況下建立 VSIX 部署。

 若要在不使用起始頁專案範本的情況下建立 VSIX 部署，請先使用下列兩種方式之一來建立起始頁的 *.vsix* 檔案：

- 將自訂起始頁檔加入至空白的 VSIX 專案。 如需詳細資訊，請參閱 [VSIX 專案範本](../extensibility/vsix-project-template.md)。

- 藉由手動建立 *.vsix* 檔案。 若要手動建立 *.vsix* 檔：

   1. 在新的資料夾中建立 *extension.vsixmanifest* 檔案和 *[Content_Types] .xml* 檔案。 如需詳細資訊，請參閱 [VSIX 封裝的剖析](../extensibility/anatomy-of-a-vsix-package.md)。

   2. 在 Windows 檔案總管中，以滑鼠右鍵按一下包含這兩個 XML 檔案的資料夾，按一下 [ **傳送到**]，然後按一下 [壓縮的 (壓縮) 資料夾]。 將產生的 *.zip* 檔案重新命名為 *檔案名 .Vsix*，其中 filename 是安裝套件之可轉散發檔案的名稱。

為了讓 Visual Studio 辨識起始頁， `Content Element` VSIX 資訊清單的必須包含將 `CustomExtension Element` `Type` 屬性設為的 `"StartPage"` 。 使用 VSIX 部署安裝的起始頁延伸，會顯示在 [**啟動** 選項] 頁面上的 [**自訂起始頁**] 清單中，顯示為 **[已安裝的延伸模組]** *延伸模組名稱*。

如果您的起始頁封裝包含元件，則必須新增系結路徑註冊，以便在 Visual Studio 啟動時可以使用這些元件。 若要這樣做，請確定您的套件包含具有下列資訊的 *.pkgdef* 檔案。

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>適用于所有使用者的 VSIX 部署
 根據預設，部署在 VSIX 套件中的延伸模組只會針對目前的使用者進行安裝。 您可以建立 All-Users 部署，為目的電腦的所有使用者建立起始頁安裝。

### <a name="to-create-an-all-users-deployment"></a>建立 All-Users 部署

1. 在程式碼視圖中開啟 *extension.vsixmanifest* 檔案。

2. 在 `Identifier` vsix 資訊清單的元素中，加入 `AllUsers` 具有值的元素 `true` 。

    ```
    <AllUsers>true</AllUsers>
    ```

     這會導致 vsix 安裝程式提示您輸入系統管理員許可權，然後將檔案安裝至 *\Common7\IDE\Extensions*。

3. 開啟 *.pkgdef* 檔案。

4. 藉由新增下列程式來修改 *.pkgdef* ，以設定 HKLM 底下的預設起始頁，其中 *MyStartPage* 是包含起始頁的 *.xaml 檔案名。*

     [$RootKey $ \StartPage\Default]

     "Uri" = "$PackageFolder $ \\ *MyStartPage .xaml*"

     這會告訴 Visual Studio 查看新的起始頁位置。

## <a name="file-copy-deployment"></a>檔案複製部署
 您不需要建立 *.vsix* 檔案來部署自訂起始頁。 相反地，您可以將標記和支援檔案直接複製到使用者的 <em>\StartPages \* 資料夾中。[啟動選項] 頁面上的 [*自訂起始頁</em>* ] 清單會列出該資料夾中的每個 *.xaml* 檔案，以及路徑，例如 *%USERPROFILE%\My Documents\Visual Studio {version} \StartPages \\ {file Name} .xaml*.  如果您的起始頁包含私用元件的參考，您必須複製這些元件，並將其貼到 * \PrivateAssemblies \* 資料夾中。

 若要散發您所建立的起始頁，而不將它封裝在 *.vsix* 檔案中，建議您使用基本的檔案複寫原則，例如批次腳本，或任何其他可讓您將檔案放在必要目錄中的部署技術。

### <a name="to-manually-install-a-custom-start-page"></a>手動安裝自訂起始頁

1. 複製包含起始頁標記的 *.xaml* 檔案，連同元件以外的任何支援檔案，然後將它們貼到使用者的 * \StartPages \* 資料夾中。

2. 如果起始頁需要元件，請複製並貼上 *。 \\{Visual Studio 安裝資料夾} \Common7\IDE\PrivateAssemblies \\*。

3. 在 [**啟動** 選項] 頁面的 [**自訂起始頁**] 清單中，選取新的起始頁。 如需詳細資訊，請參閱 [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)
- [將使用者控制項新增至起始頁](../extensibility/adding-user-control-to-the-start-page.md)
