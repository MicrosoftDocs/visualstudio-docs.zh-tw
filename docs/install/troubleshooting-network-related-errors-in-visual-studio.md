---
title: 對安裝或使用 Visual Studio 時所發生的網路相關錯誤進行疑難排解 | Microsoft Docs
description: ''
ms.custom: ''
ms.date: 02/12/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fc5f1c07f709c1cdb8e20704dbea9cb5550b14b3
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>對安裝或使用 Visual Studio 時所發生的網路相關錯誤進行疑難排解
對於您在使用防火牆或 Proxy 伺服器的情況下安裝或使用 Visual Studio 時可能會遇到的常見網路或 Proxy 相關錯誤，我們皆有提供解決方案。

## <a name="error-proxy-authorization-required"></a>錯誤：「需要 Proxy 授權」

通常當使用者透過 Proxy 伺服器連線到網際網路，而 Proxy 伺服器封鎖 Visual Studio 對某些網路資源所做的呼叫時，就會發生這個錯誤。

### <a name="to-fix-this-error"></a>修正這個錯誤：

- 重新啟動 Visual Studio。 應該會出現 [Proxy 驗證] 對話方塊。 在對話方塊中依提示輸入您的認證。

- 如果重新啟動 Visual Studio 無法解決問題，這可能是因為您的 Proxy 伺服器並未提示輸入 http:&#47;&#47;go.microsoft.com 位址的認證，而是提示輸入 &#42;.visualStudio.com 位址的認證。 對於這些伺服器，請考慮將下列 URL 列於白名單上，以解除封鎖 Visual Studio 中的所有登入案例：

    - &#42;.windows.net

    - &#42;.microsoftonline.com

    - &#42;.visualstudio.com

    - &#42;.microsoft.com

    - &#42;.live.com

- 否則您可以從白清單中移除 http:&#47;&#47;go.microsoft.com 位址，這樣 Proxy 驗證對話方塊在 Visual Studio 重新啟動時，就會同時針對 http:&#47;&#47;go.microsoft.com 位址及伺服器端點顯示。

    OR

- 如果您想要將您的預設認證用於 Proxy，您可以執行下列動作：

    1. 在 **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** 或 **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** 中尋找 **devenv.exe.config** (devenv.exe 設定檔)。

    1. 在設定檔中，找出 `<system.net>` 區塊，並加入下列程式碼：

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        您必須在 `proxyaddress="<http://<yourproxy:port#>`中插入您的網路的正確 Proxy 位址。

    OR

- 您也可以遵循[如何透過驗證的 Web Proxy 進行連線](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) \(英文\) 部落格文章中的指示，該文章能示範如何新增可讓您使用 Proxy 的程式碼。

## <a name="error-the-underlying-connection-was-closed"></a>錯誤：「基礎連線已關閉」

如果您在使用防火牆的私人網路中使用 Visual Studio，Visual Studio 可能無法連線到某些網路資源。 這些資源可能包括用於登入和授權的 Visual Studio Team Services (VSTS)、NuGet 和 Azure 服務。 如果 Visual Studio 無法連線到這些資源的其中一項，您可能會看到以下錯誤訊息：

  **基礎連線已關閉：傳送時發生未預期的錯誤**

Visual Studio 使用傳輸層安全性 (TLS) 1.2 通訊協定連線到網路資源。 有些私人網路的安全性設備在 Visual Studio 使用 TLS 1.2 時，會封鎖某些伺服器連線。

### <a name="to-fix-this-error"></a>修正這個錯誤：

針對下列 URL 啟用連線：

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (適用於 Azure 連線)

- &#42;.visualstudio.com

- cdn.vsassets.io (主機內容傳遞網路 (又稱 CDN) 內容)

- &#42;.gallerycdn.vsassets.io (裝載 VSTS 擴充功能)

- static2.sharepointonline.com (裝載 Visual Studio 用於 Office UI 網狀架構 套件中的資源，例如字型)

- &#42;.nuget.org (適用於 NuGet 連線)

 > [!NOTE]
 > 此清單可能不含私人擁有的 NuGet 伺服器 URL。 您可以在 %APPData%\Nuget\NuGet.Config 中檢查您所使用的 NuGet 伺服器。


## <a name="get-support"></a>取得支援
如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面。 如果所有的安裝疑難排解步驟都沒有幫助，您可以透過即時聊天與我們連絡，以取得安裝協助 (僅限英文)。 如需詳細資料，請參閱 [Visual Studio 支援頁面](https://www.visualstudio.com/vs/support/#talktous)。

以下是一些支援選項：
* 您可以透過 Visual Studio 安裝程式和 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具來向我們報告產品問題。
* 您可以在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享產品建議。
* 您可以在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)追蹤產品問題，也可以在那裡詢問問題和尋找解答。
* 您也可以透過我們[在 Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動  (這個選項需要 [GitHub](https://github.com/) 帳戶)。

## <a name="see-also"></a>另請參閱
* [在防火牆或 Proxy 伺服器後方安裝及使用 Visual Studio](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [安裝 Visual Studio 2017](install-visual-studio.md)
