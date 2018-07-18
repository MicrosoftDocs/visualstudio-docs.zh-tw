---
title: 逐步解說： 發行 Visual Studio 擴充功能 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: f823334f3686bdba3406daac69b2a98d203780a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147062"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>逐步解說： 發行 Visual Studio 擴充功能

本逐步解說將示範如何將 Visual Studio 擴充功能發行至 Visual Studio Marketplace。 當您將您的擴充功能加入至 Marketplace 時，開發人員可以使用**擴充功能和更新**瀏覽是否那里新的和更新擴充功能。

## <a name="prerequisites"></a>必要條件

 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-visual-studio-extension"></a>建立 Visual Studio 擴充功能

在此情況下，我們將使用預設 VSPackage 的延伸模組，但相同的步驟適用於每種延伸模組。

1. 在 C# 中名為"TestPublish 」 具有功能表命令建立 VSPackage。 如需詳細資訊，請參閱[建立您的第一個延伸模組： Hello World](../extensibility/extensibility-hello-world.md)。

## <a name="package-your-extension"></a>將擴充功能封裝

1. 更新擴充功能 vsixmanifest 與產品名稱、 作者和版本的正確資訊。

  ![更新擴充功能 vsixmanifest](media/update-extension-vsixmanifest.png)

2. 建置您的擴充功能**發行**模式。 現在您的延伸模組會封裝為 VSIX \bin\Release 資料夾中。

3. 您可以按兩下此 VSIX，若要確認安裝。

## <a name="test-the-extension"></a>測試擴充功能

 發佈擴充功能之前，建置和測試以確定它已正確安裝 Visual Studio 的實驗執行個體中。

1. 在 Visual Studio 中，開始偵錯。 若要開啟的 Visual Studio 的實驗執行個體。

2. 在實驗執行個體中，移至**工具**功能表，然後按一下**擴充功能和更新...**.TestPublish 延伸應該會出現在中間窗格中，並啟用。

3. 在**工具**功能表上，請確定您看到測試命令。

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>發行至 Visual Studio Marketplace 的擴充功能

1. 請確定您已建立您的擴充功能的版本，而且它是最新狀態。

2. 在 web 瀏覽器中，開啟[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)網站。

3. 按一下右上角**登入**。

4. 使用您的 Microsoft 帳戶登入。 如果您沒有 Microsoft 帳戶，您可以在此時建立一個。

5. 按一下**發佈擴充功能**。  這會將您巡覽至您的擴充功能的管理頁面。  如果您沒有 「 發行者 」 帳戶，系統會提示您建立一個在這個階段。

  ![上傳至 Marketplace](media/upload-to-marketplace.png)

6. 選擇您要用來上傳您的擴充功能的發行者。  您可以變更 「 發行者 」 上所列左側的發行者名稱即可。  按一下**新的延伸模組**選取**Visual Studio**。

7. 在**1： 上傳副檔名**，您可以選擇直接上傳 VSIX 檔案到 Visual Studio Marketplace 或只新增您自己的網站的連結。 在此情況下，我們會將上傳擴充功能，TestPublish.vsix。  拖放您的擴充功能，或使用**按一下**連結以瀏覽檔案。  您的擴充功能可以找到專案的 \bin\Release 資料夾中。  按一下 [ **繼續**]。

8. 在**2： 提供擴充功能的詳細資料**，某些欄位 source.extension.vsixmanifest 檔案從您的延伸模組是 自動填入。  更多詳細說明每一個您可以找到下方：

    * **內部名稱**將擴充功能的詳細資料頁面的 URL 中使用。 如需範例，發行在 「 發行者 」 名稱"myname 」 擴充功能和指定的內部名稱為"myextension"會產生的 URL"marketplace.visualstudio\.com/items?itemName=myname.myextension 」 您的擴充功能詳細資料頁面。
    
    * **顯示名稱**延伸模組。  這是自動填入 source.extension.vsixmanifest 檔案。
   
    * **版本**您上傳擴充功能的數字。  這是自動填入 source.extension.vsixmanifest 檔案。
    
    * **VSIX ID**是 Visual Studio 會使用您的擴充功能的唯一識別碼。  如果您想要有您的擴充功能會自動更新，這是必要的。  這是自動填入 source.extension.vsixmanifest 檔案。
    
   * **標誌**，將使用您的擴充功能。  這將會自動填入如果提供 source.extension.vsixmanifest 檔案。
    
    * **簡短描述**的擴充功能的用途。  這將會自動填入 source.extension.vsixmanifest 檔案。
    
    * **概觀**是要包含螢幕擷取畫面和您的擴充功能的執行作業的相關詳細的資訊的好地方。
    
    * **支援的 Visual Studio 版本**可讓您選擇哪一個版本的 Visual Studio 會處理您的擴充功能。  您的延伸模組只會安裝這些版本。
    
    * **支援的 Visual Studio 版本**可讓您選擇哪一個版本的 Visual Studio 會處理您的擴充功能。  您的延伸模組只會安裝這些版本。
    
    * **型別**：  最常見的延伸模組類型是**工具**。
    
    * **類別**。  挑選最多三是適合您的擴充功能。
    
    * **標記**是關鍵字，幫助使用者尋找您的擴充功能。 標記可以協助提升您的擴充功能在 Marketplace 中的搜尋相關性。
    
    * **定價類別**是您的擴充功能的成本。
    
    * **原始程式碼儲存機制**可讓您與社群分享您的原始程式碼的連結。
    
    * **您的擴充功能允許問與答**可讓使用者離開您的延伸模組項目頁面上的問題。

9. 按一下**儲存並上傳**。 這會帶您回到您的發行者管理頁面。  您的擴充功能尚未發行。  若要發行您的擴充功能，以滑鼠右鍵按一下您的擴充功能，並選取**設為公用**。  您可以檢視您的擴充功能的外觀類似 Marketplace 上選取**檢視延伸**。  擷取的數字，按一下**報表**。  若要變更您的擴充功能，請按一下 **編輯*。

  ![延伸項目功能表](media/extension-entry-menu.png)

10. 按一下後**設為公用**，您的擴充功能現在是公用。  搜尋 Visual Studio Marketplace 您的擴充功能。

## <a name="add-additional-users-to-manage-your-publisher-account"></a>新增其他使用者管理您的 「 發行者 」 帳戶

Marketplace 支援授與其他使用者的權限來存取和管理 「 發行者 」 帳戶。

1. 瀏覽至您想要加入其他使用者的 「 發行者 」 帳戶。

2. 選取**成員**，然後按一下 **新增**

  ![加入額外的使用者](media/add-users.png)

3. 然後，您可以指定您想要新增並正確等級的存取權授與使用者的電子郵件地址**選取角色**。  您可以從下列項目中選擇：

  * **建立者**： 使用者可以發行擴充功能，但是您無法檢視或管理其他使用者所發行的擴充功能。
  
  * **讀取器**： 使用者可以檢視的擴充功能，但是您無法發行或管理擴充功能。
  
  * **參與者**： 使用者可以發佈和管理擴充功能，但是您無法編輯 發行者設定或管理存取權。
  
  * **擁有者**： 使用者可以發行和管理擴充功能中，編輯 發行者設定並管理存取權。
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>從 Visual Studio Marketplace 安裝擴充功能

現在已發行的擴充功能，將它安裝在 Visual Studio 並測試其存在。

1. 在 Visual Studio 中，在**工具**功能表上，按一下 **擴充功能和更新...**.

2. 按一下**線上**TestPublish 然後搜尋。

3. 按一下 [ **下載**]。 然後系統會排定擴充功能安裝。

4. 若要完成安裝，請關閉 Visual Studio 的所有執行個體。

## <a name="remove-the-extension"></a>移除擴充功能

從 Visual Studio Marketplace 並從您的電腦，您可以移除擴充功能。

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>若要從 Visual Studio Marketplace 移除擴充功能

1. 開啟[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)網站。

2. 按一下右上角**發行**擴充功能。  選擇您用來發行 TestPublish 「 發行者 」。  TestPublish 的清單隨即顯示。

3. 延伸模組項目上按一下滑鼠右鍵，然後按一下**移除**會要求您確認要移除該擴充功能。  按一下 [確定 **Deploying Office Solutions**]。

### <a name="to-remove-the-extension-from-your-computer"></a>若要從電腦移除擴充功能

1. 在 Visual Studio 中，在**工具**功能表上，按一下 **擴充功能和更新...**.

2. 選取 TestPublish，然後按一下**解除安裝**。 然後排定解除安裝擴充功能。

3. 若要完成解除安裝，請關閉所有 Visual Studio 執行個體。
