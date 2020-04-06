---
title: 使用命令列發佈延伸
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40be0252218f39b4ff98b58caedd7f9f20ce6d5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697119"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>演練:通過命令行發佈可視化工作室擴展

本演練演示如何使用命令行將可視化工作室擴展發佈到可視化工作室市場。 將擴展添加到應用商店時,開發人員可以使用[**「擴展和更新**](../ide/finding-and-using-visual-studio-extensions.md)」對話框流覽其中的新擴展和更新的擴展。

VsixPublisher.exe 是用於將可視化工作室擴展發佈到應用商店的命令列工具。 可以從 ${VSInstallDir}VSSDK\VisualStudio 整合的\工具\Bin_VsixPublisher.exe 存取它。 此工具上可用的指令是:**請發佈**、**建立發行者**,**刪除發行者**,**刪除延伸**, 登入,**請登**入 , 請登入 ,**請登入**。

## <a name="commands"></a>命令

### <a name="publish"></a>publish

發佈到應用商店的擴展。 擴展名可以是 vsix、exe/msi 檔案或連結。 如果擴展已使用相同的版本存在,它將覆蓋擴展。 如果擴展不存在,它將創建新擴展。

|指令選項 |描述 |
|---------|---------|
|有效負載(必要) | 要發佈的有效負載的路徑或用作"更多資訊 URL"的連結。 |
|發佈清單(必要) | 要使用的發佈清單檔的路徑。 |
|忽略警告 | 發布擴展時要忽略的警告清單。 發佈擴展時,這些警告顯示為命令行消息。 (例如,"VSIX 驗證器警告 01,VSIX 驗證器警告 02")
|個人存取權杖 | 用於對發佈者進行身份驗證的個人訪問權杖 (PAT)。 如果未提供,則從登錄使用者獲取 PAT。 |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>建立發行者

在應用商店中創建發行者。 還將發佈者記錄到計算機中以進行將來的操作(例如,刪除/發佈擴展)。

|指令選項 |描述 |
|---------|---------|
|顯示名稱(必要) | 顯示發佈者的名稱。 |
|發行者名稱 (必要) | 發行者的名稱(例如標識符)。 |
|個人存取權杖(必要) | 用於對發佈者進行身份驗證的個人訪問權杖。 |
|shortDescription | 發佈者的簡短描述(不是檔)。 |
|長描述 | 發行者(不是檔)的長描述。 |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>刪除發行者

刪除應用商店上的發行者。

|指令選項 |描述 |
|---------|---------|
|發行者名稱 (必要) | 發行者的名稱(例如標識符)。 |
|個人存取權杖(必要) | 用於對發佈者進行身份驗證的個人訪問權杖。 |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>刪除延伸

從應用商店中刪除擴展。

|指令選項 |描述 |
|---------|---------|
|分名(必填) | 要刪除的擴展的名稱。 |
|發行者名稱 (必要) | 發行者的名稱(例如標識符)。 |
|個人存取權杖 | 用於對發佈者進行身份驗證的個人訪問權杖。 如果未提供,則從登錄用戶獲取 pat。 |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

將發行者記錄到計算機中。

|指令選項 |描述 |
|---------|---------|
|個人存取權杖(必要 | 用於對發佈者進行身份驗證的個人訪問權杖。 |
|發行者名稱 (必要) | 發行者的名稱(例如標識符)。 |
|overwrite | 指定任何現有發行者都應使用新的個人訪問權杖進行覆蓋。 |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

將發佈者從計算機中註銷。

|指令選項 |描述 |
|---------|---------|
|發行者名稱 (必要) | 發行者的名稱(例如標識符)。 |
|忽略遺失的發行者 | 指定如果指定的發行者尚未登錄,該工具不應出錯。 |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>發佈清單檔案

**發布**命令使用 publishManifest 檔。 它表示有關應用商店需要知道的擴展的所有元數據。 如果上載的擴展來自 VSIX 擴展,"標識"屬性必須僅設置"內部名稱"。 這是因為可以從 vsixmanifest 檔生成"標識"屬性的其餘部分。 如果擴展是 msi/exe 或連結擴展,則用戶必須在"標識"屬性中提供所需的欄位。 清單的其餘部分包含特定於應用商店的資訊(例如,類別、是否啟用Q&A等)。

VSIX 延伸名稱發布清單檔範例:

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

MSI/EXE 或 LINK 發佈清單檔範例:

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

可以提供資產檔,用於在讀讀檔中嵌入圖像等內容。 例如,如果擴展具有以下「概述」標記文檔:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

為了解決前面的示例中的「圖像/testlogo.png」,用戶可以在其發佈清單中提供「資產檔」,如下所示:

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

## <a name="publishing-walkthrough"></a>發佈演練

### <a name="prerequisites"></a>Prerequisites

若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="create-a-visual-studio-extension"></a>建立視覺化工作室延伸

在這種情況下,我們將使用預設的 VSPackage 擴展,但相同的步驟對於每種擴展都有效。

1. 在 C# 中創建一個 VSPackage,名為"TestPublish",具有功能表命令。 有關詳細資訊,請參閱[創建您的第一個擴展:你好世界](../extensibility/extensibility-hello-world.md)。

### <a name="package-your-extension"></a>封裝您的延伸模組

1. 使用有關產品名稱、作者和版本的正確資訊更新擴展 vsix 清單。

   ![更新延伸 vsixmanifest](media/update-extension-vsixmanifest.png)

2. 在**釋放**模式下生成擴展。 現在,您的擴展將打包為 [bin_釋放資料夾中的 VSIX》。

3. 您可以雙擊 VSIX 以驗證安裝。

### <a name="test-the-extension"></a>測試延伸

 在分發擴展之前,請生成並對其進行測試,以確保它在 Visual Studio 的實驗實例中正確安裝。

1. 在可視化工作室中,開始調試。 打開視覺工作室的實驗實例。

2. 在實驗實例中,轉到 **"工具"** 功能表,然後單擊 **"擴展和更新..."。** 測試發佈擴展應顯示在中心窗格中並啟用。

3. 在 **「工具」** 選單上,請確保看到測試命令。

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>通過命令列將擴展發佈到應用商店

1. 請確保您已構建擴展的發佈版本,並且該版本是最新的。

2. 請確保您已創建 publishmanifest.json 和overview.md檔。

3. 開啟命令列並導航到 $_VSInstallDir_VSSDK_VisualStudio 整合的\工具\Bin_目錄。

4. 要建立新發佈伺服器,請使用以下指令:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. 成功建立發行者時,您將看到以下命令列訊息:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. 您可以通過瀏[覽到 視覺化工作室市場](https://marketplace.visualstudio.com/manage/publishers)來驗證您建立的新發行者

7. 要發佈新延伸,請使用以下命令:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. 成功建立發行者時,您將看到以下命令列訊息:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. 您可以通過導航到[可視化工作室市場](https://marketplace.visualstudio.com/)來驗證發佈的新擴展

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>從視覺化工作室市場安裝擴充

現在,擴展已發佈,請將其安裝在 Visual Studio 中並在那裡進行測試。

1. 在可視化工作室中,在 **"工具"** 功能表上,單擊 **"擴展和更新..."。**

2. 按下 **「連線」 然後**搜尋測試發佈。

3. 按一下 [下載]  。 然後,將計劃安裝擴展。

4. 要完成安裝,關閉可視化工作室的所有實例。

## <a name="remove-the-extension"></a>移除擴充功能

可以從可視化工作室應用商店和電腦中刪除擴展。

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>透過命令列從應用商店中移除擴展

1. 如果要刪除延伸,請使用以下指令:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. 成功刪除延伸後,您將看到以下命令列訊息:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>從電腦中移除副檔名

1. 在可視化工作室中,在 **「工具」** 功能表上,按一下 **「擴展和更新**」。

2. 選擇"MyVsix 擴展",然後單擊 **"卸載**"。 然後,將安排卸載擴展。

3. 要完成卸載,關閉可視化工作室的所有實例。
