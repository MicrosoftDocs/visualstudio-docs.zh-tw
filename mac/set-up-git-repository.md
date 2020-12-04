---
title: 設定 Git 存放庫
description: 使用 Visual Studio for Mac 連接到 Git 存放庫。
author: therealjohn
ms.author: johmil
ms.date: 12/03/2020
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.topic: how-to
ms.openlocfilehash: bacd533bf5c28c6f431fe7088fad36b6bbd3d04b
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561054"
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

2. 設定存放庫名稱、描述和隱私權。 請 **不** 要初始化存放庫。 將 .gitignore 和授權設定為 [無]：

    ![設定 Git 存放庫的詳細資料](media/version-control-git2.png)

3. 下一頁可讓您選擇顯示 HTTPS 或 SSH 位址，並將其複製至您所建立的存放庫：

    ![檢視和複製位址](media/version-control-git3.png)

   您需要 HTTPS 位址，才能將 Visual Studio for Mac 指向這個存放庫。

## <a name="publishing-an-existing-project"></a>發行現有專案

如果您有尚「未」在版本控制中的現有專案，請使用下列步驟在 Git 中進行設定：

> [!TIP]
> 使用 .gitignore 檔案來控制要使用 Git 追蹤和發佈的資料夾和檔案。 您可能會想要排除組建目錄、二進位檔或產生的檔案。 在 [GitHub 檔](https://docs.github.com/en/free-pro-team@latest/github/using-git/ignoring-files)中深入瞭解忽略檔案。

1. 從 [方案] 視窗中選取 [Visual Studio for Mac 的解決方案名稱。

2. 在功能表列中，選取 [ **版本控制] > 在版本控制中發行** 以顯示 [ **複製存放庫** ] 對話方塊：

    ![在 Visual Studio for Mac 中開始簽出](media/version-control-git4.png)

    如果此功能表項目在功能表中呈現灰色，請確定您已選取方案名稱。

3. 選擇 [ **從已註冊** ] 索引標籤，然後按 [ **新增** ] 按鈕：

    ![[新增已註冊的存放庫] 對話方塊。](media/version-control-git5.png)

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

10. 當您開始進行其他變更時，請先使用 **版本控制 >** 的 [檢查] 和 [認可] 功能表來開啟 [狀態視圖]。 選取並認可變更之後，請選取 [ **推送** ]，將變更推送至遠端存放庫。 這將允許所有適當的使用者在 github.com 上進行檢視：

    ![將變更推送到遠端存放庫](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>發行新的專案

新專案對話方塊可用來以本機 git 存放庫建立新的專案。 若要啟用它，請選取 [使用 git 進行版本控制] 核取方塊，如下列螢幕擷取畫面所示。 這將會初始化您的存放庫，並新增選擇性 .gitignore 檔案：

![使用 git 支援建立新專案](media/version-control-git-publish-new1.png)

請遵循以下步驟將新的本機存放庫推送至新的 GitHub 存放庫：

> [!NOTE]
> 如果您未建立 GitHub 存放庫，請參閱[在 GitHub 上建立遠端存放庫](#creating-a-remote-repo-on-github)一節。

1. 前往功能表列中的 [ **版本控制] > 審核] 和 [認可]，** 以建立您的第一個認可。

2. 在 [狀態] 索引標籤中，選擇左上方的 [認可]。

3. 撰寫認可訊息，例如「第一個認可」，然後按一下 [認可]：

    ![將初始變更認可到 git 存放庫](media/version-control-git-publish-new2.png)

4. 接下來，前往功能表列中的 [版本控制] > [管理分支和遠端]。

5. 前往 [遠端來源] 索引標籤，然後按一下 [新增]。

6. 在 [遠端來源] 視窗中，新增您先前所建立 GitHub 存放庫的詳細資料，然後按一下 [確定]：

    ![設定 git 存放庫的遠端來源](media/version-control-git-publish-new3.png)

7. 關閉 [Git 存放庫組態] 視窗中，然後前往功能表列中的 [版本控制] > [推送變更]。

8. 在 [推送至存放庫] 視窗中，按一下 [推送變更] 按鈕：

    ![將變更推送到遠端存放庫](media/version-control-git-publish-new4.png)

9. 出現提示時，請輸入您的 GitHub 使用者名稱和密碼。

> [!NOTE]
> 如果您的帳戶已啟用雙因素驗證 (2FA)，您必須建立存取權杖，以用來取代密碼。 如果您尚未建立存取權杖，請遵循 Git [存取權杖](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) \(英文\) 文件中的步驟。

Visual Studio for Mac 現在會將變更推送至您的遠端 GitHub 存放庫：

![推送作業已成功完成的確認文字](media/version-control-git11.png)

## <a name="clone-an-existing-repository"></a>複製現有的存放庫

您可能必須使用只存在於遠端的 GitHub 存放庫，而不是本機電腦上的 GitHub 存放庫。 Visual Studio for Mac 可讓您快速複製此存放庫。 請遵循下列步驟將其複製到您的電腦：

1. 在功能表列中，選取 [ **版本控制] > 複製存放庫**：

2. 這會顯示 [ **使用 Url 連接** ] 索引標籤：

    ![已輸入詳細資料的 [Url] 索引標籤](media/version-control-git13.png)

3. 在遠端存放庫的 GitHub 頁面上，按 [複製或下載] 按鈕，然後複製提供的 URL：

    ![顯示的 GitHub URL](media/version-control-git14.png)

4. 取代 [ **Connect With URL** ] 索引標籤中 [ **URL** 輸入] 欄位中的所有文字。這會為您填入此索引標籤中的大部分其他欄位，如步驟 #2 中的影像所示。

5. 輸入您想要複製存放庫的目錄，然後按下 [ **複製**]。

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
1. 在 [方案] 視窗中，選取您的方案節點。
1. 瀏覽至 [版本控制] 功能表，然後選擇 [Publish in Version Control] (在版本控制中發行)。
1. 遵循上述教學課程中從步驟 6 開始的步驟。

## <a name="see-also"></a>另請參閱

- [Visual Studio (Windows) 中的版本控制](/visualstudio/version-control/)
