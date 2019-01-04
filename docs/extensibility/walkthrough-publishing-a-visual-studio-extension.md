---
title: 逐步解說：發行 Visual Studio 擴充功能 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0eef45253ff8d6aa0060c122c5003f8f239e73c5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852449"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>逐步解說：發行 Visual Studio 擴充功能

本逐步解說會示範如何將 Visual Studio 延伸模組發佈至 Visual Studio Marketplace。 當您新增您的延伸模組至 Marketplace 時，開發人員可以使用**擴充功能和更新**瀏覽新的和更新擴充功能。

## <a name="prerequisites"></a>必要條件

 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-visual-studio-extension"></a>建立 Visual Studio 擴充功能

這篇文章會使用預設 VSPackage 擴充功能，但步驟都適用於所有類型的延伸模組。

1. 在 C# 中名為建立 VSPackage`TestPublish`具有功能表命令。 如需詳細資訊，請參閱[建立您的第一個延伸模組：Hello World](../extensibility/extensibility-hello-world.md)。

## <a name="package-your-extension"></a>封裝您的延伸模組

1. 更新延伸模組 *.vsixmanifest*有關產品名稱、 作者和版本的正確資訊。

   ![更新延伸模組 vsixmanifest](media/update-extension-vsixmanifest.png)

2. 在建置您的延伸模組**發行**模式。 現在您的延伸模組會封裝成 VSIX \bin\Release 資料夾中。

3. 您可以按兩下來驗證安裝 VSIX。

## <a name="test-the-extension"></a>測試此擴充功能

 發佈擴充功能之前，請建置並測試它，以確定已正確安裝 Visual Studio 的實驗執行個體中。

1. 在 Visual Studio 中開始偵錯以開啟 Visual Studio 的實驗執行個體。

2. 在實驗執行個體中，移至**工具**功能表，然後按一下**擴充功能和更新**。 TestPublish 擴充功能應該會出現在中間窗格中，並啟用。

3. 在 [**工具**] 功能表中，請確定您看到 [測試] 命令。

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>將延伸模組發行至 Visual Studio Marketplace

1. 請確定您已建立您的延伸模組的發行版本，而且它是最新狀態。

2. 在 web 瀏覽器中，開啟[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)網站。

3. 按一下右上角**登入**。

4. 使用您的 Microsoft 帳戶登入。 如果您沒有 Microsoft 帳戶，您可以在此時建立一個。

5. 按一下 **發行擴充功能**。  此選項可讓您巡覽至所有延伸模組的 [管理] 頁面。 如果您還沒有發佈者帳戶，系統會提示您建立一個在此階段。

   ![上傳至 Marketplace](media/upload-to-marketplace.png)

6. 選擇您想要用來上傳您的延伸模組的發行者。 您可以變更 「 發行者 」 按一下列在左側的 「 發行者 」 名稱。 按一下 **新的延伸模組**，然後選取**Visual Studio**。

7. 在  **1:上傳延伸模組**，您可以選擇直接上傳的 VSIX 檔案到 Visual Studio Marketplace，或只是將連結新增至您自己的網站。 在此範例中，延伸模組*TestPublish.vsix*上傳。 拖放您的延伸模組，或使用**按一下**連結以瀏覽檔案。 您的延伸模組資料夾中找到 \bin\Release 專案。  按一下 [ **繼續**]。

8. 在  **2:提供擴充功能的詳細資訊**，某些欄位會自動填入從*source.extension.vsixmanifest*從您的延伸模組的檔案。 尋找更多詳細資訊如下：

    * **內部名稱**用於擴充功能的詳細資料頁面的 URL。 如需範例，發佈在 「 發行者 」 名稱"myname 」 延伸模組，並指定為"my 擴充功能 」 的內部名稱產生 URL 的"marketplace.visualstudio\.com/items?itemName=myname.myextension 」 擴充功能的詳細資料頁面。
    
    * **顯示名稱**延伸模組。 這個名稱是從自動填入*source.extension.vsixmanifest*檔案。
   
    * **版本**您要上傳擴充功能的數字。 此版本已從自動填入*source.extension.vsixmanifest*檔案。
    
    * **VSIX 識別碼**是 Visual Studio 會使用您的擴充功能的唯一識別碼。 如果您想要自動更新您的延伸模組，這個識別碼是必要的。 這個識別碼是從自動填入*source.extension.vsixmanifest*檔案。
    
   * **標誌**用於您的延伸模組。 此標誌是從自動填入*source.extension.vsixmanifest*檔案提供。
    
     * **簡短描述**您的擴充功能的作用。 這項描述是從自動填入*source.extension.vsixmanifest*檔案。
    
     * **概觀**是包含螢幕擷取畫面以及您的擴充功能的詳細的資訊的好地方。
    
     * **支援的 Visual Studio 版本**可讓您選擇哪一個版本的 Visual Studio 擴充功能將在上運作。 您的延伸模組只會安裝這些版本。
    
     * * * 支援 Visual Studio 版本可讓您選擇哪些版本的 Visual Studio 會作用於您的延伸模組。 您的延伸模組只會安裝這些版本。
    
     * **型別**： 最常見的延伸模組的類型是**工具**。
    
     * **類別**。 挑選最多 3 是最適合您的延伸模組。
    
     * **標記**是關鍵字，協助使用者尋找擴充功能。 標記可協助增加您的擴充功能，在 Marketplace 中搜尋相關性。
    
     * **定價分類**就是您的擴充功能的成本。
    
     * **原始程式碼存放庫**可讓您與社群分享您的程式碼的連結。
    
     * **您的擴充功能可讓問與答**可讓使用者保留在您的延伸模組項目頁面上的問題。

9. 按一下 **儲存並上傳**。 如此的選項會讓您回到您的發行者管理頁面。 您的延伸模組尚未發佈。 若要發佈您的延伸模組，以滑鼠右鍵按一下您的延伸模組並選取**設為公用**。 您可以檢視您的延伸模組的外觀類似 Marketplace 上選取**檢視延伸模組**。 取得數字，按一下**報表**。 若要變更您的延伸模組，請按一下**編輯**。

   ![延伸模組項目功能表](media/extension-entry-menu.png)

10. 按一下後**設為公用**，您的擴充功能現在是公用的。 您的擴充功能在 Visual Studio Marketplace 內搜尋。

## <a name="add-additional-users-to-manage-your-publisher-account"></a>新增其他使用者管理發佈者帳戶

Marketplace 可支援授與其他使用者的權限來存取和管理發佈者帳戶。

1. 瀏覽至您想要新增其他使用者的發佈者帳戶。

2. 選取 **成員**，然後按一下**新增**。

   ![新增額外的使用者](media/add-users.png)

3. 然後，您可以指定您想要新增並授與正確的層級的存取權之使用者的電子郵件地址**選取角色**。  您可以從下列選項中選擇：

   * **建立者**:使用者可發行擴充功能，但是您無法檢視或管理其他使用者所發行的擴充功能。
  
   * **讀取器**:使用者可以檢視擴充功能，但無法發行或管理擴充功能。
  
   * **參與者**:使用者可以發佈和管理擴充功能，但無法編輯發行者設定或管理存取權。
  
   * **擁有者**:使用者可以發佈和管理擴充功能、 編輯發行者設定和管理存取權。
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>從 Visual Studio Marketplace 安裝延伸模組

現在，發佈擴充功能時，將它安裝在 Visual Studio，並測試其存在。

1. 在 Visual Studio 中，在**工具**功能表上，按一下**擴充功能和更新**。

2. 按一下 **線上**，然後搜尋**TestPublish**。

3. 按一下 [ **下載**]。 然後，延伸模組已排程進行安裝。

4. 若要完成安裝，請關閉 Visual Studio 的所有執行個體。

## <a name="remove-the-extension"></a>移除擴充功能

從 Visual Studio Marketplace，並從您的電腦，您可以移除延伸模組。

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>從 Visual Studio Marketplace 中移除擴充功能

1. 開啟[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)網站。

2. 按一下右上角**發佈**延伸模組。 選取之發行者的您用來發行**TestPublish**。 列出**TestPublish**隨即出現。

3. 延伸模組項目上按一下滑鼠右鍵，然後按一下 **移除**。 系統會要求您確認是否您想要移除擴充功能。 按一下 [確定 **Deploying Office Solutions**]。

### <a name="to-remove-the-extension-from-your-computer"></a>若要從電腦移除擴充功能

1. 在 Visual Studio 中，在**工具**功能表上，按一下**延伸模組和更新**。

2. 選取  **TestPublish** ，然後按一下**解除安裝**。 然後延伸模組已排程解除安裝。

3. 若要完成解除安裝，請關閉所有 Visual Studio 執行個體。
