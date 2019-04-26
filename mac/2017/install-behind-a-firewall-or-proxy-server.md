---
title: 在防火牆或 Proxy 伺服器後方安裝及使用 Visual Studio for Mac
description: 此文件提供的主機清單必須列在防火牆的允許清單中，讓 Visual Studio for Mac (以及其工作負載，包括 Xamarin) 在公司環境中運作。
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: asb3993
ms.author: amburns
ms.date: 10/23/2018
ms.openlocfilehash: 70ac8defdcea9cccd8a3b3f9be71d38fb78c9c50
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997955"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>在防火牆或 Proxy 伺服器後方安裝及使用 Visual Studio for Mac

如果您或您的組織使用防火牆或 Proxy 伺服器等安全性措施，則您應該將部分網域 URL 加入允許清單，並開放某些連接埠與通訊協定，以在安裝及使用 Visual Studio for Mac 與 Azure 服務時獲得最佳體驗。

- [**安裝 Visual Studio for Mac**](#install-visual-studio-for-mac)：這些資料表包含允許清單的 URL，以便您可以存取 Visual Studio for Mac 的所有功能與工作負載。

- [**使用 Visual Studio for Mac**](#use-visual-studio-for-mac)：這些資料表包含允許清單的 URL，以便您可以存取想要的所有服務與功能。

## <a name="install-visual-studio-for-mac"></a>安裝 Visual Studio for Mac

因為 Visual Studio for Mac 安裝程式會從各網域和下載伺服器下載，以下是您可能要在設定中新增為信任的網域和 URL。

### <a name="microsoft-domains"></a>Microsoft 網域

| Domain| 用途 |
| ----------------------------------- |---------------------------|
| *.live.com| 認證管理 |
| app.vssps.visualstudio.com| 安裝程式中繼資料|
| vortex.data.microsoft.com | 當機與錯誤報告 |
| az667904.vo.msecnd.net| 當機與錯誤報告 |
| xamarin.com | 安裝程式中繼資料|
| xampubdl.blob.core.windows.net| 安裝程式套件|
| download.visualstudio.microsoft.com | 安裝程式套件|
| xamarin.azureedge.net | 安裝程式套件|
| developer.xamarin.com | 安裝程式套件|
| dc.services.visualstudio.com| 當機報告 |

### <a name="third-party-domains"></a>協力廠商網域

| Domain| 用途 |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Java SDK|
| api.apple-cloudkit.com| Apple 安全性服務 |

## <a name="use-visual-studio-for-mac"></a>使用 Visual Studio for Mac

為了確保您在 Proxy 或防火牆後方時，可以存取 Visual Studio for Mac 中的每一個功能，我們建議您將下列網域與連接埠加入允許清單。

### <a name="general"></a>一般

| Domain | 連接埠|用途|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Microsoft URL 解析 |
| vsstartpage.blob.core.windows.net| 80/443| 起始頁資料|
| software.xamarin.com |  80/443|更新程式服務|
| addins.monodevelop.com | 80/443| 擴充服務 |
| visualstudio-devdiv-c2s.msedge.net | 80/443| 實驗性功能與通知 |
| targetednotifications.azurewebsites.net|  80/443| 用來將通知全域清單篩選為僅適用於特定電腦/使用方式情節類型的清單|

### <a name="identity"></a>身分識別

| Domain | 連接埠|用途|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| 識別提供者|
| secure.aadcdn.microsoftonline-p.com | 80/443|識別提供者|
| dc.services.visualstudio.com| 80/443|當機報告|
| management.azure.com|80/443| Azure 服務 API |

### <a name="nuget"></a>NuGet

| Domain | 連接埠|用途|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|NuGet API|
| secure.aadcdn.microsoftonline-p.com |80/443| 識別提供者|

### <a name="android-projects"></a>Android 專案

| Domain| 用途|
| ------------------------------------|------------------------------------|
| time.android.com| Android Emulator 的時間伺服器 |
| connectivitycheck.gstatic.com | Android Emulator 的連線|
| cloudconfig.googleapis.com| Android Emulator 的 API|

## <a name="see-also"></a>另請參閱

- [在防火牆或 Proxy 伺服器後方安裝並使用 Visual Studio 2017 和 Azure 服務](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [在 Windows 上對類似問題進行疑難排解](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
