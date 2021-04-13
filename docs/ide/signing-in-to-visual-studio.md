---
title: 登入 Visual Studio
description: 瞭解如何登入 Visual Studio。
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 749814dc6fd20107a2a1d2d5c0c26c7a4bad421b
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296803"
---
# <a name="sign-in-to-visual-studio"></a>登入 Visual Studio

您可以登入個人化帳戶，將 Visual Studio 中的開發體驗個人化及優化。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[登入 Visual Studio for Mac](/visualstudio/mac/signing-in)。

::: moniker range="vs-2017"

> [! 警告] 使用 Visual Studio 2017 來存取針對條件式存取設定的資源，可能會觸發降級的驗證體驗，並在相同的 Visual Studio 會話內提示重新驗證數次。 
> 若要使用針對條件式存取設定的資源，請升級至 Visual Studio 2019 Update 16.6 或更新版本。 如需詳細資訊，請參閱 [如何搭配使用 Visual Studio 與需要多重要素驗證的帳戶](work-with-multi-factor-authentication.md)。

::: moniker-end

## <a name="why-should-i-sign-in-to-visual-studio"></a>我為何應該登入 Visual Studio？

當您登入時，您可以擴充 Visual Studio 體驗。 例如，在您登入之後，您可以跨裝置 [同步處理您的設定](synchronized-settings-in-visual-studio.md) 、延長試用版，並自動連接到 Azure 服務。

以下是您在登入後預期及可執行事項的完整清單：
- **延長 Visual Studio 試用期** - 您可以額外使用 90 天的 Visual Studio Professional 或 Visual Studio Enterprise，而不受限於 30 天的試用期。 如需詳細資訊，請參閱 [擴充試用版或更新授權](../ide/how-to-unlock-visual-studio.md)。

- **繼續使用 Visual Studio Community 版** -如果您的社區版安裝提示您提供授權，請登入 IDE 以繼續 **免費** 使用 Visual Studio Community。 

- **使用與 Visual Studio 訂用帳戶或 Azure DevOps 組織建立關聯的帳戶，就可以解除鎖定 Visual Studio**。 如需詳細指示，請參閱 [延長試用版或更新授權](../ide/how-to-unlock-visual-studio.md)。

- **存取 Visual Studio Dev Essentials 方案** - 此方案包含免費的軟體供應項目、訓練、支援等等。 如需詳細資訊，請查看 [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) 。

- **同步處理您的 Visual Studio 設定** - 您自訂的設定 (例如按鍵繫結關係、視窗配置和色彩佈景主題)，會在您從任何裝置登入 Visual Studio 時立即套用。 請參閱 [Visual Studio 中的同步處理設定](../ide/synchronized-settings-in-visual-studio.md)。

- 對於同一個帳戶不會再次提示輸入認證，即可在 IDE 中 **自動連線到 Azure 和 Azure DevOps Services 等服務**。

## <a name="how-to-sign-in-to-visual-studio"></a>如何登入 Visual Studio

當您第一次開啟 Visual Studio 時，系統會要求您登入並提供一些基本註冊資訊。

![登入提示](../ide/media/vs2019_signinpopup.png)

您應該選擇 Microsoft 帳戶或最能代表您的工作或學校帳戶。 如果您沒有這些帳戶，您可以按一下 [登入] 按鈕下的連結，免費建立 Microsoft 帳戶。 如果您遇到問題，請參閱 [如何? 註冊 Microsoft 帳戶？](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

接下來，選擇您在 Visual Studio 中要使用的 UI 設定和色彩佈景主題。 Visual Studio 會記住這些設定，並在您已登入的所有 Visual Studio 環境中同步處理這些設定。 如需已同步處理的設定清單，請參閱 [同步](../ide/synchronized-settings-in-visual-studio.md)處理的設定。 如果您在 Visual Studio 中開啟 [**工具** 選項] 功能表，您可以稍後再變更這些設定  >   。

提供設定之後會啟動 Visual Studio，您也將完成登入並準備開始使用。 若要確認您是否已登入，請在 Visual Studio 環境的右上角尋找您的名稱。

![VS2019 中目前登入的使用者](../ide/media/vs2019_username.png)

如果您在第一次開啟 Visual Studio 時選擇不登入，稍後可以輕鬆地進行登入。 在 Visual Studio 環境的右上角尋找 [登 **入** ] 連結。

![未登入使用者](../ide/media/vs2019_usernotsignedin.png)

除非您登出，否則每當啟動 Visual Studio 時便會自動登入，而且會自動套用同步設定的任何變更。 若要登出，請在 Visual Studio 環境的右上角，按一下具有您設定檔名稱的圖示，選擇 [ **帳戶設定** ] 命令，然後選擇 [ **登出** ] 連結。 若要再次登入，請選擇 Visual Studio 環境右上角的 [ **登入** ] 命令。

## <a name="to-change-your-profile-information"></a>若要變更您的設定檔資訊

1. 移至  >  [檔案 **帳戶設定**]，然後選擇 [**管理 Visual Studio 設定檔**] 連結。

1. 在瀏覽器視窗中，選取 [編輯設定檔] 並變更所要的設定。

1. 當您完成時，請選擇 [儲存變更]。

## <a name="troubleshooting"></a>疑難排解

如果您在登入時遇到任何問題，請參閱 [訂閱支援](https://visualstudio.microsoft.com/subscriptions/support/) 頁面以取得協助。

## <a name="see-also"></a>另請參閱

* [延長試用版或更新授權](../ide/how-to-unlock-visual-studio.md)
* [在 Visual Studio 中使用 GitHub 帳戶](../ide/work-with-github-accounts.md)
* [Visual Studio IDE 概觀](../get-started/visual-studio-ide.md)
* [登入 (Visual Studio for Mac)](/visualstudio/mac/signing-in)
* [啟用 (Visual Studio for Mac)](/visualstudio/mac/activation)
