---
title: 逐步解說：發佈 Visual Studio 延伸模組 |Microsoft Docs
description: 瞭解如何將 Visual Studio 延伸模組發佈至 Visual Studio Marketplace，讓開發人員能夠流覽新的和更新的延伸模組。
ms.custom: SEO-VS-2020
ms.date: 01/15/2021
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bda44c0c3f6c4b1986fc45a7c9cbf5c4ffa83043
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889001"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>逐步解說：發佈 Visual Studio 擴充功能

本逐步解說會示範如何將 Visual Studio 擴充功能發佈到 Visual Studio Marketplace。 當您將延伸模組新增至 Visual Studio Marketplace 時，開發人員可以使用 **擴充功能和更新** 來流覽新的和更新的延伸模組。

## <a name="prerequisites"></a>必要條件

 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-visual-studio-extension"></a>建立 Visual Studio 擴充功能

本文使用預設的 VSPackage 延伸模組，但這些步驟適用于每種擴充功能。

- 使用 `TestPublish` 具有功能表命令的 c # 來建立名為的 VSPackage。 如需詳細資訊，請參閱 [建立您的第一個延伸模組： Hello World](../extensibility/extensibility-hello-world.md)。

## <a name="package-your-extension"></a>封裝您的延伸模組

1. 使用產品名稱、作者和版本的正確資訊，更新 *extension.vsixmanifest* 。

   ![更新擴充功能 extension.vsixmanifest](media/update-extension-vsixmanifest.png)

2. 在 **發行** 模式中建立您的延伸模組。 現在您的延伸模組會封裝為 \bin\Release 資料夾中的 VSIX。

3. 您可以按兩下 VSIX 來確認安裝。

## <a name="test-the-extension"></a>測試擴充功能

 散發延伸模組之前，請先建立並測試它，以確定它已正確安裝在 Visual Studio 的實驗實例中。

1. 在 Visual Studio 中，啟動偵錯工具以開啟 Visual Studio 的實驗實例。

2. 在實驗性實例中，移至 [ **工具** ] 功能表，然後按一下 [ **擴充功能和更新**]。 TestPublish 延伸模組應該會出現在中央窗格中，並加以啟用。

3. 在 [ **工具** ] 功能表上，確認您看到 [測試] 命令。

## <a name="publish-the-extension-to-visual-studio-marketplace"></a>將延伸模組發佈至 Visual Studio Marketplace

1. 確定您已建立擴充功能的發行版本，而且是最新的版本。

2. 在網頁瀏覽器中，移至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。

3. 在右上角按一下 [登 **入**]。

4. 使用您的 Microsoft 帳戶登入。 如果您沒有 Microsoft 帳戶，此時可以建立一個。

5. 按一下 [ **發行延伸** 模組]。 此選項會將您流覽至所有延伸模組的 [管理] 頁面。 如果您沒有發行者帳戶，此時會提示您建立一個。

   ![上傳至 Marketplace](media/upload-to-marketplace.png)

6. 選擇您想要用來上傳擴充功能的發行者。 您可以按一下左側所列的發行者名稱來變更發行者。 按一下 [ **新增延伸** 模組]，然後選取 [ **Visual Studio**]。

7. 在 **[1：上傳延伸** 模組] 中，您可以選擇直接將 VSIX 檔案上傳至 Visual Studio Marketplace，或直接將連結新增至您自己的網站。 在此範例中，會上傳 *TestPublish* 的副檔名。 拖放您的延伸模組，或使用 **點擊** 連結來流覽檔案。 在專案的 \bin\Release 資料夾中尋找您的延伸模組。  按一下 [繼續] 。

8. 在 **2：提供擴充功能詳細資料** 時，會從您的延伸模組中的 *extension.vsixmanifest* 檔案自動填入部分欄位。 尋找下列各項的詳細資料：

    * **內部名稱** 會用於延伸模組詳細資料頁面的 URL 中。 例如，發佈發行者名稱為 "myname" 的延伸模組，並將內部名稱指定為「我的延伸模組」，會產生 \. 您延伸模組詳細資料頁面的 "visualstudio com/items？專案名稱 = myname. myextension" URL。

    * 延伸模組的 **顯示名稱**。 此名稱會自動填入 *extension.vsixmanifest* 檔案。

    * 您要上傳之延伸模組的 **版本** 號碼。 此版本會自動填入 *extension.vsixmanifest* 檔案。

    * **VSIX** 識別碼是 Visual Studio 針對您的延伸模組使用的唯一識別碼。 如果您想要自動更新您的延伸模組，則需要此識別碼。 此識別碼會自動填入 *extension.vsixmanifest* 檔案。

    * 用於延伸模組的 **標誌**。 如果有提供 *extension.vsixmanifest* 檔案，則會自動填入此標誌。

    * 延伸模組用途的 **簡短描述**。 *Extension.vsixmanifest* 檔案會自動填入此描述。

    * 您可以使用 **總覽** 來包含有關延伸模組功能的螢幕擷取畫面和詳細資訊。

    * **支援的 Visual Studio 版本** 可讓您選擇您的延伸模組將使用的 Visual Studio 版本。 您的延伸模組只會安裝到這些版本。

    * **支援的 Visual Studio 版** 可讓您選擇您的延伸模組將使用的 Visual Studio 版本。 您的延伸模組只會安裝到這些版本。

    * **類型**。 最常見的延伸模組類型是 **工具**。

    * **類別目錄**。 最多挑選三個最適合您的延伸模組。

    * **標記** 是可協助使用者找到您的延伸模組的關鍵字。 標籤有助於提高 Visual Studio Marketplace 中擴充功能的搜尋相關性。

    * **定價類別** 是您的延伸模組成本。

    * **原始程式碼存放庫** 可讓您與社區共用原始程式碼的連結。

    * **針對您的延伸模組允許 Q&** ，可讓使用者在您的延伸模組專案頁面上留下問題。

9. 按一下 **[儲存 & 上傳**]。 此選項會將您帶回發行者的 [管理] 頁面。 尚未發行您的延伸模組。

10. 若要發佈您的延伸模組，請以滑鼠右鍵按一下您的延伸模組，然後選取 [ **設為公用**] 若要查看您的延伸模組在 Visual Studio Marketplace 中的外觀，請選取 [ **視圖擴充** 功能]。 若為取得編號，請按一下 [ **報表**]。 若要變更您的延伸模組，請按一下 [ **編輯**]。

    ![擴充功能專案功能表](media/extension-entry-menu.png)

11. 按一下 [ **設為公用**]，您的延伸模組現在是公用的。 搜尋您的延伸模組 Visual Studio Marketplace。

## <a name="update-a-published-extension-in-visual-studio-marketplace"></a>更新 Visual Studio Marketplace 中已發佈的延伸模組

開始之前，請確定您已建立擴充功能的新發行版本，而且是最新的版本。

1.  在網頁瀏覽器中，移至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。

1.  在右上角按一下 [登 **入**]，然後使用您的 Microsoft 帳戶登入。

    :::image type="content" source="media/marketplace-upload-extension.png" alt-text="顯示在檔案總管中選取上傳擴充檔案的螢幕擷取畫面。":::

1.  按一下 [ **發行延伸** 模組]，然後選擇您想要用來上傳更新的延伸模組的發行者。

    :::image type="content" source="media/marketplace-select-extension-version.png" alt-text="醒目提示 [發行延伸模組] 連結之 Visual Studio Marketplace 的螢幕擷取畫面。":::

1.  在您想要更新的延伸模組旁，將滑鼠停留在三個水準點上，然後選擇 [ **編輯**]。

    :::image type="content" source="media/marketplace-select-extension.png" alt-text="顯示選擇要編輯之延伸模組的螢幕擷取畫面。":::

1.  在 **[1：上傳延伸** 模組] 中，在您的 VSIX 檔案名之後，按一下鉛筆圖示以編輯已發佈的延伸模組。

     :::image type="content" source="media/marketplace-edit-extension-details.png" alt-text="顯示按一下鉛筆圖示以編輯擴充功能的螢幕擷取畫面。":::

1.  流覽至更新的延伸模組 VSIX 檔案。 按一下該檔案，然後按一下 [ **開啟**]。

    更新的延伸模組上傳。

    :::image type="content" source="media/marketplace-upload-extension-notification.png" alt-text="上傳已編輯的延伸模組之後，上傳檔案通知的螢幕擷取畫面。":::

1. 在 **2：提供擴充功能詳細資料** 時，某些詳細資料是延伸模組更新的唯讀，或從您的延伸模組中的 *extension.vsixmanifest* 檔案自動填入。 以下是擴充功能詳細資料的詳細資訊：

    - **內部名稱** \*用於延伸模組詳細資料頁面的 URL 中。 例如，發佈發行者名稱為 "myname" 的延伸模組，並將內部名稱指定為「我的延伸模組」，會產生 "marketplace.visualstudio.com/items?itemName=myname.myextension" 的 URL 做為您延伸模組詳細資料頁面的 URL。

    - **顯示名稱** \*的延伸模組。 此名稱會自動填入 *extension.vsixmanifest* 檔案。

    - **版本** \*您正在上傳的擴充功能編號。 此版本會自動填入 *extension.vsixmanifest* 檔案。

    - **VSIX 識別碼** \*這是 Visual Studio 針對您的延伸模組使用的唯一識別碼。 如果您想要自動更新您的延伸模組，則需要此識別碼。 此識別碼會自動填入 *extension.vsixmanifest* 檔案。

    - **標誌** \*用於您的延伸模組。 如果有提供 *extension.vsixmanifest* 檔案，則會自動填入此標誌。

    - **簡短描述** \*擴充功能的功能。 *Extension.vsixmanifest* 檔案會自動填入此描述。

    - 您可以使用 **總覽** 來包含有關延伸模組功能的螢幕擷取畫面和詳細資訊。

    - **支援的 Visual Studio 版本** \*可讓您選擇您的延伸模組將使用的 Visual Studio 版本。 您的延伸模組只會安裝到這些版本。

    - **支援的 Visual Studio 版本** \*可讓您選擇您的延伸模組將使用的 Visual Studio 版本。 您的延伸模組只會安裝在這些版本上。

    - **類型**。 最常見的延伸模組類型是 **工具**。

    - **類別目錄**。 最多挑選三個最適合您的延伸模組。

    - **標記** 是可協助使用者找到您的延伸模組的關鍵字。 標籤有助於提高 Visual Studio Marketplace 中擴充功能的搜尋相關性。

    - **定價類別** 是您的延伸模組成本。

    - **原始程式碼存放庫** 可讓您與社區共用原始程式碼的連結。

    - **針對您的延伸模組允許 Q&** ，可讓使用者在您的延伸模組專案頁面上留下問題。

       \* 此詳細資料無法針對延伸模組更新進行變更。

1. 按一下 **[儲存 & 上傳**]。 此選項會將您帶回發行者的 [管理] 頁面。 尚未發行您的延伸模組。

1. 若要發佈您的延伸模組，請以滑鼠右鍵按一下您的延伸模組，然後選取 [ **設** 為 若要查看您的延伸模組在 Visual Studio Marketplace 中的外觀，請選取 [ **視圖擴充** 功能]。 若為取得編號，請按一下 [ **報告**]。 若要變更您的延伸模組，請按一下 [ **編輯**]。

## <a name="add-additional-users-to-manage-your-publisher-account"></a>新增其他使用者來管理您的發行者帳戶

Visual Studio Marketplace 支援授與其他使用者存取和管理發行者帳戶的許可權。

1. 流覽至您想要新增其他使用者的發行者帳戶。

2. 選取 [ **成員** ]，然後按一下 [ **新增**]。

   ![新增其他使用者](media/add-users.png)

3. 然後，您可以指定您想要新增之使用者的電子郵件地址，並在 [ **選取角色**] 底下授與正確的存取層級。  您可選擇下列選項：

   * **Creator**：使用者可以發行延伸模組，但無法查看或管理其他使用者所發佈的延伸模組。

   * **讀者**：使用者可以查看延伸模組，但無法發行或管理延伸模組。

   * **參與者**：使用者可以發佈和管理延伸模組，但無法編輯發行者設定或管理存取權。

   * **擁有** 者：使用者可以發佈和管理延伸模組、編輯發行者設定，以及管理存取權。

## <a name="install-the-extension-from-visual-studio-marketplace"></a>從 Visual Studio Marketplace 安裝擴充功能

現在擴充功能已發佈，請將它安裝在 Visual Studio 中，並在該處進行測試。

1. 在 Visual Studio 中，按一下 [ **工具** ] 功能表上的 [ **擴充功能和更新**]。

2. 按一下 [ **線上** ]，然後搜尋 **TestPublish**。

3. 按一下 [下載] 。 接著會排定要安裝的延伸模組。

4. 若要完成安裝，請關閉 Visual Studio 的所有實例。

## <a name="remove-the-extension"></a>移除擴充功能

您可以從 Visual Studio Marketplace 和您的電腦移除擴充功能。

### <a name="to-remove-the-extension-from-visual-studio-marketplace"></a>若要從 Visual Studio Marketplace 移除擴充功能

1. 移至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。

2. 在右上角按一下 [ **發行** 延伸模組]。 選擇您用來發行 **TestPublish** 的發行者。 **TestPublish** 的清單隨即出現。

3. 以滑鼠右鍵按一下擴充功能專案，然後按一下 [ **移除**]。 系統會要求您確認是否要移除此延伸模組。 按一下 [確定]  。

### <a name="to-remove-the-extension-from-your-computer"></a>從電腦移除擴充功能

1. 在 Visual Studio 中，按一下 [ **工具** ] 功能表上的 [ **擴充功能和更新**]。

2. 選取 [ **TestPublish** ]，然後按一下 [ **卸載**]。 接著會排定要卸載的擴充功能。

3. 若要完成卸載，請關閉 Visual Studio 的所有實例。
