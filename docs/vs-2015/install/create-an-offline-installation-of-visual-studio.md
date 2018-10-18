---
title: 建立 Visual Studio 的離線安裝 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: c248ee51d266eaa30bf738eba6e649ca15f3c9ce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193202"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>建立 Visual Studio 的離線安裝
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 2017 最新文件，請參閱 <<c0> [ 在低頻寬或不可靠的網路環境安裝 Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-vs-inconsistent-quality-network)，或[建立網路安裝的 Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio)和[安裝 Visual Studio 2017 的離線環境中的特殊考量](https://docs.microsoft.com/visualstudio/install/install-visual-studio-in-offline-environment)。

此頁面說明如何安裝 Visual Studio 2015，當您未連線到網際網路。 不過，若要執行的 「 已中斷連線 」 的安裝，您必須先建立離線安裝版面配置使用連線到網際網路的電腦。 以下為作法。  
  
> [!IMPORTANT]
>  如果您的離線電腦正在執行 Windows 7 SP1 或 Windows Server 2008 R2，請參閱中的特殊指示[疑難排解離線安裝](#BKMK_tshoot)本主題一節。  您必須遵循這些指示*之前*安裝 Visual Studio 2015。  
  
##  <a name="BKMK_Offline"></a> 建立離線安裝，安裝  
  
#### <a name="to-create-an-offline-installation-layout"></a>若要建立離線安裝版面配置  
  
1.  選擇您想要從安裝的 Visual Studio 的版本[My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015)下載頁面。  
  
2.  檔案系統上的位置下載安裝程式之後，請執行"\<可執行檔名稱 > /layout"。  
  
     例如，執行： `vs_enterprise.exe /layout D:\VisualStudio2015`  
  
     使用`/layout`參數，您可以下載幾乎所有的安裝封裝，而不只是適用於下載電腦。 此方法會提供您需要在任何位置執行這個安裝程式檔案，如果您想要安裝原本未安裝的元件可能會有用。  
  
3.  執行此命令之後，對話方塊會出現，可讓您變更您想要離線安裝版面配置，以存放的資料夾。   接下來，按一下**下載** 按鈕。  
  
     套件下載成功時，您應該會看到訊息指出**安裝成功 ！已成功取得所有指定的元件。**  
  
4.  找出您稍早指定的資料夾。 （例如，找出 D:\VisualStudio2015。）此資料夾包含您要複製到共用位置或安裝媒體的所有項目。  
  
    > [!CAUTION]
    >  Android SDK 目前尚不支援離線安裝體驗。 如果您將 Android SDK 安裝程式的項目安裝在未連線至網際網路的電腦，安裝可能會失敗。 如需詳細資訊，請參閱本主題 < 疑難排解離線安裝 > 一節。  
  
5.  從檔案位置，或從安裝媒體，請執行安裝。  
  
## <a name="updating-an-offline-installation"></a>更新離線安裝  
 Microsoft 已發行的 Visual Studio 2015 的數項更新。 若要更新您的 Visual Studio 安裝，只是下載從您想要的版本從[My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015)下載頁面。 接下來，請遵循本主題以建立新的離線安裝版面配置中所述的步驟，然後使用它來更新您的 Visual Studio 2015。  
  
##  <a name="BKMK_tshoot"></a> 疑難排解離線安裝  
 當您從離線安裝快取中離線安裝時，可能會看到無法安裝某些元件和套件的警告訊息。 下表包含這些情況下的可能方案。  
  
|元件或套件|方案|  
|--------------------------|--------------|  
|Dotfuscator 和 Analytics Community Edition 5.19.1 (Community、 Professional 和 Enterprise 版本的 Visual Studio 中，因為安裝於**Windows 7 SP1**並**Windows Server 2008 R2**)|如果您的離線電腦執行**Windows 7 SP1**或是**Windows Server 2008 R2**，您必須先執行下列步驟，才能安裝 Visual Studio 2015:<br /><br /> 1.若要下載 CTL 檔案的檔案或 web 伺服器設定。<br /><br /> 2.  重新導向 Microsoft 自動更新 URL 已中斷連線的環境。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 設定信任的根目錄和不允許的憑證](https://technet.microsoft.com/library/dn265983.aspx)Microsoft TechNet 網站上的頁面。|  
|Android SDK 安裝程式 (API 層級)|您必須連接網際網路，才能安裝 Android SDK (API 層級) 套件。 如果您是在受限網路上，則必須在安裝 Visual Studio 時允許存取下列 URL：<br /><br /> -   http://dl.google.com:443<br />-   http://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />如需如何解決可能的問題的 proxy 設定的詳細資訊，請參閱[Visual Studio 2015 安裝在 Proxy 後方的失敗 （Android SDK 安裝程式）](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/)部落格文章。|  
|Visual Studio 擴充性項目範本<br /><br /> Visual Studio 的 GitHub 擴充<br /><br /> PowerShell Tools for Visual Studio|如果當您安裝 Visual Studio 2015 時，您還沒有網際網路連線，您可以使用特殊的離線摘要來產生離線安裝版面配置。 **注意：** 此特殊的摘要包含 Visual Studio 2015 最新的更新。 <br /><br /> 若要建立離線摘要的特殊，執行下列命令： /layout*磁碟機：* \VisualStudio2015 /overridefeeduri *xml 來摘要 URL*<br /><br /> 例如，英文特殊離線摘要的 Visual Studio 2015 Enterprise，請執行：<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "http://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> 如您可以使用自選的語言建立離線摘要的特殊的 Url 的完整清單，請參閱下表。|  
  
 上表中所述，請使用下列 Url 來建立特定語言的特殊離線摘要。  
  
|語言|URL|  
|--------------|---------|  
|中文 (簡體)|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804|  
|和 SharePoint 2010 顯示的|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404|  
|捷克文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405|  
|德文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407|  
|英文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409|  
|西班牙文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A|  
|法文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C|  
|義大利文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410|  
|日文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411|  
|韓文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412|  
|波蘭文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415|  
|葡萄牙文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416|  
|俄文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419|  
|土耳其文|http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F|  
  
## <a name="see-also"></a>另請參閱  
 [安裝 Visual Studio]()