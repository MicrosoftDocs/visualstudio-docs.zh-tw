---
title: 設定 Git 存放庫
description: 在 Visual Studio for Mac 中使用 Git 和 Subversion。
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: 615f9d5bcba036301c2aa100e4618ab339412882
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796966"
---
# <a name="set-up-a-git-repository"></a>設定 Git 存放庫

Git 是一種分散式版本控制系統，可讓小組同時處理相同的文件。 這表示有單一伺服器包含所有檔案，但只要從這個中央來源簽出存放庫時，就會將整個存放庫複製至您的本機電腦。

有許多遠端主機可讓您使用 Git 來進行版本控制，不過最常見的主機是 GitHub。 下列範例使用 GitHub 主機，但您可以在 Visual Studio for Mac 中使用任何 Git 主機來進行版本控制。

如果您想要使用 GitHub，請確定您已先建立並設定帳戶，再遵循本文章中的步驟。

## <a name="creating-a-remote-repo-on-github"></a>在 GitHub 上建立遠端存放庫

下列範例使用 GitHub 主機，但您可以在 Visual Studio for Mac 中使用任何 Git 主機來進行版本控制。

若要設定 Git 存放庫，請執行下列步驟：

1. 在 github.com 中建立新的 Git 存放庫：

    ![建立新的 Git 存放庫](media/version-control-git1-sml.png)

2. 設定存放庫名稱、描述和隱私權。 請**不**要初始化存放庫。 將 .gitignore 和授權設定為 [無]：

    ![設定 Git 存放庫的詳細資料](media/version-control-git2.png)

3. 下一頁可讓您選擇顯示 HTTPS 或 SSH 位址，並將其複製至您所建立的存放庫：

    ![檢視和複製位址](media/version-control-git3.png)

   您需要 HTTPS 位址，才能將 Visual Studio for Mac 指向這個存放庫。

## <a name="publishing-an-existing-project"></a>發行現有專案

如果您有尚「未」在版本控制中的現有專案，請使用下列步驟在 Git 中進行設定：

1.  從 Visual Studio for Mac 的 Solution Pad 中選取方案名稱。

2. 在功能表列中，選取 [版本控制] > [在版本控制中發行] 以顯示 [選取存放庫] 對話方塊：

    ![在 Visual Studio for Mac 中開始簽出](media/version-control-git4-sml.png)

    如果此功能表項目在功能表中呈現灰色，請確定您已選取方案名稱。

3. 選擇 [已註冊的存放庫] 索引標籤，然後按 [新增] 按鈕：

    ![](media/version-control-git5.png)

4. 輸入您想要顯示在本機的存放庫名稱，並貼入步驟 3 中的 URL。 [存放庫組態] 對話方塊應該與下列類似。 按 [確定]：

    ![輸入 Git 詳細資料對話方塊](media/version-control-git6.png)

    也可以使用 SSH 連線至 Git。

5. 若要嘗試將應用程式發行至 Git，請選取存放庫，然後確定 [模組名稱] 和 [訊息] 文字欄位皆已完成：

    ![嘗試將專案發行至 Git](media/version-control-git7.png)

6. 按一下 [確定]，然後按一下警示對話方塊中的 [發行]。

7. 在 [Git 認證] 視窗中，輸入您的 GitHub 使用者名稱和密碼。 

> [!NOTE]
> 如果您的帳戶已啟用雙因素驗證 (2FA)，您必須建立存取權杖，以用來取代密碼。 如果您尚未建立存取權杖，請遵循 Git [存取權杖](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) \(英文\) 文件中的步驟。

8. 輸入使用者名稱和個人存取權杖，然後按 [確定]：

    ![輸入 Git 的使用者名稱和密碼](media/version-control-git9-sml.png)

9. 幾秒之後，方案應該搭配其初始認可發行。 透過瀏覽 [版本控制] 功能表項目來確認方案已發行；現在其中應該已填入許多選項：

    ![版本控制功能表](media/version-control-git10.png)

10. 在您開始進行其他變更時，請選取 [推送變更] ****  以將變更推送至 **遠端** 存放庫。 這將允許所有適當的使用者在 github.com 上進行檢視：

    ![將變更推送到遠端存放庫](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>發行新的專案

[新增專案] 對話方塊可以用來使用 Git 發行新的專案。 若要啟用它，請選取 [使用 Git 進行版本控制]。 核取方塊，如下列螢幕擷取畫面所示。 這將會初始化您的存放庫，並新增選擇性 .gitignore 檔案：

![將變更推送到遠端存放庫](media/version-control-git12.png)

## <a name="check-out-an-existing-repository"></a>簽出現有的存放庫

您可能必須使用只存在於遠端的 GitHub 存放庫，而不是本機電腦上的 GitHub 存放庫。 Visual Studio for Mac 可讓您快速簽出此存放庫。 請遵循下列步驟將其複製到您的電腦：

1. 在功能表列中，選取 [版本控制] > [簽出]：

2. 這會顯示 [連線到存放庫] 索引標籤：

    ![已輸入詳細資料的 [連線到存放庫] 索引標籤](media/version-control-git13.png)

3. 在遠端存放庫的 GitHub 頁面上，按 [複製或下載] 按鈕，然後複製提供的 URL：

    ![顯示的 GitHub URL](media/version-control-git14.png)

4. 在 [連線到存放庫] 索引標籤中，取代 [URL] 輸入欄位中的所有文字。這將會自動填入此索引標籤中的大部分其他欄位，如步驟 2 中的影像所示。

5. 輸入您想要複製存放庫的目標目錄，然後按 [簽出]。

> [!NOTE]
> 如果存放庫大小超過 4 GB，您可能會遇到問題。

## <a name="troubleshooting"></a>疑難排解

如果您在初始化含有空白遠端存放庫的專案時發生問題，可以嘗試下列步驟：

1. 移至方案資料夾。
1. 按下 **Command + Shift + .** 以顯示隱藏的檔案和資料夾。
1. 如果有 **.git** 資料夾，請刪除它。
1. 如果有 **gitignore** 檔案，請刪除它。
1. 按下 **Command + Shift + .** 以隱藏檔案和資料夾。
1. 在 VS for Mac 中開啟方案。
1. 在 Solution Pad 上選取您的方案節點。
1. 瀏覽至 [版本控制] 功能表，然後選擇 [Publish in Version Control] (在版本控制中發行)。
1. 遵循上述教學課程中從步驟 6 開始的步驟。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的版本控制 (Windows 上)](/visualstudio/version-control/)