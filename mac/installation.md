---
title: "安裝 Visual Studio for Mac | Microsoft Docs"
description: "如何安裝 Visual Studio for Mac 和跨平台開發所需之其他元件的指示。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 7f91a28449ffad135058438ec767095818cc8527
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2017
---
# <a name="setup-and-install-visual-studio-for-mac"></a>設定與安裝 Visual Studio for Mac

## <a name="setup"></a>安裝程式

若要在下載 Visual Studio for Mac 時開始開發原生的跨平台應用程式，有必須安裝和設定以做為準備的數個項目。

若要在 Visual Studio 中使用 iOS，您需要下列各項：

* 具有 macOS Sierra 10.12 或以上版本的 Mac
* Xcode 8.3 或以上版本。 通常建議使用最新穩定版本。
* Apple ID。 如果您還沒有 Apple 識別碼，可以在 https://appleid.apple.com 免費建立一個新識別碼。安裝及登入 Xcode 時需要有 Apple 識別碼。

## <a name="install"></a>安裝

1. 從 [https://www.visualstudio.com/](https://www.visualstudio.com/) 下載 Visual Studio for Mac

2. 安裝程式套件下載後，按一下 **VisualStudioInstaller.dmg** 檔案裝載安裝程式，然後按兩下標誌加以執行，如下圖所示：

  ![[安裝程式] 對話方塊](media/installer-image1.png)

3. 您可能會看到類似下圖的警示對話方塊提示。 在此情況下，按一下 [開啟]：

  ![[警示] 對話方塊](media/installer-image2.png)

4. 安裝程式會檢查您的系統，以驗證哪些元件需要安裝或更新：

  ![評估您的系統](media/installer-image3.png)

5. 您接著會看到 [警示] 對話方塊，要求您確認隱私權和授權條款。 按 [繼續] 按鈕以確認條款：

  ![[授權] 對話方塊](media/installer-image4.png)

6. 安裝程式會顯示遺失且需要下載及安裝的必要元件清單。 從這裡選取您想要下載的產品：

  ![選取項目](media/installer-image5.png)

  此安裝畫面顯示每個個別的元件的版本和大小。 您可以按一下每個元件，顯示該元件的相依性清單 (適用於 Android)，查看它下載的其他套件 (適用於.NET Core)，或檢視所需的任何其他應用程式 (適用於 iOS 和 macOS)：

  ![Android 其他相依性](media/installer-image6.png)

7. 一旦您滿意您的選擇之後，選取 [安裝及更新] 按鈕以啟動安裝程序。

8. 安裝程式會開始所選取項目的下載與安裝程序：

  ![開始安裝](media/installer-image7.png)

  ![下載 Xamarin.Mac](media/installer-image8.png)

  ![完成安裝](media/installer-image9.png)

9. 您可能會被提示要提高完成安裝所需之個別元件的必要權限。 在這裡輸入您的系統管理員認證以繼續安裝程序：

  ![輸入權限以繼續安裝程式](media/installer-image10.png)

10. 安裝成功之後，您可以按 [開始]，開始在 Visual Studio 中開發應用程式：

  ![開啟 Visual Studio](media/installer-image11.png)

> [!NOTE]
如果您在原始安裝期間選擇不安裝平台或工具 (在步驟 #6 中取消選取它)，當您稍後想要新增元件時，必須再次執行[安裝程式](https://www.visualstudio.com/vs/)。

## <a name="manual-installation"></a>手動安裝

如果您的安裝失敗或安裝的任何單一元件失敗，您或許可以透過手動安裝來解決此問題。 若要檢視必要元件並下載每個元件，請採取下列步驟：

1. 在 Visual Studio 安裝程式的第二個畫面中，移至功能表列，然後選取 [View Manual Installation Instructions] (檢視手動安裝指示)：

    ![顯示手動安裝功能表項目的選項](media/installer-image12.png)

2. 遵循指示以手動下載並安裝這些元件：

  ![手動安裝對話方塊](media/installer-image13.png)

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>將 Visual Studio for Mac 安裝在防火牆或 Proxy 伺服器後方

若要將 Visual Studio for Mac 安裝在防火牆後方，某些端點必須設為可供存取，才能允許下載您軟體所需的工具和更新。

將您的網路設定為允許存取下列位置：

* [Visual Studio 端點](https://docs.microsoft.com/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)