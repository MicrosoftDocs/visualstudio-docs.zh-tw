---
title: 如何： 安裝特定版本的 Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 50075d46edcf6ffc73ccdcdedb0daf42c8ff6e2d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827593"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>如何：安裝特定版本的 Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

我們時常更新 Visual Studio 安裝程式，以便讓您取得最新且最佳化版本的選擇性功能。  但如果您想安裝舊版 Visual Studio 2015 (例如包括 iOS 支援，且在 Update 1 之前版本的 Visual Studio 2015)，則必須強制 Visual Studio 安裝程式使用舊版的功能資訊清單檔案。 本文說明如何執行這項操作。  
  
## <a name="installing-the-current-release"></a>安裝目前版本  
 Visual Studio 2015 的初始版本，因為我們已更新數次安裝程式引擎和資訊清單檔案。  這表示，如果您下載 web 安裝程式，從[Visual Studio 下載](https://www.visualstudio.com/downloads/download-visual-studio-vs)乾淨、 連線網際網路的電腦上的網站，安裝程式會安裝最新的 Visual Studio 2015 更新，其中包含最新的產品增強功能及更新版本，但最新版本的選用功能和工具。  
  
## <a name="installing-earlier-releases"></a>安裝舊版  
 您可以建立並掛接 ISO 映像，或您可以下載並啟動安裝程式，直接從[My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)然後附加.exe 檔案，與其他命令列參數 (例如 /CustomInstallPath、 / 滿了，/ InstallSelectableItems /NoRestart 等。)若要控制安裝 Visual Studio 的方式。  
  
 下表包含一些特定的時間點案例，以及必要的命令列參數，您必須傳遞給 Enterprise edition 安裝程式。 (Community 或 Professional 版本的安裝程式也都可以使用相同參數)  
  
|Visual Studio 2015 版本|要執行的項目|要使用的命令列|安裝程式的動作|  
|--------------------------------|-----------------|--------------------------|---------------------|  
|Visual Studio Enterprise (最新的公開版本)|Visual Studio Enterprise 含更新 (可從[My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **注意：** 此安裝的預設行為提供最新的選擇性功能，因此，不需要任何命令列參數。|Visual Studio 安裝程式會使用最新的 feed.xml 並安裝最新的檔案|  
|Visual Studio Enterprise Update 3 (原始 Update 3 而不需要任何進一步的 Update 3-紀元更新)|Visual Studio Enterprise RTM (可從 [MSDN 訂用帳戶下載頁面](https://msdn.microsoft.com/subscriptions/downloads/)取得)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Visual Studio 安裝程式將使用 Update 3 發行時所提供的 feed.xml|  
|Visual Studio Enterprise Update 2 （原始 Update 2，但與更新該預先狀態的 Update 3）|Visual Studio Enterprise RTM (可從 [MSDN 訂用帳戶下載頁面](https://msdn.microsoft.com/subscriptions/downloads/)取得)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Visual Studio 安裝程式會使用發行的 Update 3 之前為目前的 feed.xml|  
|Visual Studio Enterprise (原始 Update 2 而不需要任何進一步的 Update 2-紀元更新)|Visual Studio Enterprise RTM (可從 [MSDN 訂用帳戶下載頁面](https://msdn.microsoft.com/subscriptions/downloads/)取得)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Visual Studio 安裝程式將使用 Update 2 發行時所提供的 feed.xml|  
|Visual Studio Enterprise Update 1 （原始 Update 1，但與更新該預先狀態的 Update 2）|Visual Studio Enterprise RTM (可從 [MSDN 訂用帳戶下載頁面](https://msdn.microsoft.com/subscriptions/downloads/)取得)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Visual Studio 安裝程式會使用發行的 Update 2 之前為目前的 feed.xml|  
|Visual Studio Enterprise Update 1 (沒有其他 Update 1 時期更新的原始 Update 1)|Visual Studio Enterprise RTM (可從 [MSDN 訂用帳戶下載頁面](https://msdn.microsoft.com/subscriptions/downloads/)取得)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Visual Studio 安裝程式將使用 Update 1 發行時所提供的 feed.xml|  
|Visual Studio Enterprise (原始 RTM，但包含 Update 1 前的更新)|Visual Studio Enterprise RTM (可從  [MSDN 訂用帳戶下載頁面](https://msdn.microsoft.com/en-us/subscriptions/downloads/)取得)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Visual Studio 安裝程式將使用在 Update 1 發行前現用的 feed.xml|  
|Visual Studio Enterprise (沒有更新的原始 RTM)|Visual Studio Enterprise RTM (可從 [MSDN 訂用帳戶下載頁面](https://msdn.microsoft.com/subscriptions/downloads/)取得)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Visual Studio 安裝程式將使用 RTM 發行時所提供的 feed.xml|  
  
> [!IMPORTANT]
>  請根據您想要使用的語言，以下列其中一個值取代 "enu"(英文)：  
> 
> - chs (中文 (簡體))  
>   -   cht (中文 (繁體))  
>   -   csy (捷克文)  
>   -   deu (德文)  
>   -   esn (西班牙文)  
>   -   fra (法文)  
>   -   ita (義大利文)  
>   -   jpa (日文)  
>   -   kor (韓文)  
>   -   plk (波蘭文)  
>   -   ptb (葡萄牙文)  
>   -   rus (俄文)  
>   -   trk (土耳其文)  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)