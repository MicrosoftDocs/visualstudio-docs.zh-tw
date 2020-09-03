---
title: 發佈延伸模組 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201973"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>逐步解說︰發佈 Visual Studio 延伸模組
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**注意**： Visual Studio Marketplace 將取代 Visual Studio 資源庫。 如需詳細資訊，請參閱本主題的最新版本。

本逐步解說示範如何將 Visual Studio 延伸模組發佈至 Visual Studio 資源庫。 當您將延伸模組新增至資源庫時，開發人員可以使用 **擴充功能和更新** 來流覽新的和更新的延伸模組。

## <a name="prerequisites"></a>Prerequisites
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

## <a name="create-a-visual-studio-extension"></a>建立 Visual Studio 擴充功能
 在此情況下，我們會使用預設的 VSPackage 延伸模組，但相同的步驟對每種延伸模組都有效。

1. 使用 `TestPublishing` 具有功能表命令的 c # 來建立名為的 VSPackage。 如需詳細資訊，請參閱 [使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能。

## <a name="test-the-extension"></a>測試擴充功能
 散發延伸模組之前，請先建立並測試它，以確定它已正確安裝在 Visual Studio 的實驗實例中。

1. 在 Visual Studio 中，啟動調試。 開啟 Visual Studio 的實驗實例。

2. 在實驗性實例中，移至 [ **工具** ] 功能表，然後按一下 [ **擴充管理員**]。 TestPublishing 延伸模組應該會出現在中央窗格中，並加以啟用。

3. 在 [ **工具** ] 功能表上，確認您看到 [測試] 命令。

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>將延伸模組發佈至 Visual Studio 資源庫
 現在您可以將延伸模組發佈至 Visual Studio 資源庫。

1. 確定您已建立擴充功能的發行版本，而且是最新的。

2. 在網頁瀏覽器中，開啟 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 網站。

3. 在右上角按一下 [登 **入**]。

4. 使用您的 Microsoft 帳戶登入。 如果您沒有 Microsoft 帳戶，此時可以建立一個。

5. 按一下 [上傳] 。

6. 在 [**步驟1：擴充功能類型**] 中選取 [**工具**]，然後按 **[下一步]**

7. 在 **[步驟2：上傳**] 中，您可以選擇直接上傳至 Visual Studio 圖庫，或直接將連結新增至您自己的網站。 在此情況下 **，請選取 [我想要上傳我的工具**]。 [ **選取您的控制項** ] 方塊隨即出現。 按一下 [ **流覽]** ，然後在專案的 [\bin\Release] 資料夾中選取 [TestPublish]。 按一下 [下一步]  。

8. 在 [ **步驟3：基本資訊**] 中，會顯示 extension.vsixmanifest 檔案中的欄位。 選取適當的 **類別** ，並新增 **標記** 以協助使用者找到您的延伸模組。 您可能會想要新增更詳細的摘要和描述， (描述的長度必須至少為280個字元) 。 將 **延伸模組類型** 保留為 **不是 Microsoft 擴充** 功能，並將 **成本類別** 保留為 **試用版**。

9. 閱讀頁面底部的投稿合約，並確認 **我同意**。

10. 按一下 [ **建立投稿**]。 這會顯示您的延伸模組將對 Visual Studio 資源庫顯示的頁面，其中包含尚未發行頁面的訊息。

11. 按一下 [發佈] 。

12. 在 Visual Studio 圖庫中搜尋您的延伸模組。 TestPublish 延伸模組的清單應會出現。

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>從 Visual Studio 資源庫安裝擴充功能
 現在擴充功能已發佈，請將它安裝在 Visual Studio 中，並在該處進行測試。

1. 在 Visual Studio 中，按一下 [ **工具** ] 功能表上的 [ **擴充功能和更新**]。

2. 按一下 [ **線上** ]，然後搜尋 TestPublish。 TestPublish 延伸模組的清單應會出現。

3. 按一下 [下載]  。 下載擴充功能之後，按一下 [安裝] ****。

4. 若要完成安裝，請重新開機 Visual Studio。

## <a name="removing-the-extension"></a>移除擴充功能
 您可以從 Visual Studio 資源庫和電腦移除擴充功能。

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>從 Visual Studio 資源庫移除擴充功能

1. 開啟 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 網站。

2. 在右上角，按一下 [我的 **Extenions**]。 TestPublish 的清單隨即顯示。

3. 按一下 **[刪除]** 。

#### <a name="to-remove-the-extension-from-your-computer"></a>從電腦移除擴充功能

1. 在 Visual Studio 的 [工具] **** 功能表上，按一下 [擴充管理員] ****。

2. 選取 [TestPublish]，然後按一下 [ **卸載**]。

3. 若要完成卸載，請重新開機 Visual Studio。
