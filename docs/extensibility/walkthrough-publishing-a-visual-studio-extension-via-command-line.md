---
title: 使用命令列發佈延伸模組
description: 瞭解如何使用命令列將延伸模組發佈至 Visual Studio Marketplace，讓開發人員能夠流覽新的和更新的延伸模組。
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: how-to
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98c73da67e607346138d7d6fae124a86b7a34618
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961842"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>逐步解說：透過命令列發佈 Visual Studio 擴充功能

本逐步解說將示範如何使用命令列，將 Visual Studio 擴充功能發佈到 Visual Studio Marketplace。 當您將延伸模組新增至 Marketplace 時，開發人員可以使用 [ [**擴充功能和更新**](../ide/finding-and-using-visual-studio-extensions.md) ] 對話方塊來流覽新的和更新的延伸模組。

VsixPublisher.exe 是用來將 Visual Studio 延伸模組發佈至 Marketplace 的命令列工具。 您可以從 $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe 存取。 此工具上提供的命令為： **publish**、 **createPublisher**、 **deletePublisher**、 **deleteExtension**、 **login**、 **登出**。

## <a name="commands"></a>命令

### <a name="publish"></a>publish

將延伸模組發佈至 Marketplace。 延伸模組可以是 vsix、exe/msi 檔案或連結。 如果已經有相同版本的延伸模組，它會覆寫延伸模組。 如果延伸模組不存在，則會建立新的擴充功能。

|命令選項 |Description |
|---------|---------|
|承載 (必要)  | 要發佈之承載的路徑，或用來作為「更多資訊 URL」的連結。 |
|publishManifest (必要)  | 要使用之發佈資訊清單檔案的路徑。 |
|ignoreWarnings | 發佈延伸模組時要忽略的警告清單。 發佈延伸模組時，這些警告會顯示為命令列訊息。  (例如 "VSIXValidatorWarning01，VSIXValidatorWarning02" ) 
|personalAccessToken | 個人存取權杖 (PAT) 用來驗證發行者。 如果未提供，則會從已登入的使用者取得 PAT。 |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

在 Marketplace 上建立發行者。 也會將「發行者」記錄到電腦中，以供未來的動作 (例如，刪除/發佈延伸模組) 。

|命令選項 |Description |
|---------|---------|
|displayName (必要的)  | 發行者的顯示名稱。 |
|publisherName (必要)  | 發行者的名稱 (例如，識別碼) 。 |
|personalAccessToken (必要)  | 用來驗證發行者的個人存取權杖。 |
|shortDescription | 發行者的簡短描述 (不是檔案) 。 |
|longDescription | 發行者的詳細描述 (不是檔案) 。 |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

刪除 Marketplace 上的發行者。

|命令選項 |Description |
|---------|---------|
|publisherName (必要)  | 發行者的名稱 (例如，識別碼) 。 |
|personalAccessToken (必要)  | 用來驗證發行者的個人存取權杖。 |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

從 Marketplace 刪除擴充功能。

|命令選項 |Description |
|---------|---------|
|extensionName (必要)  | 要刪除的延伸模組名稱。 |
|publisherName (必要)  | 發行者的名稱 (例如，識別碼) 。 |
|personalAccessToken | 用來驗證發行者的個人存取權杖。 如果未提供，則會從已登入的使用者取得 pat。 |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

將發行者記錄至電腦。

|命令選項 |Description |
|---------|---------|
|需要 personalAccessToken ( | 用來驗證發行者的個人存取權杖。 |
|publisherName (必要)  | 發行者的名稱 (例如，識別碼) 。 |
|overwrite | 指定應以新的個人存取權杖覆寫任何現有的發行者。 |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

將發行者登出電腦。

|命令選項 |Description |
|---------|---------|
|publisherName (必要)  | 發行者的名稱 (例如，識別碼) 。 |
|ignoreMissingPublisher | 指定如果指定的發行者尚未登入，則工具不應該發生錯誤。 |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishManifest 檔案

PublishManifest 檔案是由 **publish** 命令使用。 它代表 Marketplace 需要知道之延伸模組的所有中繼資料。 如果要上傳的延伸模組是來自 VSIX 擴充功能，"identity" 屬性必須設定 "internalName"。 這是因為可以從 extension.vsixmanifest 檔產生其餘的 "identity" 屬性。 如果延伸模組是 msi/exe 或連結延伸模組，則使用者必須在 "identity" 屬性中提供必要的欄位。 資訊清單的其餘部分包含 Marketplace (的詳細資訊，例如類別、是否已啟用 Q&A 等等 ) 。

VSIX 擴充功能 publishManifest 檔案範例：

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

MSI/EXE 或連結 publishManifest 檔範例：

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

您可以提供資產檔案，以便在讀我檔案中嵌入影像。 例如，如果某個擴充功能有下列的「總覽」 Markdown 檔：

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

為了解析上述範例中的「映射/testlogo.png」，使用者可以在其發佈資訊清單中提供 "Assetfile"，如下所示：

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

## <a name="publishing-walkthrough"></a>發佈逐步解說

### <a name="prerequisites"></a>必要條件

若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="create-a-visual-studio-extension"></a>建立 Visual Studio 擴充功能

在此情況下，我們會使用預設的 VSPackage 延伸模組，但相同的步驟對每種延伸模組都有效。

1. 在 c # 中建立具有功能表命令的 VSPackage，名為 "TestPublish"。 如需詳細資訊，請參閱 [建立您的第一個延伸模組： Hello World](../extensibility/extensibility-hello-world.md)。

### <a name="package-your-extension"></a>封裝您的延伸模組

1. 使用產品名稱、作者和版本的正確資訊，更新延伸模組 extension.vsixmanifest。

   ![更新擴充功能 extension.vsixmanifest](media/update-extension-vsixmanifest.png)

2. 在 **發行** 模式中建立您的延伸模組。 現在您的延伸模組會封裝為 \bin\Release 資料夾中的 VSIX。

3. 您可以按兩下 VSIX 來確認安裝。

### <a name="test-the-extension"></a>測試擴充功能

 散發延伸模組之前，請先建立並測試它，以確定它已正確安裝在 Visual Studio 的實驗實例中。

1. 在 Visual Studio 中，啟動調試。 開啟 Visual Studio 的實驗實例。

2. 在實驗性實例中，移至 [ **工具** ] 功能表，然後按一下 [ **擴充功能和更新 ...**]。TestPublish 延伸模組應該會出現在中央窗格中，並加以啟用。

3. 在 [ **工具** ] 功能表上，確認您看到 [測試] 命令。

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>透過命令列將延伸模組發佈至 Marketplace

1. 確定您已建立擴充功能的發行版本，而且是最新的。

2. 請確定您已在和 overview.md 檔案上建立 publishmanifest.js。

3. 開啟命令列，然後流覽至 $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\ 目錄。

4. 若要建立新的發行者，請使用下列命令：

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. 成功建立「發行者」時，您會看到下列命令列訊息：

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. 您可以藉由流覽至來確認您所建立的新發行者 [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. 若要發佈新的擴充功能，請使用下列命令：

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. 成功建立「發行者」時，您會看到下列命令列訊息：

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. 您可以藉由流覽至來確認您發行的新延伸模組 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>從 Visual Studio Marketplace 安裝擴充功能

現在擴充功能已發佈，請將它安裝在 Visual Studio 中，並在該處進行測試。

1. 在 Visual Studio 的 [ **工具** ] 功能表上，按一下 [ **擴充功能和更新 ...**]。

2. 按一下 [ **線上** ]，然後搜尋 TestPublish。

3. 按一下 [下載] 。 擴充功能接著會排程安裝。

4. 若要完成安裝，請關閉 Visual Studio 的所有實例。

## <a name="remove-the-extension"></a>移除擴充功能

您可以從 Visual Studio Marketplace 和您的電腦移除擴充功能。

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>透過命令列從 Marketplace 移除擴充功能

1. 如果您想要移除擴充功能，請使用下列命令：

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. 在成功刪除延伸模組時，您會看到下列命令列訊息：

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>從電腦移除擴充功能

1. 在 Visual Studio 中，按一下 [ **工具** ] 功能表上的 [ **擴充功能和更新**]。

2. 選取 [MyVsixExtension]，然後按一下 [ **卸載**]。 然後，將會排定要卸載的擴充功能。

3. 若要完成卸載，請關閉 Visual Studio 的所有實例。
