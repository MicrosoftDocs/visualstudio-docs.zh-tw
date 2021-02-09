---
title: R 的遠端工作區
description: 如何設定遠端 R 工作區並從 Visual Studio 連線到工作區。
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 96078d1b2fdb5a54c912cbf214024726ce102e4e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851838"
---
# <a name="set-up-remote-workspaces"></a>設定遠端工作區

本文說明如何使用 SSL 和適當的 R 服務來設定遠端伺服器。 這可讓 Visual Studio R 工具 (RTVS) 連線到該伺服器上的遠端工作區。

## <a name="remote-computer-requirements"></a>遠端電腦需求

- Windows 10、Windows Server 2016 或 Windows Server 2012 R2。 RTVS 也需要
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) 或更新版本

## <a name="install-an-ssl-certificate"></a>安裝 SSL 憑證

RTVS 需要所有與遠端伺服器通訊均透過 HTTP，而這需要伺服器上有 SSL 憑證。 您可以使用受信任的憑證授權單位所簽署的憑證 (建議)，或自我簽署憑證  (自我簽署憑證時，RTVS 會在連線時發出警告 ) 。您必須將其安裝在電腦上，並允許存取其私密金鑰。

### <a name="obtain-a-trusted-certificate"></a>取得受信任的憑證

受信任的憑證是由憑證授權單位核發 (請參閱[維基百科的憑證授權單位](https://en.wikipedia.org/wiki/Certificate_authority)了解背景)。 如同取得政府的身分證一樣，發出受信任的憑證牽涉到很多程序和可能產生的費用，但會驗證要求及要求者的真實性。

憑證中需要有一個索引鍵欄位，其為您 R 伺服器電腦的完整網域名稱。 憑證授權單位需要您證明有權針對伺服器所屬網域建立新的伺服器。

如需詳細背景，請參閱維基百科的[公開金鑰憑證](https://en.wikipedia.org/wiki/Public_key_certificate)。

## <a name="install-an-ssl-certificate-on-windows"></a>在 Windows 上安裝 SSL 憑證

您必須手動將 SSL 憑證安裝到 Windows 上。 請遵循下列指示安裝 SSL 憑證。

### <a name="obtain-a-self-signed-certificate-windows"></a>取得自我簽署憑證 (Windows)

如果您有受信任的憑證，請略過本節。 相較於來自受信任授權單位的憑證，自我簽署的憑證就像是您自行建立的身分證。 此程序當然比使用受信任的授權單位更為簡單，但因為缺乏強有力的驗證，表示攻擊者可以他們自己的憑證取代未簽署的憑證，擷取用戶端與伺服器之間的所有流量。 因此，「自我簽署憑證應該僅用於受信任網路上的測試案例，絕不能用在生產環境中」。

基於這個理由，RTVS 在連線使用自我簽署憑證的伺服器時，一律會發出下列警告︰

![自我簽署憑證警告對話方塊](media/workspaces-remote-self-signed-certificate-warning.png)

核發自我簽署憑證：

1. 使用系統管理員帳戶登入 R 伺服器電腦。
1. 開啟新的系統管理員 PowerShell 命令提示字元，並發出下列命令，以您伺服器電腦的完整網域名稱取代 `"remote-machine-name"`。

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. 如果您從未在 R 伺服器電腦上執行過 PowerShell，請執行下列命令，明確執行命令︰

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

如需背景，請參閱維基百科上的[自我簽署憑證](https://en.wikipedia.org/wiki/Self-signed_certificate)。

### <a name="install-the-certificate"></a>安裝憑證

若要在遠端電腦上安裝憑證，請從命令提示字元執行 certlm.msc (憑證管理員)。 以滑鼠右鍵按一下 [個人] 資料夾，然後選取 [所有工作] > [匯入] 命令︰

![匯入憑證命令](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>授權讀取 SSL 憑證的私密金鑰

一旦匯入憑證，即授與 `NETWORK SERVICE` 帳戶讀取私密金鑰的權限，如下列指示所述。 `NETWORK_SERVICE` 是執行 R 服務訊息代理程式所使用的帳戶，這是終止 SSL 連線連入伺服器電腦的服務。

1. 從系統管理員命令提示字元執行 certlm.msc (憑證管理員)。
1. 展開 [**個人**  >  **憑證**]，在您的憑證上按一下滑鼠右鍵，然後選取 [  >  **管理私密金鑰**]。
1. 以滑鼠右鍵按一下憑證，然後選取 [所有工作] 下的 [管理私密金鑰] 命令。
1. 在出現的對話方塊中，選取 [新增] 並輸入 `NETWORK SERVICE` 為帳戶名稱︰

    ![[管理私密金鑰] 對話方塊, 新增 NETWORK_SERVICE](media/workspaces-remote-manage-private-key-dialog.png)

1. 選取兩次 [確定] 關閉對話方塊並認可變更。

## <a name="install-an-ssl-certificate-on-ubuntu"></a>在 Ubuntu 上安裝 SSL 憑證

`rtvs-daemon` 套件預設會在安裝時一併安裝自我簽署的憑證。

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>取得自我簽署憑證 (Ubuntu)

如需了解使用自我簽署憑證的優點與風險，請參閱 Windows 描述。 `rtvs-daemon` 套件會在安裝期間產生和設定自我簽署的憑證。 只有當您想要取代自動產生的自我簽署憑證時，才需要進行下列作業。

自行核發自我簽署憑證：

1. SSH 或登入您的 Linux 電腦。
2. 安裝 `ssl-cert` 套件：

    ```sh
    sudo apt-get install ssl-cert
    ```

3. 執行 `make-ssl-cert` 以產生預設的自我簽署 SSL 憑證：

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. 將產生的金鑰和 PEM 檔案轉換成 PFX。 產生的 PFX 應該在主資料夾中：

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>設定 RTVS 精靈

您必須在 /etc/rtvs/rtvsd.config.json 中設定 SSL 憑證檔案路徑 (PFX 的路徑)。 分別使用檔案路徑與密碼來更新 `X509CertificateFile` 和 `X509CertificatePassword`。

```json
{
  "logging": { "logFolder": "/tmp" },
  "security": {
    "allowedGroup": "",
    "X509CertificateFile": "/etc/rtvs/ssl-cert-snakeoil.pfx",
    "X509CertificatePassword": "SnakeOil"
  },
  "startup": { "name": "rtvsd" },
  "urls": "https://0.0.0.0:5444"
}
```

儲存檔案並重新啟動 `sudo systemctl restart rtvsd` 精靈。

## <a name="install-r-services-on-windows"></a>在 Windows 上安裝 R 服務

若要執行 R 程式碼，遠端電腦就必須安裝 R 解譯器，如下所示︰

1. 下載並安裝下列一項︰

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R for Windows](https://cran.r-project.org/bin/windows/base/)

     兩者有相同的功能，但 Microsoft R Open 得益於使用 [Intel Math Kernel Library](https://software.intel.com/intel-mkl) (Intel 數學核心程式庫) 提供的線性代數程式庫加速的額外硬體。

2. 執行 [R 服務安裝程式](https://github.com/Microsoft/RTVS/blob/master/doc/rtvsd/rtvs-remote-downloads.md)，並於系統提示時重新開機。 安裝程式會執行下列動作︰

    - 在 *%PROGRAMFILES%\R Tools for Visual Studio\1.0\\* 中建立資料夾，然後複製所有必要的二進位檔。
    - 安裝 `RHostBrokerService` 和 `RUserProfileService` 並設定自動啟動。
    - 設定 `seclogon` 服務自動啟動。
    - 在預設連接埠 5444 上，將 Microsoft.R.Host.exe 和 Microsoft.R.Host.Broker.exe 新增至防火牆輸入規則。

電腦重新開機時會自動啟動 R 服務︰

- **R 主機訊息代理程式服務** 處理 Visual Studio 與電腦上執行 R 程式碼之處理序間的所有 HTTPS 流量。
- **R 使用者設定檔服務** 是處理 Windows 使用者設定檔建立的特殊權限元件。 新使用者第一次登入 R 伺服器電腦時，會呼叫此服務。

您可以在服務管理主控台中看到這些服務 (compmgmt.msc)。

## <a name="install-r-services-on-linux"></a>在 Linux 上安裝 R 服務

若要執行 R 程式碼，遠端電腦就必須安裝 R 解譯器，如下所示︰

1. 下載並安裝下列一項︰

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R for Windows](https://cran.r-project.org/bin/linux/ubuntu/)

     兩者有相同的功能，但 Microsoft R Open 得益於使用 [Intel Math Kernel Library](https://software.intel.com/intel-mkl) (Intel 數學核心程式庫) 提供的線性代數程式庫加速的額外硬體。

2. 遵循 [Linux 的遠端 R 服務](setting-up-remote-r-service-on-linux.md)指示，其中涵蓋了實體 Ubuntu 電腦、Azure Ubuntu VM、適用於 Linux 的 Windows 子系統 (WSL) 及 Docker 容器，包括在 Azure Container Repository 上執行的項目。

## <a name="configure-r-services"></a>設定 R 服務

在遠端電腦上執行 R 服務，也需要建立使用者帳戶、設定防火牆規則、設定 Azure 網路功能，以及設定 SSL 憑證。

1. 使用者帳戶︰為每位存取遠端電腦的使用者建立帳戶。 您可以建立標準的 (不具權限) 本機使用者帳戶，或者將 R 伺服器電腦加入您的網域，並將適當的安全性群組新增至 `Users` 安全性群組。

1. 防火牆規則︰根據預設，`R Host Broker` 會接聽 TCP 通訊埠 5444。 因此，請確定傳入和傳出流量皆已啟用 Windows 防火牆規則 (安裝套件和類似案例需要傳出)。  R 服務安裝程式會為內建的 Windows 防火牆自動設定這些規則。 不過，如果您使用協力廠商防火牆，請手動開啟連接埠 5444 供 `R Host Broker` 使用。

1. Azure 組態︰如果您的遠端電腦是 Azure 的虛擬機器，請也開啟連接埠 5444 供 Azure 網路的連入流量使用，它不受 Windows 防火牆影響。 如需詳細資訊，請參閱 Azure 文件的[使用網路安全性群組來篩選網路流量](/azure/virtual-network/virtual-networks-nsg)。

1. 通知 R 主機訊息代理程式要載入的 SSL 憑證︰如果您要在內部網路伺服器上安裝憑證，則您伺服器的完整網域名稱很可能與其 NETBIOS 名稱相同。 在此情況下，您不需要做任何事，因為這是載入的預設憑證。

    不過，如果您要在網際網路伺服器 (例如 Azure VM) 上安裝憑證，請使用伺服器的完整網域名稱 (FQDN)，因為網際網路伺服器的 FQDN 與其 NETBIOS 名稱絕不會相同。

    若要使用 FQDN，請巡覽至 R 服務的安裝位置 (預設為 %PROGRAM FILES%\R Remote Service for Visual Studio\1.0)，並在文字編輯器中開啟 Microsoft.R.Host.Broker.Config.json 檔案，然後使用下列內容取代其內容，以將 CN 指派給任何的伺服器 FQDN，例如 `foo.westus.cloudapp.azure.com`：

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    儲存檔案並重新啟動電腦以套用變更。

## <a name="troubleshooting"></a>疑難排解

**問。R 伺服器電腦沒有回應，我該怎麼辦？**

嘗試從命令列 ping 遠端電腦：`ping remote-machine-name`。 如果 ping 失敗，請確定電腦正在執行。

**問。R 互動視窗顯示遠端電腦已開啟，但為什麼服務未執行？**

有三個可能的原因：

- 電腦上未安裝 [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) 或更新版本。
- 通訊埠 5444 連接埠的連入和連出連線未啟用 `Microsoft.R.Host.Broker` 和 `Microsoft.R.Host` 防火牆規則。
- 未安裝具有 `CN=<remote-machine-name>` 的SSL 憑證。

完成任何上述變更後，請重新啟動電腦。 然後透過工作管理員 ([服務] 索引標籤) 或 services.msc 確定 `RHostBrokerService` 和 `RUserProfileService` 正在執行。

**問。連接到 R 伺服器時，R 互動視窗為何顯示「401拒絕存取」？**

有兩個可能的原因：

- `NETWORK SERVICE` 帳戶很可能無法存取 SSL 憑證的私密金鑰。 請依稍早的指示授與私密金鑰的 `NETWORK SERVICE` 存取權。
- 確定 `seclogon` 服務正在執行。 使用 services.msc 設定 `seclogon` 自動啟動。

**問。連接到 R 伺服器時，為什麼 R 互動視窗顯示「找不到404」？**

此錯誤可能是因為遺漏 Visual C++ 可轉散發程式庫。 檢查 R 互動視窗看看是否有關於遺漏文件庫的訊息 (DLL)。 然後檢查是否安裝 VS 2015 可轉散發套件以及已安裝 R。

**問。我無法從 R 互動視窗存取網際網路/資源，我該怎麼做？**

確定 `Microsoft.R.Host.Broker` 和 `Microsoft.R.Host` 的防火牆規則允許通訊埠 5444 的傳出存取。 套用變更之後，重新啟動電腦。

**問。我試過這些解決方案，但仍無法運作。現在怎麼辦？**

查看 *C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp* 中的記錄檔。此資料夾包含每個已執行之 R 訊息代理程式服務實例的個別記錄檔。 只要服務重新啟動，就會建立新的記錄檔。 請檢查最新記錄檔中是否有發生問題的線索。
