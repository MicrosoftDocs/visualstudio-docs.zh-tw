---
title: "在 Visual Studio for Mac 中設定 Git 存放庫"
description: "在 Visual Studio for Mac 中使用 Git 和 Subversion。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 9f25eda17648ba7eb3c264660ee0eb3b8eee166c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/11/2017

---

# <a name="setting-up-a-git-repository"></a>設定 Git 存放庫

Git 是一種分散式版本控制系統，可讓小組同時處理相同的文件。 這表示有單一伺服器包含所有檔案，但只要從這個中央來源簽出存放庫時，就會將整個存放庫本機複製至您的電腦。

有許多遠端主機可讓您使用 Git 來進行版本控制；不過，其中最常見的是 GitHub。 下面範例使用 GitHub 主機，但您可以在 Visual Studio for Mac 中使用任何 Git 主機來進行版本控制。

如果您想要使用 GitHub，請確定您已先建立並設定帳戶，再遵循下列步驟。 

## <a name="creating-a-remote-repo-on-github"></a>在 GitHub 上建立遠端存放庫

下面範例使用 GitHub 主機，但您可以在 Visual Studio for Mac 中使用任何 Git 主機來進行版本控制。

若要設定 Git 存放庫，請執行下列步驟：

1. 在 github.com 中建立新的 Git 存放庫：

    ![建立新的 Git 存放庫](media/version-control-git1-sml.png)

2. 設定存放庫名稱、描述和隱私權。 請**不**要初始化存放庫。 將 .gitignore 和授權設定為 [無]：

    ![設定 Git 存放庫的詳細資料](media/version-control-git2.png)

3. 下一個位置可讓您選擇顯示 HTTPS 或 SSH 位址，並將其複製至您剛剛建立的存放庫：

    ![檢視和複製位址](media/version-control-git3.png) 您需要 HTTPS 位址，才能將 Visual Studio for Mac 指向這個存放庫。


## <a name="publishing-an-existing-project"></a>發行現有專案

4. 返回 Visual Studio for Mac 中已開啟的專案。 

5. 在功能表列中，選取 [版本控制] > [Publish in Version Control] (在版本控制中發行)：

    ![在 Visual Studio for Mac 中開始簽出](media/version-control-git4-sml.png)

6. 這將會顯示 [選取存放庫] 對話方塊。 選擇 [已註冊的存放庫] 索引標籤，然後按 [新增] 按鈕：

    ![](media/version-control-git5.png)

7. 輸入您想要顯示在本機的存放庫名稱，並貼入步驟 3 中的 URL。 [存放庫組態] 對話方塊應該與下列類似。 按 [確定]： 

    ![輸入 Git 詳細資料對話方塊](media/version-control-git6.png)

    請注意，也可以使用 SSH 連線至 Git。

8. 若要嘗試將應用程式發行至 Git，請選取剛剛建立的存放庫，然後確定已完成 [模組名稱] 和 [訊息] 文字欄位：

    ![嘗試將專案發行至 Git](media/version-control-git7.png)

9. 按一下 [確定]，然後按一下警示對話方塊中的 [發行]。

10. 如果您尚未在 Visual Studio for Mac 喜好設定中輸入 Git 認證，請立即將其輸入。 首先，您必須建立存取權杖，以用來取代密碼。 若要這麼做，請遵循 Git [Access Token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) (存取權杖) 文件中的步驟。

11. 輸入使用者名稱和個人存取權杖，然後按 [確定]：

    ![輸入 Git 的使用者名稱和密碼](media/version-control-git9-sml.png)

12. 幾秒之後，應該使用初始認可來發行方案。 確認的方式是瀏覽 [版本控制] 功能表項目，現在在其中應該填入許多選項： 

    ![版本控制功能表](media/version-control-git10.png)

13. 在您開始進行其他變更之後，請選取 [推送變更] 將變更推送到 **remote** 存放庫。 這將允許所有適當的使用者在 github.com 上進行檢視： 

    ![將變更推送到遠端存放庫](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>發行新的專案

[新增專案] 對話方塊可以用來使用 Git 發行新的專案。 若要啟用它，請選取 [使用 Git 進行版本控制]。 核取方塊，如下列螢幕擷取畫面所示。 這將會初始化您的存放庫，並新增選擇性 .gitignore 檔案：

![將變更推送到遠端存放庫](media/version-control-git12.png)

## <a name="troubleshooting"></a>疑難排解

如果您在初始化含有空白遠端存放庫的專案時發生問題，可以嘗試下列步驟：

- 移至方案資料夾。
- 按 `Command + Shift + . `。顯示隱藏的檔案和資料夾。
- 如果有 `.git` 資料夾，請刪除它。
- 如果有 `gitignore` 檔案，請刪除它。
- 按 `Command + Shift + . `。隱藏檔案和資料夾。
- 在 VS for Mac 中開啟方案。
- 在 Solution Pad 上，選取方案節點。
- 瀏覽至 [版本控制] 功能表，然後選擇 [Publish in Version Control] (在版本控制中發行)。
- 遵循上述教學課程中從步驟 6 開始的步驟。
