---
title: 針對網路或 Proxy 錯誤進行疑難排解
description: 針對您在使用防火牆或 Proxy 伺服器的情況下安裝或使用 Visual Studio 時可能會遇到的網路或 Proxy 相關錯誤，尋找解決方案。
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5e7d54b4e7777b3569031e96760699e7c075245f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306822"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>當您安裝或使用 Visual Studio 時針對網路相關錯誤進行疑難排解

對於您在使用防火牆或 Proxy 伺服器的情況下安裝或使用 Visual Studio 時可能會遇到的常見網路或 Proxy 相關錯誤，我們皆有提供解決方案。

## <a name="error-proxy-authorization-required"></a>錯誤：「需要 Proxy 授權」

通常當使用者透過 Proxy 伺服器連線到網際網路，而 Proxy 伺服器封鎖 Visual Studio 對某些網路資源所做的呼叫時，就會發生這個錯誤。

### <a name="to-fix-this-proxy-error"></a>修復這個 Proxy 錯誤

- 重新啟動 Visual Studio。 應該會出現 [Proxy 驗證] 對話方塊。 在對話方塊中依提示輸入您的認證。

- 如果重新啟動 Visual Studio 無法解決問題，這可能是因為您的 Proxy 伺服器並未提示輸入 http:&#47;&#47;go.microsoft.com 位址的認證，而是提示輸入 &#42;.visualStudio.microsoft.com 位址的認證。 針對這些伺服器，請考慮將下列 URL 新增至允許清單上，以解除封鎖 Visual Studio 中的所有登入案例：

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- 您也可以從允許清單中移除 http:&#47;&#47;go.microsoft.com 位址，如此一來，當 Visual Studio 重新啟動時，就會同時針對 http:&#47;&#47;go.microsoft.com 位址及伺服器端點顯示 Proxy 驗證對話方塊。

  -或-

- 如果您想要將您的預設認證用於 Proxy，您可以執行下列動作：

::: moniker range="vs-2017"

  1. 在 **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** 或 **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** 中尋找 **devenv.exe.config** (devenv.exe 設定檔)。

  2. 在設定檔中，找出 `<system.net>` 區塊，並加入下列程式碼：

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      您必須在 `proxyaddress="<http://<yourproxy:port#>` 中插入您的網路的正確 Proxy 位址。

     > [!NOTE]
     > 如需詳細資訊，請參閱[ &lt; &gt; (網路設定) ](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/)和[ &lt; proxy &gt; 元素 (網路設定) ](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)頁面中的 defaultProxy 元素。

::: moniker-end

::: moniker range=">=vs-2019"

  1. 在下列位置尋找 **devenv.exe.config** (devenv.exe configuration 檔案)：**%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** 或 **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**。

  2. 在設定檔中，找出 `<system.net>` 區塊，並加入下列程式碼：

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      您必須在 `proxyaddress="<http://<yourproxy:port#>` 中插入您的網路的正確 Proxy 位址。

     > [!NOTE]
     > 如需詳細資訊，請參閱[ &lt; &gt; (網路設定) ](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/)和[ &lt; proxy &gt; 元素 (網路設定) ](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)頁面中的 defaultProxy 元素。

::: moniker-end

## <a name="error-disconnected-from-visual-studio-when-attempting-to-report-a-problem"></a>錯誤：嘗試回報問題時「中斷與 Visual Studio」的連線

當使用者透過 proxy 伺服器連線到網際網路，而 proxy 伺服器封鎖了 Visual Studio 對某些網路資源進行的呼叫時，通常就會發生此錯誤。

### <a name="to-fix-this-proxy-error"></a>修復這個 Proxy 錯誤

1. 在： **% ProgramFiles (x86) % \ Microsoft Visual Studio\Installer** 或 **%ProgramFiles%\Microsoft Visual Studio\Installer** 中，尋找 feedback.exe 設定檔)  (**feedback.exe.config** 。

2. 在設定檔中，檢查是否有下列程式碼：如果程式碼不存在，請將它新增到最後 `</configuration>` 一行之前。

   ```xml
   <system.net>
       <defaultProxy useDefaultCredentials="true" />
   </system.net>
   ```

## <a name="error-the-underlying-connection-was-closed"></a>錯誤：「基礎連線已關閉」

如果您在使用防火牆的私人網路中使用 Visual Studio，Visual Studio 可能無法連線到某些網路資源。 這些資源可能包括用於登入和授權的 Azure DevOps Services、NuGet 和 Azure 服務。 如果 Visual Studio 無法連線到這些資源的其中一項，您可能會看到以下錯誤訊息：

  **基礎連線已關閉：傳送時發生未預期的錯誤**

Visual Studio 使用傳輸層安全性 (TLS) 1.2 通訊協定連線到網路資源。 有些私人網路的安全性設備在 Visual Studio 使用 TLS 1.2 時，會封鎖某些伺服器連線。

### <a name="to-fix-this-connection-error"></a>修正這個連線錯誤

針對下列 URL 啟用連線：

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (適用於 Azure 連線)

- &#42;.visualstudio.microsoft.com

- cdn.vsassets.io (主機內容傳遞網路 (又稱 CDN) 內容)

- &#42;.gallerycdn.vsassets.io (裝載 Azure DevOps Services 延伸模組)

- static2.sharepointonline.com (裝載 Visual Studio 用於 Office UI 網狀架構 套件中的資源，例如字型)

- &#42;.nuget.org (適用於 NuGet 連線)

  > [!NOTE]
  > 此清單可能不含私人擁有的 NuGet 伺服器 URL。 您可以在 %APPData%\Nuget\NuGet.Config 中檢查您所使用的 NuGet 伺服器。

## <a name="error-failed-to-parse-id-from-parent-process"></a>錯誤：「無法從父系進程剖析識別碼」

當您使用 Visual Studio 啟動載入器和網路磁碟機機上的 response.js時，可能會遇到這個錯誤訊息。 錯誤的來源是 Windows 中 (UAC) 的使用者帳戶控制。

以下是發生此錯誤的原因：對應的網路磁碟機機或 [UNC](/dotnet/standard/io/file-path-formats#unc-paths) 共用會連結到使用者的存取權杖。 當啟用 UAC 時，會建立兩個使用者 [存取權杖](/windows/win32/secauthz/access-tokens) ：一個 *具有* 系統管理員存取權，另一個則 *沒有* 系統管理員存取權。 建立網路磁碟機機或共用時，會連結使用者的目前存取權杖。 由於啟動載入器必須以系統管理員身分執行，因此如果磁片磁碟機或共用未連結到具有系統管理員存取權的使用者存取權杖，它就無法存取網路磁碟機機或共用。

### <a name="to-fix-this-error"></a>若要修正這個錯誤

您可以使用 `net use` 命令，也可以變更 UAC 群組原則設定。 如需這些因應措施及如何執行的詳細資訊，請參閱下列 Microsoft 支援文章：

* [在 Windows 中將 UAC 設定為「提示輸入認證」時，無法從提高許可權的提示字元使用對應的磁片磁碟機](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [當您在 Windows 作業系統中開啟使用者帳戶控制之後，程式可能無法存取某些網路位置](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [在防火牆或 Proxy 伺服器後方安裝及使用 Visual Studio](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [安裝 Visual Studio](install-visual-studio.md)
