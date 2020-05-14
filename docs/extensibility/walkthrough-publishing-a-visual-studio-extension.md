---
title: 演練:發佈視覺工作室擴展 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34260124baedeba297dbd64e8a2c1856b55ec5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697133"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>演練:發佈可視化工作室擴展

本演練將介紹如何將可視化工作室擴展發佈到可視化工作室市場。 將擴展添加到應用商店時,開發人員可以使用**擴展和更新**來流覽新的和更新的擴展。

## <a name="prerequisites"></a>Prerequisites

 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-visual-studio-extension"></a>建立視覺化工作室延伸

本文使用預設的 VSPackage 擴展,但這些步驟對於每種擴展都有效。

1. 在 C#`TestPublish`中建立具有選單命令的 VSPackage。 有關詳細資訊,請參閱[創建您的第一個擴展:你好世界](../extensibility/extensibility-hello-world.md)。

## <a name="package-your-extension"></a>封裝您的延伸模組

1. 使用有關產品名稱、作者和版本的正確資訊更新延伸 *.vsix 清單*。

   ![更新延伸 vsixmanifest](media/update-extension-vsixmanifest.png)

2. 在**釋放**模式下生成擴展。 現在,您的擴展在 \bin_釋放資料夾中打包為 VSIX。

3. 您可以雙擊 VSIX 以驗證安裝。

## <a name="test-the-extension"></a>測試延伸

 在分發擴展之前,請生成並對其進行測試,以確保它在 Visual Studio 的實驗實例中正確安裝。

1. 在可視化工作室中,開始調試以打開 Visual Studio 的實驗實例。

2. 在實驗實例中,轉到 **「工具」** 功能表,然後單擊 **「擴展和更新**」。 測試發佈擴展應顯示在中心窗格中並啟用。

3. 在 **「工具」** 選單上,請確保看到測試命令。

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>將擴展發佈到可視化工作室市場

1. 請確保您已構建擴展的發佈版本,並且該版本是最新的。

2. 在 Web 瀏覽器中,打開[可視化工作室應用商店](https://marketplace.visualstudio.com/vs)網站。

3. 在右上角,按一下「**登錄**」。。

4. 使用您的 Microsoft 帳戶登入。 如果您沒有 Microsoft 帳戶,此時可以創建一個帳戶。

5. 按下 **「發布擴展**」。  這個選項將引導您存取所有擴充的管理頁面。 如果您沒有發佈者帳戶,系統將提示您此時創建一個。

   ![上傳到市場](media/upload-to-marketplace.png)

6. 選擇要用於上載擴展的發行者。 您可以通過按一下左側列出的發行者名稱來更改發行者。 點選 **「新增延伸」** 並選擇**視覺工作室**。

7. 在**1:上傳副檔名**,你可以選擇上傳一個VSIX檔直接到可視化工作室市場或只是添加一個連結到自己的網站。 在此示例中,將上載擴展 *,TestPublish.vsix。* 拖放副檔名或使用**按一下**連結瀏覽檔。 在專案的 [bin_釋放資料夾中找到您的擴展名。  按一下 **[繼續]**。

8. 在**2:提供擴展詳細資訊**時,某些欄位從*源*自動填充。 在下面尋找有關每個內容的詳細資訊:

    * **內部名稱**用於擴展的詳細資訊頁的 URL。 例如,在發佈者名稱"myname"下發佈擴展並將內部名稱指定為"我的擴展"會導致擴展的詳細資訊頁中的 URL"市場.visualstudio\.com/item?itemName_myname.my 擴展"。

    * **顯示**副檔名。 此名稱是從*source.擴展.vsixmanifest*檔自動填充的。

    * 要上載的擴展**的版本號。** 此版本是從*源.擴展.vsixmanifest*文件自動填充的。

    * **VSIX ID**是 Visual Studio 用於擴展的唯一標識碼。 如果要自動更新擴展,則需要此標識符。 此識別碼是從*source.擴展.vsixmanifest*檔自動填充的。

    * 擴充的**標誌 。** 此徽標從*source.擴展.vsixmanifest*檔(如果提供)自動填充。

    * **延伸功能的簡短描述**。 此說明是從*source.擴展.vsixmanifest*檔自動填充的。

    * **概述**是包含螢幕截圖和有關擴展功能的詳細資訊的好地方。

    * **支援的視覺化工作室版本**允許您選擇擴展將處理的 Visual Studio 版本。 您的擴展僅安裝到這些版本。

    * *支援的視覺工作室版本允許您選擇哪些版本的視覺工作室,您的擴展將工作。 您的擴展僅安裝到這些版本。

    * [類型]****。 最常見的延伸類型是**工具**。

    * **類別**. 最多取三個最適合您的擴展。

    * **標籤**是説明使用者找到副檔名的關鍵字。 標記可説明提高應用商店中擴展的搜索相關性。

    * **定價類別**是您的擴展成本。

    * **原始程式碼儲存庫**允許您與社區共用指向原始碼的連結。

    * **允許 Q&A 進行擴展**,用戶可以在擴展條目頁面上留下問題。

9. 點選「**儲存&上傳中載**。 此選項將帶您返回發行者管理頁面。 您的擴展尚未發佈。 要發佈擴展,請右鍵單擊擴展並選擇「**公開**」。 您可以通過選擇 **「查看擴展**」來查看擴展在應用商店中的外觀。 有關購置編號,請單擊 **「報表**」。。 要更改副檔名,請按下「**編輯**」。

   ![延伸項目選單](media/extension-entry-menu.png)

10. 單擊 **"公開"** 後,您的擴展現在公開。 在可視化工作室市場搜索您的擴展。

## <a name="add-additional-users-to-manage-your-publisher-account"></a>新增其他使用者來管理您的發行者帳戶

應用商店支援授予其他用戶訪問和管理發行者帳戶的許可權。

1. 導航到要向其添加其他使用者的發行者帳戶。

2. 選擇 **「成員」** 並按下「**添加**」。

   ![新增其他使用者](media/add-users.png)

3. 然後,您可以在 **「選擇角色**」下指定要添加的用戶的電子郵寄地址並授予正確的存取級別。  您可選擇下列選項：

   * **建立者**:使用者可以發佈擴展,但不能查看或管理其他用戶發佈的擴展。

   * **讀取器**:使用者可以查看擴展,但不能發佈或管理擴展。

   * **參與者**:使用者可以發佈和管理擴展,但不能編輯發行者設置或管理訪問許可權。

   * **擁有者**:用戶可以發佈和管理擴展、編輯發行者設置和管理訪問許可權。

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>從視覺化工作室市場安裝擴充

現在,擴展已發佈,請將其安裝在 Visual Studio 中並在那裡進行測試。

1. 在可視化工作室中,在 **「工具」** 功能表上,按一下 **「擴展和更新**」。

2. 點選 **「連線」 選單機,** 然後搜尋**測試發佈**。

3. 按一下 [下載]  。 然後計劃安裝擴展。

4. 要完成安裝,關閉可視化工作室的所有實例。

## <a name="remove-the-extension"></a>移除擴充功能

可以從可視化工作室應用商店和電腦中刪除擴展。

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>從視覺化工作室市場中移除擴展

1. 打開[可視化工作室市場](https://marketplace.visualstudio.com/vs)網站。

2. 在右上角,按兩下 **「發布**擴展」。。 選擇用於發佈**TestPublish**的發行者。 將顯示**測試發佈**的清單。

3. 右鍵按一下擴展項目,然後按下 **「刪除**」。 系統將要求您確定是否要刪除擴展。 按一下 [確定]  。

### <a name="to-remove-the-extension-from-your-computer"></a>從電腦中移除副檔名

1. 在可視化工作室中,在 **「工具」** 功能表上,按一下 **「擴展和更新**」。

2. 選擇 **「測試發佈」 然後**單擊「**卸載**」 。 然後,將擴展計劃卸載。

3. 要完成卸載,關閉可視化工作室的所有實例。
