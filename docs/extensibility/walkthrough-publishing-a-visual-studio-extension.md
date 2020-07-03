---
title: 逐步解說：發行 Visual Studio 延伸模組 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6bd7a5d9622f7aea7382522dcf69ce660b61ae7
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904740"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>逐步解說：發行 Visual Studio 延伸模組

本逐步解說將示範如何將 Visual Studio 擴充功能發行至 Visual Studio Marketplace。 當您將擴充功能新增至 Marketplace 時，開發人員可以使用 [**擴充功能和更新**] 來流覽新的和更新的延伸模組。

## <a name="prerequisites"></a>必要條件

 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-visual-studio-extension"></a>建立 Visual Studio 擴充功能

本文使用預設的 VSPackage 延伸模組，但這些步驟對每種延伸模組都是有效的。

1. 在 c # 中建立名為 `TestPublish` 的 VSPackage，其具有功能表命令。 如需詳細資訊，請參閱[建立您的第一個延伸模組： Hello World](../extensibility/extensibility-hello-world.md)。

## <a name="package-your-extension"></a>封裝您的延伸模組

1. 使用產品名稱、作者和版本的正確資訊來更新*extension.vsixmanifest* 。

   ![更新延伸模組 extension.vsixmanifest](media/update-extension-vsixmanifest.png)

2. 以**發行**模式建立您的擴充功能。 現在您的擴充功能會封裝為 \bin\Release 資料夾中的 VSIX。

3. 您可以按兩下 VSIX 來確認安裝。

## <a name="test-the-extension"></a>測試延伸模組

 散發延伸模組之前，請先建立並測試它，以確定它已正確安裝在 Visual Studio 的實驗實例中。

1. 在 Visual Studio 中，啟動 [偵錯工具] 以開啟 Visual Studio 的實驗實例。

2. 在實驗實例中，移至 [**工具**] 功能表，然後按一下 [**擴充功能和更新**]。 TestPublish 延伸模組應會出現在中央窗格中，並加以啟用。

3. 請在 [**工具**] 功能表上，確定您看到 [測試] 命令。

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>將擴充功能發佈至 Visual Studio Marketplace

1. 請確定您已建立擴充功能的發行版本，而且該版本是最新的。

2. 在網頁瀏覽器中，開啟[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)網站。

3. 按一下右上角的 [登**入**]。

4. 使用您的 Microsoft 帳戶登入。 如果您沒有 Microsoft 帳戶，您可以在此時建立一個。

5. 按一下 [**發行延伸**模組]。  此選項會將您流覽至所有延伸模組的 [管理] 頁面。 如果您沒有發行者帳戶，此時系統會提示您建立一個。

   ![上傳至 Marketplace](media/upload-to-marketplace.png)

6. 選擇您想要用來上傳擴充功能的發行者。 您可以按一下左側所列的發行者名稱來變更發行者。 按一下 [**新增擴充**功能]，然後選取 [ **Visual Studio**]。

7. 在**1：上傳延伸**模組中，您可以選擇直接將 VSIX 檔案上傳至 Visual Studio Marketplace，或只是將連結新增至您自己的網站。 在此範例中，會上傳擴充功能*TestPublish* 。 拖放您的擴充功能，或使用**按一下**連結流覽檔案。 在專案的 [\bin\Release] 資料夾中尋找您的擴充功能。  按一下 [繼續] 。

8. 在**2：提供延伸模組詳細資料**中，會從您的延伸模組中的*extension.vsixmanifest*檔案自動填入部分欄位。 如需詳細資訊，請查看下列各項：

    * **內部名稱**用於延伸模組詳細資料頁面的 URL。 例如，發佈發行者名稱為 "myname" 的延伸模組，並將內部名稱指定為「我的延伸模組」，會產生 \. 您延伸模組詳細資料頁面的 URL "visualstudio com/items？專案名稱 = myname. myextension"。

    * 延伸模組的**顯示名稱**。 這個名稱會自動填入*extension.vsixmanifest*檔案。

    * 您要上傳之延伸模組的**版本**號碼。 會從*extension.vsixmanifest*檔案自動填入此版本。

    * **VSIX ID**是 Visual Studio 用於擴充功能的唯一識別碼。 如果您想要自動更新延伸模組，則需要此識別碼。 此識別碼會從*extension.vsixmanifest*檔案自動填入。

    * 用於擴充功能的**標誌**。 如果提供，則會從*extension.vsixmanifest*檔案自動填入此標誌。

    * 擴充功能的**簡短描述**。 此描述會從*extension.vsixmanifest*檔案自動填入。

    * **總覽**是包含螢幕擷取畫面的好地方，以及您的擴充功能的詳細資訊。

    * **支援的 Visual Studio 版本**可讓您選擇擴充功能所要使用的 Visual Studio 版本。 您的延伸模組只會安裝到這些版本。

    * * * 支援的 Visual Studio 版本可讓您選擇擴充功能所要使用的 Visual Studio 版本。 您的延伸模組只會安裝到這些版本。

    * [類型]****。 最常見的延伸模組類型是**工具**。

    * **類別**。 最多挑選三個最適合您的延伸模組。

    * **標記**是可協助使用者尋找您的擴充功能的關鍵字。 標籤有助於增加您在 Marketplace 中擴充功能的搜尋相關性。

    * **定價類別**是您的延伸模組成本。

    * **原始程式碼存放庫**可讓您與該社區共用原始程式碼的連結。

    * **針對您的擴充功能允許問&A** ，讓使用者在您的延伸模組輸入頁面上留下問題。

9. 按一下 **[儲存 & 上傳**]。 此選項會將您帶回發行者的 [管理] 頁面。 您的延伸模組尚未發佈。 若要發佈擴充功能，請以滑鼠右鍵按一下您的擴充功能，然後選取 [**設為公用**]。 您可以藉由選取 [ **View extension**]，來查看您的延伸模組在 Marketplace 上的外觀。 針對取得號碼，按一下 [**報表**]。 若要對您的擴充功能進行變更，請按一下 [**編輯**]。

   ![擴充功能專案功能表](media/extension-entry-menu.png)

10. 按一下 [**設為公用**] 之後，您的延伸模組現在是公用的。 搜尋您的擴充功能 Visual Studio Marketplace。

## <a name="add-additional-users-to-manage-your-publisher-account"></a>新增額外的使用者以管理您的發行者帳戶

Marketplace 支援授與其他使用者存取和管理發行者帳戶的許可權。

1. 流覽至您想要新增其他使用者的發行者帳戶。

2. 選取 [**成員**]，然後按一下 [**新增**]。

   ![新增其他使用者](media/add-users.png)

3. 接著，您可以指定您想要新增之使用者的電子郵件地址，並在 [**選取角色**] 底下授與正確的存取層級。  您可選擇下列選項：

   * 建立**者**：使用者可以發行延伸模組，但無法查看或管理其他使用者所發行的延伸模組。

   * **讀者**：使用者可以查看延伸模組，但無法發行或管理延伸模組。

   * **參與者**：使用者可以發行和管理延伸模組，但無法編輯發行者設定或管理存取權。

   * **擁有**者：使用者可以發行和管理擴充功能、編輯發行者設定，以及管理存取權。

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>從 Visual Studio Marketplace 安裝延伸模組

既然已發行延伸模組，請將它安裝在 Visual Studio 中，然後在該處進行測試。

1. 在 Visual Studio 的 [**工具**] 功能表上，按一下 [**擴充功能和更新**]。

2. 按一下 [**線上**]，然後搜尋**TestPublish**。

3. 按一下 [下載] 。 接著會排程安裝的延伸模組。

4. 若要完成安裝，請關閉 Visual Studio 的所有實例。

## <a name="remove-the-extension"></a>移除擴充功能

您可以從 Visual Studio Marketplace 和您的電腦中移除延伸模組。

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>若要從 Visual Studio Marketplace 移除延伸模組

1. 開啟[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)網站。

2. 按一下右上角的 [**發行**延伸模組]。 挑選您用來發佈**TestPublish**的發行者。 **TestPublish**的清單隨即出現。

3. 在延伸模組專案上按一下滑鼠右鍵，然後按一下 [**移除**]。 系統會要求您確認是否要移除此延伸模組。 按一下 [確定] 。

### <a name="to-remove-the-extension-from-your-computer"></a>若要從您的電腦移除延伸模組

1. 在 Visual Studio 的 [**工具**] 功能表上，按一下 [**擴充功能和更新**]。

2. 選取 [ **TestPublish** ]，然後按一下 [**卸載**]。 接著會針對卸載排程此延伸模組。

3. 若要完成卸載，請關閉 Visual Studio 的所有實例。
