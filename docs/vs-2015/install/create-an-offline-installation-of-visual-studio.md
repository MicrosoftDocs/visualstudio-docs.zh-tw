---
title: 建立離線安裝 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 72bf11519ec500082304fde431122d05ee65db54
ms.sourcegitcommit: 3b48ce4649d38a7e3b095bd087739d6131e49d1b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76124513"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>建立 Visual Studio 的離線安裝
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新文件，請參閱[建立 Visual Studio 的離線安裝](/visualstudio/install/create-an-offline-installation-of-visual-studio)或[建立 Visual Studio 的網路安裝](/visualstudio/install/create-a-network-installation-of-visual-studio)。

此頁面說明當您未連線到網際網路時，如何安裝 Visual Studio 2015。 不過，若要執行「中斷連線」安裝，您必須先使用連線到網際網路的機器，建立離線安裝配置。 以下為作法。

> [!IMPORTANT]
> 如果您的離線機器是執行 Windows 7 SP1 或 Windows Server 2008 R2，請參閱此主題中[針對離線安裝進行疑難排解](#BKMK_tshoot)一節的特殊指示。  安裝 Visual Studio 2015「之前」  ，您必須遵循這些指示操作。

## <a name="BKMK_Offline"></a> 透過建立離線安裝來安裝

#### <a name="to-create-an-offline-installation-layout"></a>建立離線安裝配置

1. 從 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) 下載頁面選擇您要安裝的 Visual Studio 版本。

2. 將安裝程式下載到您的本機檔案系統之後，執行 "\<可執行檔名稱> /layout"。

     例如，執行：`vs_enterprise.exe /layout D:\VisualStudio2015`

     您可以使用 `/layout` 參數下載幾乎所有安裝套件，而不只是適用於下載電腦的套件。 此方法提供您在任何位置執行此安裝程式時需要的檔案，且如果您想要安裝一開始未安裝的元件，此安裝程式會非常有用。

3. 執行此命令之後，隨即出現對話方塊，讓您變更放置離線安裝配置的資料夾。   按一下 [下載]  按鈕。

     套件順利下載完成時，您應該會看到訊息顯示「安裝成功!  已成功取得所有指定元件。」

4. 找出您稍早之前指定的資料夾。 (例如，找出 D:\VisualStudio2015。)此資料夾包含您需要複製到共用位置或安裝媒體所需的所有項目。

    > [!CAUTION]
    > Android SDK 目前尚不支援離線安裝體驗。 如果您將 Android SDK 安裝程式的項目安裝在未連線至網際網路的電腦，安裝可能會失敗。 如需此問題的詳細資訊，請參閱本主題中的＜針對離線安裝進行疑難排解＞小節。

5. 從檔案位置或安裝媒體執行安裝。

## <a name="updating-an-offline-installation"></a>更新離線安裝
 Microsoft 已發行數個 Visual Studio 2015 更新。 若要更新您的 Visual Studio 安裝，請從 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) 下載頁面直接下載您想要的版本。 接著，依照此主題中概述的步驟建立新的離線安裝配置，然後使用它來更新您的 Visual Studio 2015 複本。

## <a name="BKMK_tshoot"></a> 針對離線安裝進行疑難排解
 當您從離線安裝快取中離線安裝時，可能會看到無法安裝某些元件和套件的警告訊息。 下表包含這些情況下的可能方案。

| 元件或套件 | 方案 |
|-|-|
| Dotfuscator and Analytics Community Edition 5.19.1 (適用於在 **Windows 7 SP1** 和 **Windows Server 2008 R2** 上安裝的 Community、Professional 與 Enterprise 版本 Visual Studio) | 如果您的離線機器是執行 **Windows 7 SP1** 或 **Windows Server 2008 R2**，您必須先執行下列步驟，才能安裝 Visual Studio 2015：<br /><br /> 1.設定檔案或 Web 伺服器來下載 CTL 檔案。<br /><br /> 2.  針對離線環境將 Microsoft 自動更新 URL 重新導向。<br /><br /> 如需詳細資訊，請參閱 Microsoft TechNet 網站上的[設定受信任的根目錄和不允許的憑證](https://technet.microsoft.com/library/dn265983.aspx) \(英文\) 頁面。 |
| Android SDK 安裝程式 (API 層級) | 您必須連接網際網路，才能安裝 Android SDK (API 層級) 套件。 如果您是在受限網路上，則必須在安裝 Visual Studio 時允許存取下列 URL：<br /><br /> -   https://dl.google.com:443<br />-   https://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />如需如何解決 Proxy 設定可能問題的詳細資訊，請參閱 [Visual Studio 2015 install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (受 Proxy 保護的 Visual Studio 2015 安裝失敗 (Android SDK 安裝程式)) 部落格文章。 |
| Visual Studio 擴充性項目範本<br /><br /> Visual Studio 的 GitHub 延伸模組<br /><br /> PowerShell Tools for Visual Studio | 當您在安裝 Visual Studio 2015 時，如果沒有網際網路連線，您可以使用特殊離線摘要來產生離線安裝配置。 **注意：** 此特殊摘要包含最新的 Visual Studio 2015 更新。 <br /><br /> 若要建立特殊離線摘要，請執行下列命令：/layout *Drive:* \VisualStudio2015 /overridefeeduri *URL-to-feed-xml*<br /><br /> 例如，如需 Visual Studio 2015 Enterprise 的英文語言特殊離線摘要，請執行：<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> 如需能以您所選語言建立特殊離線摘要的 URL 完整清單，請參閱下表。 |

 使用下列 URL 來建立語言特定特殊離線摘要，如上表中所述。

|       語言        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| 中文 (簡體)  | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| 和 SharePoint 2010 顯示的 | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         捷克文         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        德文         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        英文        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        西班牙文        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        法文         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        義大利文        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       日文        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        韓文         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        波蘭文         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      葡萄牙文       | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        俄文        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        土耳其文        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>另請參閱

- [安裝 Visual Studio](install-visual-studio-2015.md)