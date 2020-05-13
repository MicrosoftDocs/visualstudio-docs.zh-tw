---
title: 部署自定義起始頁 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 210b4589c0e2165af537c3fa9129affb06197e9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712233"
---
# <a name="deploy-custom-start-pages"></a>部署自訂起始頁

您可以透過使用 VSIX 部署或將檔案複製到目標電腦上的正確位置來部署自訂起始頁。

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>使用「開始頁」專案樣本進行 VSIX 部署

當您使用「開始頁」專案範本建立「開始頁」,然後生成專案時,Visual Studio 將創建一個可以分發的 *.vsix*檔。 在 *.vsix*檔案中打包起始頁可為您提供以下部署選項,具體取決於您的目標受眾:

- 您可以將 *.vsix*檔案放在網路共享上或公共網站上。 當有人打開該檔時,將自動安裝"開始頁"。

- 您可以將 *.vsix*檔上傳到[可視化工作室應用商店](https://marketplace.visualstudio.com/)網站,以便使用者可以使用**擴展管理器**安裝該檔。

"開始頁"專案範本創建預設可視化工作室起始頁的副本,以便您可以修改副本並保留原始副本。

您可以使用**延伸管理器**或從網站下載"開始頁"專案範本。

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>不使用「開始頁」專案樣本進行 VSIX 部署
 成功的 VSIX 部署需要將擴展安裝在 VSIX 註冊過程和**擴展管理器**識別的資料夾中。 由於「開始頁」專案樣本已指定正確的資料夾,因此我們建議您在要打包 VSIX 部署擴展時使用它。 但是,如果您有無法使用範本的情況,則可以創建 VSIX 部署而不使用它。

 要建立 VSIX 部署而不使用「開始頁」專案樣本,請首先透過以下兩種方式為起始頁建立 *.vsix*檔案:

- 通過將自訂「開始頁」檔案添加到空的 VSIX 專案中。 有關詳細資訊,請參閱[VSIX 專案樣本](../extensibility/vsix-project-template.md)。

- 以手動創建 *.vsix*檔案。 要手動建立 *.v6*檔,請執行操作:

   1. 在新資料夾中建立*擴展.vsixmanifest*檔案和 *[Content_Types]xml*檔案。 有關詳細資訊,請參閱[VSIX 套件的分析](../extensibility/anatomy-of-a-vsix-package.md)。

   2. 在 Windows 資源管理器中,右鍵按一下包含兩個 XML 檔的資料夾,按下「**發送到**」,然後單擊「壓縮(壓縮)資料夾」。 將產生的 *.zip*檔案重新命名為*Filename.vsix,* 其中 Filename 是安裝套件的可再分發檔的名稱。

Visual Studio`Content Element`要識別 起始頁,VSIX 清單`CustomExtension Element``Type`必須包含`"StartPage"`的屬性 設定為的 。 使用 VSIX 部署安裝的開始頁面延伸頁會顯示在 **「啟動**」選項**頁上的「自訂起始頁**」 清單中,作為 **[已安裝副檔名]** *副檔名*。

如果「開始頁」包包含程式集,則必須添加綁定路徑註冊,以便在 Visual Studio 啟動時它們可用。 為此,請確保您的包包含包含以下資訊的 *.pkgdef*檔。

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>所有使用者的 VSIX 部署
 預設情況下,在 VSIX 包中部署的擴展僅針對當前使用者安裝。 您可以通過創建所有使用者部署,為目標電腦的所有使用者安裝"開始頁"。

### <a name="to-create-an-all-users-deployment"></a>建立所有使用者部署

1. 在代碼檢視中打開*副檔名.vsixmanifest*檔案。

2. 在`Identifier`vsix 清單的元素中`AllUsers`,添加值為的`true`元素。

    ```
    <AllUsers>true</AllUsers>
    ```

     這會導致 vsix 安裝程式提示管理員權限,然後將檔案安裝到*Common7_IDE裝置延伸*。

3. 打開 *.pkgdef*檔。

4. 通過添加以下內容,修改 *.pkgdef*以設置 HKLM 下的預設起始頁,其中*MyStartPage.xaml*是包含"開始頁"的 *.xaml*檔的名稱。

     [$RootKey$_開始頁\預設]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml"*

     這告訴 Visual Studio 在新的「開始頁」位置查看。

## <a name="file-copy-deployment"></a>檔案副本部署
 您不必創建 *.vsix*檔來部署自定義"開始頁" 相反,您可以將標記和支援檔案直接複製到使用者的<em>\*@StartPages 資料夾中。啟動選項頁上的 >*自訂起始頁</em>* 清單列出該資料夾中的每個 *.xaml*檔案以及路徑 — 例如 *,%USERPROFILE%%\我的文檔_Visual\\Studio [版本][起始頁 ]檔案名稱\.xaml*。 **Startup** 如果「開始頁」包含對專用程式集的引用,則必須複製它們並將其貼上到_PrivateAssemblies\*資料夾中。

 要分發建立「開始頁」而不將其打包到 *.vsix*檔中,我們建議您使用基本檔案複製策略,例如批處理腳本或任何其他部署技術,以便將檔放入所需的目錄中。

### <a name="to-manually-install-a-custom-start-page"></a>手動安裝自訂起始頁

1. 複製包含「開始頁」標記的 *.xaml*檔以及程式集以外的任何支援檔,並將其貼上到使用者\*的@StartPages資料夾中。

2. 如果"開始頁"需要程式集,請複製它們並將其粘貼到*中。{可檢視化工作室安裝資料夾}公共7_IDE_私有程式集\\ \\ *

3. 在 **「啟動」選項**「頁上的 **」自訂起始頁**「清單中,選擇新的」開始頁」。。 有關詳細資訊,請參閱[自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [自訂「開始」頁](../ide/customizing-the-start-page-for-visual-studio.md)
- [將使用者控制件添加到"開始頁面"](../extensibility/adding-user-control-to-the-start-page.md)
