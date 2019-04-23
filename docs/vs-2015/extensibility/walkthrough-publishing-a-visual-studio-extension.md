---
title: 發行擴充功能 |Microsoft Docs
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046288"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>逐步解說：發佈 Visual Studio 延伸模組
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**注意**：Visual Studio 組件庫會取代 Visual Studio Marketplace。 請參閱本主題的詳細資料的最新版本。

本逐步解說會示範如何將 Visual Studio 延伸模組發佈至 Visual Studio 組件庫。 當您新增您的延伸模組資源庫時，開發人員可以使用**擴充功能和更新**瀏覽是否那里新的和更新擴充功能。

## <a name="prerequisites"></a>必要條件
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。

## <a name="create-a-visual-studio-extension"></a>建立 Visual Studio 擴充功能
 在此情況下，我們將使用預設 VSPackage 擴充功能，但相同的步驟都適用於所有類型的延伸模組。

1. 在 C# 中名為建立 VSPackage`TestPublishing`具有功能表命令。 如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的擴充](../extensibility/creating-an-extension-with-a-menu-command.md)。

## <a name="test-the-extension"></a>測試此擴充功能
 發佈擴充功能之前，請建置並測試它，以確定已正確安裝 Visual Studio 的實驗執行個體中。

1. 在 Visual Studio 中開始偵錯。 若要開啟 Visual Studio 的實驗執行個體。

2. 在實驗執行個體中，移至**工具**功能表，然後按一下**延伸模組管理員**。 TestPublishing 擴充功能應該會出現在中間窗格中，並啟用。

3. 在 [**工具**] 功能表中，請確定您看到 [測試] 命令。

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>將延伸模組發行至 Visual Studio 組件庫
 現在您可以發行延伸模組至 Visual Studio 組件庫。

1. 請確定您已建立您的延伸模組的發行版本，而且它是最新狀態。

2. 在 web 瀏覽器中，開啟[Visual Studio Marketplace](https://marketplace.visualstudio.com/)網站。

3. 按一下右上角**號 IN**。

4. 使用您的 Microsoft 帳戶登入。 如果您沒有 Microsoft 帳戶，您可以在此時建立一個。

5. 按一下 [上傳] 。

6. 在 [**步驟 1:延伸模組型別**，選取**工具**，然後按一下**下一步]**。

7. 在 **步驟 2:上傳**，您可以選擇直接上傳至 Visual Studio 組件庫，或只是將連結新增至您自己的網站。 在此案例中，選取**我想要上傳我的工具**。 **選取您的控制項**方塊隨即出現。 按一下 **瀏覽**，然後選取 TestPublish.vsix \bin\Release 專案的資料夾中。 按 [ **下一步**]。

8. 在 **步驟 3:基本資訊**，會顯示 source.extension.vsixmanifest 檔案中的欄位。 選取適當**分類**並加入**標記**可協助使用者尋找擴充功能。 若要加入更詳細的摘要和描述 （描述必須是至少 280 個字元）。 離開**延伸模組類型**做為**不是 Microsoft 擴充功能**並**成本類別**做為**試用**。

9. 讀取投稿協議，在頁面底部，並檢查**我同意**。

10. 按一下 **建立投稿文章**。 這會顯示您的延伸模組會對 Visual Studio 元件庫，與訊息尚未發行頁面的頁面。

11. 按一下 [發行] 。

12. 搜尋 Visual Studio 組件庫，您的擴充功能。 TestPublish 延伸模組清單應該會出現。

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>從 Visual Studio 組件庫安裝擴充功能
 現在，發佈擴充功能時，將它安裝在 Visual Studio，並測試其存在。

1. 在 Visual Studio 中，在**工具**功能表上，按一下**擴充功能和更新**。

2. 按一下  **Online** TestPublish 然後搜尋。 TestPublish 延伸模組清單應該會出現。

3. 按一下 [ **下載**]。 下載擴充功能之後，按一下 [安裝] 。

4. 若要完成安裝程序，重新啟動 Visual Studio。

## <a name="removing-the-extension"></a>移除延伸模組
 從 Visual Studio 組件庫和您的電腦，您可以移除延伸模組。

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>從 Visual Studio 組件庫中移除擴充功能

1. 開啟[Visual Studio Marketplace](https://marketplace.visualstudio.com/)網站。

2. 按一下右上角**My 副檔名**。 TestPublish 清單隨即顯示。

3. 按一下 [刪除]。

#### <a name="to-remove-the-extension-from-your-computer"></a>若要從電腦移除擴充功能

1. 在 Visual Studio 的 [工具]  功能表上，按一下 [擴充管理員] 。

2. 選取 TestPublish，然後按一下**解除安裝**。

3. 若要完成解除安裝作業，重新啟動 Visual Studio。
