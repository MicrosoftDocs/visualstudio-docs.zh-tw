---
title: 在防火牆或 Proxy 伺服器後方安裝及使用 Visual Studio for Mac
description: 本文件會提供必須在防火牆中允許之主機的清單，來讓 Visual Studio for Mac (及其工作負載，包括 Xamarin) 能在公司環境中運作。
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 10/23/2018
ms.openlocfilehash: d488d56bdecd2801ecd94a2551c3be0f9834d0d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85938680"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>在防火牆或 Proxy 伺服器後方安裝及使用 Visual Studio for Mac

如果您或組織使用防火牆或 Proxy 伺服器等安全性措施，將會有您應該新增至「允許清單」的網域，以及應該開啟的連接埠和通訊協定，以確保您能在安裝及使用 Visual Studio for Mac 及 Azure 服務時取得最佳體驗。

- [**安裝 Visual Studio for Mac**](#install-visual-studio-for-mac)：這些表格包含必須允許連線的網域，讓您能夠存取 Visual Studio for Mac 的所有功能和工作負載。

- [**使用 Visual Studio for Mac**](#use-visual-studio-for-mac)：這些表格包含必須允許連線的網域，讓您可以存取相關的功能。

## <a name="install-visual-studio-for-mac"></a>安裝 Visual Studio for Mac

因為 Visual Studio for Mac 安裝程式會從各網域和下載伺服器下載，以下是您可能要在設定中新增為信任的網域和 URL。

### <a name="microsoft-domains"></a>Microsoft 網域

| 網域| 目的 |
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

| 網域| 目的 |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Java SDK|
| api.apple-cloudkit.com| Apple 安全性服務 |

## <a name="use-visual-studio-for-mac"></a>使用 Visual Studio for Mac

為了確保您在 Proxy 或防火牆後方時，可以存取您在 Visual Studio for Mac 中所需的每一個功能，我們建議您將下列網域與連接埠加入允許存取清單。

### <a name="general"></a>一般

| Domain | 連接埠|目的|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Microsoft URL 解析 |
| vsstartpage.blob.core.windows.net| 80/443| 起始頁資料|
| software.xamarin.com |  80/443|更新程式服務|
| addins.monodevelop.com | 80/443| 擴充服務 |
| visualstudio-devdiv-c2s.msedge.net | 80/443| 實驗性功能與通知 |
| targetednotifications.azurewebsites.net|  80/443| 用來將通知全域清單篩選為僅適用於特定電腦/使用方式情節類型的清單|

### <a name="identity"></a>身分識別

| Domain | 連接埠|目的|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| 身分識別提供者|
| secure.aadcdn.microsoftonline-p.com | 80/443|身分識別提供者|
| dc.services.visualstudio.com| 80/443|當機報告|
| management.azure.com|80/443| Azure 服務 API |

### <a name="nuget"></a>NuGet

| Domain | 連接埠|目的|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|NuGet API|
| secure.aadcdn.microsoftonline-p.com |80/443| 身分識別提供者|

### <a name="android-projects"></a>Android 專案

| 網域| 目的|
| ------------------------------------|------------------------------------|
| time.android.com| Android Emulator 的時間伺服器 |
| connectivitycheck.gstatic.com | Android Emulator 的連線|
| cloudconfig.googleapis.com| Android Emulator 的 API|

## <a name="see-also"></a>另請參閱

- [在防火牆或 Proxy 伺服器後方安裝並使用 Visual Studio 2017 和 Azure 服務](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [在 Windows 上針對類似問題進行疑難排解](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
