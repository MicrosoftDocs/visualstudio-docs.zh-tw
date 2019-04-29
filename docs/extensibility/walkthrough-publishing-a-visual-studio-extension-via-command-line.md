---
title: 逐步解說：發行 Visual Studio 擴充功能，透過命令列 |Microsoft Docs
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2d68554ed982313e631938401f855a47dd9a35a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966262"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>逐步解說：發行的 Visual Studio 擴充功能，透過命令列

本逐步解說示範如何將 Visual Studio 延伸模組發佈至 Visual Studio Marketplace 使用命令列。 當您新增您的延伸模組至 Marketplace 時，開發人員可以使用[**擴充功能和更新**](../ide/finding-and-using-visual-studio-extensions.md)對話方塊，即可瀏覽是否那里新的和更新的延伸模組。

VsixPublisher.exe 是發佈至 Marketplace 的 Visual Studio 擴充功能的命令列工具。 它可以存取的 ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe。 用於此工具的命令是：**發佈**， **createPublisher**， **deletePublisher**， **deleteExtension**， **登入**，**登出**。

## <a name="commands"></a>命令

### <a name="publish"></a>發行

將延伸模組發佈至 Marketplace。 Vsix、 exe/msi 檔案或連結，可以是延伸模組。 如果延伸模組已存在具有相同的版本，它會覆寫擴充功能。 如果延伸模組不存在，它會建立新的延伸模組。

|命令選項 |描述 |
|---------|---------|
|裝載 （必要） | 若要發行裝載或做為 「 詳細資訊 URL 」 的連結可能是路徑。 |
|publishManifest （必要） | 發行路徑資訊清單使用的檔案。 |
|ignoreWarnings | 發行擴充功能時，忽略警告的清單。 發行延伸模組時，這些警告會顯示為命令列的訊息。 (例如，"VSIXValidatorWarning01，VSIXValidatorWarning02")
|personalAccessToken | 個人存取權杖 (PAT)，用來驗證 「 發行者 」。 如果未提供，PAT 會取得從登入的使用者。 |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

在 Marketplace 上建立 「 發行者 」。 也會記錄 「 發行者 」 端插入後續的動作 （例如刪除/發佈擴充功能） 的機器。

|命令選項 |描述 |
|---------|---------|
|displayName （必要） | 發行者顯示名稱。 |
|publisherName （必要） | 「 發行者 」 （例如，識別項） 的名稱。 |
|personalAccessToken （必要） | 個人存取權杖，用來驗證 「 發行者 」。 |
|shortDescription | 「 發行者 」 （不是檔案） 的簡短描述。 |
|longDescription | 「 發行者 」 （不是檔案） 的詳細描述。 |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

刪除在 Marketplace 上的 「 發行者 」。

|命令選項 |描述 |
|---------|---------|
|publisherName （必要） | 「 發行者 」 （例如，識別項） 的名稱。 |
|personalAccessToken （必要） | 個人存取權杖，用來驗證 「 發行者 」。 |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

從 Marketplace 刪除延伸模組。

|命令選項 |描述 |
|---------|---------|
|extensionName （必要） | 若要刪除延伸模組的名稱。 |
|publisherName （必要） | 「 發行者 」 （例如，識別項） 的名稱。 |
|personalAccessToken | 個人存取權杖，用來驗證 「 發行者 」。 如果未提供，pat 會取得從登入的使用者。 |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>登入

登入電腦的 「 發行者 」。

|命令選項 |描述 |
|---------|---------|
|personalAccessToken （必要項 | 個人存取權杖，用來驗證 「 發行者 」。 |
|publisherName （必要） | 「 發行者 」 （例如，識別項） 的名稱。 |
|overwrite | 指定應該在新的個人存取權杖與覆寫任何現有的發行者。 |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>登出

記錄從機器傳出的 「 發行者 」。

|命令選項 |描述 |
|---------|---------|
|publisherName （必要） | 「 發行者 」 （例如，識別項） 的名稱。 |
|ignoreMissingPublisher | 指定此工具應該沒有錯誤，是否指定的發行者是未已登入。 |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishManifest 檔案

PublishManifest 檔案由**發佈**命令。 它代表有關 Marketplace 小組須知的延伸模組的所有中繼資料。 正在上傳的延伸模組是否從 VSIX 擴充功能，「 識別 」 屬性必須只有"internalName 」 設定。 這是因為可以從 vsixmanifest 檔案產生的 「 身分識別 」 屬性的其餘部分。 如果 msi/exe 或連結延伸模組的延伸模組，使用者必須提供必要的欄位中的 「 身分識別 」 屬性。 資訊清單的其餘部分包含特定 Marketplace 資訊 (例如，類別，是否問與答已啟用，等等。)。

VSIX 延伸模組 publishManifest 檔案範例：

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

MSI/EXE 或連結 publishManifest 檔案範例：

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>資產檔案

資產檔案可供讀我檔案中內嵌影像等項目。 例如，如果擴充功能具有下列的 < 概觀 > Markdown 文件：

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

若要解決"images/testlogo.png 」，在上述範例中，使用者可以在提供 「 Assetfile"其發佈像下面資訊清單：

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>發行的逐步解說

### <a name="prerequisites"></a>必要條件

若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="create-a-visual-studio-extension"></a>建立 Visual Studio 擴充功能

在此案例中，我們將使用預設 VSPackage 擴充功能，但相同的步驟都適用於所有類型的延伸模組。

1. 在 C# 中名為"TestPublish 」 具有功能表命令建立 VSPackage。 如需詳細資訊，請參閱[建立您的第一個延伸模組：Hello World](../extensibility/extensibility-hello-world.md)。

### <a name="package-your-extension"></a>封裝您的延伸模組

1. 使用產品名稱、 作者和版本的正確資訊來更新延伸模組 vsixmanifest。

   ![更新延伸模組 vsixmanifest](media/update-extension-vsixmanifest.png)

2. 在建置您的延伸模組**發行**模式。 現在您的延伸模組會封裝成 VSIX \bin\Release 資料夾中。

3. 您可以按兩下來驗證安裝 VSIX。

### <a name="test-the-extension"></a>測試此擴充功能

 發佈擴充功能之前，請建置並測試它，以確定已正確安裝 Visual Studio 的實驗執行個體中。

1. 在 Visual Studio 中開始偵錯。 若要開啟 Visual Studio 的實驗執行個體。

2. 在實驗執行個體中，移至**工具**功能表，然後按一下**擴充功能和更新...**.TestPublish 擴充功能應該會出現在中間窗格中，並啟用。

3. 在 [**工具**] 功能表中，請確定您看到 [測試] 命令。

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>透過命令列在 marketplace 中發行此延伸模組

1. 請確定您已建立您的延伸模組的發行版本，而且它是最新狀態。

2. 請確定您已建立 publishmanifest.json 和 overview.md 檔案。

3. 開啟命令列，然後瀏覽至 ${VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\ 目錄。

4. 若要建立新的發行者，請使用下列命令：

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. 在發行者端成功建立，您會看到下列的命令列訊息：

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. 您可以確認您所瀏覽至您建立新的發行者[Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. 若要發佈新的延伸模組，請使用下列命令：

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. 在發行者端成功建立，您會看到下列的命令列訊息：

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. 您可以確認您所瀏覽至發行新的延伸模組[Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>從 Visual Studio Marketplace 安裝延伸模組

現在，發佈擴充功能時，將它安裝在 Visual Studio，並測試其存在。

1. 在 Visual Studio 中，在**工具**功能表上，按一下 **擴充功能和更新...**.

2. 按一下  **Online** TestPublish 然後搜尋。

3. 按一下 [ **下載**]。 然後，延伸模組會排程進行安裝。

4. 若要完成安裝，請關閉 Visual Studio 的所有執行個體。

## <a name="remove-the-extension"></a>移除擴充功能

從 Visual Studio Marketplace，並從您的電腦，您可以移除延伸模組。

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>從命令列透過 Marketplace 中移除擴充功能

1. 如果您想要移除擴充功能，請使用下列命令：

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. 在成功刪除延伸模組，您會看到下列的命令列訊息：

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>若要從電腦移除擴充功能

1. 在 Visual Studio 中，在**工具**功能表上，按一下**擴充功能和更新**。

2. 選取 「 MyVsixExtension"，然後按一下**解除安裝**。 然後將排程延伸模組解除安裝。

3. 若要完成解除安裝，請關閉所有 Visual Studio 執行個體。
