---
title: 登入 Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 03/10/2020
ms.topic: conceptual
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1033d4167c03951a642656807aeb9cca83116651
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79132690"
---
# <a name="sign-in-to-visual-studio"></a>登入 Visual Studio

您可以通過登錄個人化帳戶來個人化和優化視覺化工作室的開發體驗。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[登入 Visual Studio for Mac](/visualstudio/mac/signing-in)。

## <a name="why-should-i-sign-in-to-visual-studio"></a>我為何應該登入 Visual Studio？

當您登入時，您可以擴充 Visual Studio 體驗。 例如，登錄後，可以跨設備[同步設置](synchronized-settings-in-visual-studio.md)、擴展試用版並自動連接到 Azure 服務（僅舉幾例）。

以下是您在登入後預期及可執行事項的完整清單：
- **延長 Visual Studio 試用期** - 您可以額外使用 90 天的 Visual Studio Professional 或 Visual Studio Enterprise，而不受限於 30 天的試用期。 有關詳細資訊，請參閱[擴展試用版或更新許可證](../ide/how-to-unlock-visual-studio.md)。

- **解除鎖定 Visual Studio Community 版本** - 如果 Community 版本的安裝提示您提供授權，請登入 IDE 來自行解除鎖定。

- **使用與 Visual Studio 訂用帳戶或 Azure DevOps 組織建立關聯的帳戶，就可以解除鎖定 Visual Studio**。 有關詳細說明，請參閱[擴展試用版或更新許可證](../ide/how-to-unlock-visual-studio.md)。

- **存取 Visual Studio Dev Essentials 方案** - 此方案包含免費的軟體供應項目、訓練、支援等等。 如需詳細資訊，請查看 [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) 。

- **同步處理您的 Visual Studio 設定** - 您自訂的設定 (例如按鍵繫結關係、視窗配置和色彩佈景主題)，會在您從任何裝置登入 Visual Studio 時立即套用。 請參閱[視覺化工作室中的同步設置](../ide/synchronized-settings-in-visual-studio.md)。

- 對於同一個帳戶不會再次提示輸入認證，即可在 IDE 中**自動連線到 Azure 和 Azure DevOps Services 等服務**。

## <a name="how-to-sign-in-to-visual-studio"></a>如何登入 Visual Studio

首次打開 Visual Studio 時，系統會要求您登錄並提供一些基本的註冊資訊。 

![登入提示](../ide/media/vs2019_signinpopup.png)

您應該選擇 Microsoft 帳戶或最能代表您的工作或學校帳戶。 如果您沒有任何這些帳戶，則可以通過按一下登錄按鈕下的連結免費創建 Microsoft 帳戶。 如果您遇到問題，請參閱[如何註冊 Microsoft 帳戶？](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

接下來，選擇您在 Visual Studio 中要使用的 UI 設定和色彩佈景主題。 Visual Studio 會記住這些設定，並在您已登入的所有 Visual Studio 環境中同步處理這些設定。 有關同步設置的清單，請參閱[同步設置](../ide/synchronized-settings-in-visual-studio.md)。 如果在視覺化工作室中打開 **"工具** > **選項"** 功能表，則可以稍後更改設置。

提供設定之後會啟動 Visual Studio，您也將完成登入並準備開始使用。 若要確認您是否已登入，請在 Visual Studio 環境的右上角尋找您的名稱。

![當前在 VS2019 中登錄使用者](../ide/media/vs2019_username.png)

如果您選擇在首次打開 Visual Studio 時不登錄，則稍後很容易登錄。 在視覺化工作室環境的右上角查找**登錄**連結。 

![未登錄使用者](../ide/media/vs2019_usernotsignedin.png)

除非您登出，否則每當啟動 Visual Studio 時便會自動登入，而且會自動套用同步設定的任何變更。 要登出，請按一下 Visual Studio 環境右上角帶有個人資料名稱的圖示，選擇 **"帳戶設置"** 命令，然後選擇 **"登出**"連結。 若要再次登入，請選擇 Visual Studio 環境右上角的 [ **登入** ] 命令。

## <a name="to-change-your-profile-information"></a>若要變更您的設定檔資訊

1. 轉到 **"檔** > **帳戶設置**"並選擇 **"管理視覺化工作室設定檔**"連結。

1. 在瀏覽器視窗中，選取 [編輯設定檔]**** 並變更所要的設定。

1. 當您完成時，請選擇 [儲存變更]****。

## <a name="troubleshooting"></a>疑難排解

如果您在登錄時遇到任何問題，請參閱[訂閱支援](https://visualstudio.microsoft.com/subscriptions/support/)頁面以獲取有關説明。

## <a name="see-also"></a>另請參閱

* [延長試用版或更新授權](../ide/how-to-unlock-visual-studio.md)
* [Visual Studio IDE 概觀](../get-started/visual-studio-ide.md)
* [登入 (Visual Studio for Mac)](/visualstudio/mac/signing-in)
* [啟用 (Visual Studio for Mac)](/visualstudio/mac/activation)
