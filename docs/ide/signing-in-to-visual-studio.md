---
title: 登入
description: 登入 Visual Studio 來延長 Visual Studio 的試用期、解除鎖定 Visual Studio 等等
ms.custom: contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4b4c91a2ff4693b62ce8ac4d40d493995c52b81b
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549468"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>登入 Visual Studio Windows 

雖然您不需要登入，但這麼做有許多好處。 在本文中，您將瞭解如何登[入](#how-to-sign-in)、如何[更新您的設定檔](#update-your-profile)，以及您的 Visual Studio 體驗的權益。 

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[登入 Visual Studio for Mac](/visualstudio/mac/signing-in)。

::: moniker range="vs-2017"

> [!WARNING]
> 若要使用針對條件式存取設定的資源，請升級至 Visual Studio 2019 Update 16.6 或更新版本。 如需詳細資訊，請參閱[如何搭配使用 Visual Studio 與需要多重要素驗證的帳戶](work-with-multi-factor-authentication.md)。
> 使用 Visual Studio 2017 存取針對條件式存取設定的資源，可能會觸發降級的驗證體驗，並在相同的 Visual Studio 會話中提示重新驗證數次。 
> 
::: moniker-end

以下是您在登入後預期及可執行事項的完整清單：

|優點|Description|
|---|---|
|延長 Visual Studio 試用期限|使用 Visual Studio Professional 或 Visual Studio Enterprise **額外的90天**，而不受限於30天的試用期。 <br/>請參閱 [延長試用版或更新授權](../ide/how-to-unlock-visual-studio.md)。|
|Visual Studio (Visual Studio 訂用帳戶或 Azure DevOps 組織解除鎖定) |使用與 Visual Studio 訂用帳戶或 Azure DevOps 組織建立關聯的帳戶，就可以解除鎖定 Visual Studio。<br/>請參閱 [延長試用版或更新授權](../ide/how-to-unlock-visual-studio.md)。|
|同步處理您的 Visual Studio 設定|您自訂的設定，例如按鍵系結、視窗配置和色彩主題，會在您登入任何裝置上的 Visual Studio 時立即套用。 <br/>請參閱[Visual Studio 中的同步處理設定](../ide/synchronized-settings-in-visual-studio.md)。|
|自動連接到服務|連線至 IDE 中的服務，例如 Azure 和 Azure DevOps Services，而不會再次提示相同帳戶的認證。|
|繼續使用 Visual Studio Community 版|如果您的 Community edition 安裝提示您提供授權，請登入 IDE 以繼續 **免費** 使用 Visual Studio Community。 |
|取得 ' Visual Studio Dev Essentials '|此方案包含免費的軟體供應專案、訓練、支援等等。 <br/>請參閱[Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/)。|


## <a name="how-to-sign-in"></a>登入方式 

當您第一次開啟 Visual Studio 時，系統會要求您登入並提供一些基本註冊資訊。

![登入提示](../ide/media/vs2019_signinpopup.png)

1. 選擇最能代表您的 Microsoft 帳戶或公司或學校帳戶。 如果您沒有這些帳戶，您可以按一下 [登入] 按鈕下的連結，免費建立 Microsoft 帳戶。 如果您遇到問題，請參閱 [如何? 註冊 Microsoft 帳戶？](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. 選擇您要在 Visual Studio 中使用的 UI 設定和色彩主題。 Visual Studio 會記住這些設定，並在您已登入的所有 Visual Studio 環境中同步處理這些設定。 如需已同步處理的設定清單，請參閱 [同步](../ide/synchronized-settings-in-visual-studio.md)處理的設定。 如果您在 Visual Studio 中開啟 [**工具** 選項] 功能表，您可以稍後再變更這些設定  >   。
   提供設定之後會啟動 Visual Studio，您也將完成登入並準備開始使用。 
   
1. 若要確認您是否已登入，請在 Visual Studio 環境的右上角尋找您的名稱。

![VS2019 中目前登入的使用者](../ide/media/vs2019_username.png)

如果您在第一次開啟 Visual Studio 時選擇不登入，稍後可以輕鬆地進行登入。 在 Visual Studio 環境的右上角尋找 [登 **入**] 連結。

![未登入使用者](../ide/media/vs2019_usernotsignedin.png)

除非您登出，否則每當啟動 Visual Studio 時便會自動登入，而且會自動套用同步設定的任何變更。 若要登出，請在 Visual Studio 環境的右上角，按一下具有您設定檔名稱的圖示，選擇 [**帳戶設定**] 命令，然後選擇 [**登出**] 連結。 若要再次登入，請選擇 Visual Studio 環境右上角的 [ **登入** ] 命令。

## <a name="update-your-profile"></a>更新您的設定檔

1. 移至  >  [檔案 **帳戶] 設定**，然後選擇 [**管理 Visual Studio 設定檔**] 連結。

1. 在瀏覽器視窗中，選取 [編輯設定檔] 並變更所要的設定。

1. 當您完成時，請選擇 [儲存變更]。

## <a name="troubleshooting"></a>疑難排解

請參閱 [訂閱支援](https://visualstudio.microsoft.com/subscriptions/support/) 頁面以取得協助。
