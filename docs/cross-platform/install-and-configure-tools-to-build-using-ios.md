---
title: 安裝和設定工具以使用 iOS 進行建置 | Microsoft Docs
ms.custom: ''
ms.date: 05/13/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 411ab7f097a82fa850e3850c662d378f51ffd548
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2019
ms.locfileid: "67586811"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>安裝和設定工具以使用 iOS 進行建置

您可以使用 Visual C++ for Cross-Platform Mobile Development 編輯、偵錯 iOS 程式碼並將其部署至 iOS 模擬器或 iOS 裝置，但由於授權限制，必須在 Mac 上遠端建置及執行程式碼。 若要使用 Visual Studio 建置並執行 iOS 應用程式，您必須在 Mac 上安裝及設定 [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988)遠端代理程式。 遠端代理程式會處理來自 Visual Studio 的建立要求，並在連接至 Mac 的 iOS 裝置或 Mac 中的 iOS 模擬器上執行應用程式。

> [!NOTE]
> 如需有關使用雲端裝載 Mac 服務 (而非使用 Mac) 的相關資訊，請參閱[設定 Visual Studio 以連線至雲端裝載的 Mac](/visualstudio/cross-platform/tools-for-cordova/tips-workarounds/host-a-mac-in-the-cloud?view=toolsforcordova-2017#configure-visual-studio-to-connect-to-your-cloud-hosted-mac) \(英文\)。 本指示是針對使用 Visual Studio Tools for Apache Cordova 進行建置。 若要使用這些指示以 C++ 進行建置，請以 vcremote 取代 remotebuild。

一旦您已安裝使用 iOS 進行建置的工具，請參閱本主題以取得可在 Visual Studio 及 Mac 上進行 iOS 開發快速設定和更新遠端代理程式的方式。

## <a name="prerequisites"></a>必要條件

若要安裝和使用遠端代理程式來開發 iOS 的程式碼，您必須先具備這些必要條件：

- 執行 macOS Mojave 版本 10.14 或更新版本的 Mac 電腦

- [Apple ID](https://appleid.apple.com/)

- 使用中的 [Apple Developer Program](https://developer.apple.com/programs/) 帳戶

   您可以取得免費帳戶，其允許將應用程式側載到 iOS 裝置以進行測試，但無法進行散發。

- [Xcode](https://developer.apple.com/xcode/downloads/) 版本 10.2.1 或更新版本

   您可以從 App Store 下載 Xcode。

- Xcode 命令列工具

   若要安裝 Xcode 命令列工具，請在 Mac 上開啟 Terminal 應用程式並輸入下列命令：

   `xcode-select --install`

- 在 Xcode 中設為簽署身分識別的 Apple ID 帳戶用來簽署應用程式

   若要在 Xcode 中查看或設定簽署識別，請開啟 [Xcode]  功能表並選擇 [喜好設定]  。 選取 [帳戶]  並選擇您的 Apple ID，然後選擇 [檢視詳細資料]  按鈕。 請參閱 [Add your Apple ID account](https://help.apple.com/xcode/mac/current/#/devaf282080a) (新增您的 Apple ID 帳戶) 以取得詳細說明。
   
   如需簽署需求的詳細資訊，請參閱 [What is app signing](https://help.apple.com/xcode/mac/current/#/dev3a05256b8) (什麼是應用程式簽署)。 

- 如果您是使用 iOS 裝置進行開發，請在 Xcode 中為您的裝置設定佈建設定檔

   Xcode 會提供自動簽署，視需要為您建立簽署憑證。 如需 Xcode 自動簽署的詳細資訊，請參閱 [automatic signing](https://help.apple.com/xcode/mac/current/#/dev80cc24546) (自動簽署)。

   若您想要進行手動簽署，您需要為您的應用程式建立佈建設定檔。 如需建立佈建設定檔的詳細資訊，請參閱 [Create a development provisioning profile](https://help.apple.com/developer-account/#/devf2eb157f8) (建立開發佈建設定檔)。 

- [Node.js](https://nodejs.org/) 版本 8.11.3 和 npm 版本 5.6.0

   在您的 Mac 上安裝 Node.js 版本 8.11.3。 若您安裝 Node.js 套件，它應該會隨附版本 5.6.0 的 npm。 請注意，其他版本的 Node.js 和 npm 可能不會支援遠端代理程式 vcremote 中所使用的某些模組，這可能會造成 vcremote 安裝失敗。

## <a name="Install"></a> 安裝 iOS 適用的遠端代理程式

當您安裝 Visual C++ for Cross-Platform Mobile Development 時，Visual Studio 可與在 Mac 上遠端執行的代理程式 [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988)通訊，以用來傳輸檔案、建置及執行您的 iOS 應用程式和傳送偵錯命令。

安裝遠端代理程式之前，請確定您已符合[必要條件](#prerequisites)，並且已安裝[適用於跨平台行動裝置應用程式開發的 Visual C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#install-the-tools)。

### <a name="DownloadInstall"></a> 若要下載及安裝遠端代理程式

- 從 Mac 上的 Terminal 應用程式，輸入：

   `sudo npm install -g --unsafe-perm vcremote`

   建議使用全域安裝 ( **-g**) 參數，但非必要。

   安裝期間會在您的 Mac 上安裝 vcremote 並啟動開發人員模式。 也會安裝[Homebrew](https://brew.sh/) 和兩個 npm 封裝、vcremote-lib 和 vcremote-utils 公用程式。 安裝完成時，針對已略過的選用相依性，您可以放心忽略相關的所有警告。

   > [!NOTE]
   > 若要安裝 Homebrew，您必須具備 sudo (系統管理員) 存取權。 如果您沒有 sudo 但要安裝 vcremote，可手動將 Homebrew 安裝到 usr/local 位置，並將它的 bin 資料夾加入路徑中。 如需詳細資訊，請參閱 [Homebrew 文件](https://github.com/Homebrew/homebrew/wiki/Installation)。 若要手動啟用開發人員模式，請在 Terminal 應用程式中輸入下列命令： `DevToolsSecurity -enable`

如果您已更新為新版 Visual Studio，也必須將遠端代理程式更新為目前版本。 若要更新遠端代理程式，請重複下載及安裝遠端代理程式的步驟。

## <a name="Start"></a> 啟動遠端代理程式

您必須為 Visual Studio 執行遠端代理程式，才能建置並執行您的 iOS 程式碼。 Visual Studio 必須搭配遠端代理程式才可進行通訊。 根據預設，遠端代理程式會以安全連線模式執行，其需要 PIN 碼與 Visual Studio 配對。

### <a name="RemoteAgentStartServer"></a> 若要啟動遠端代理程式

- 從 Mac 上的 Terminal 應用程式，輸入：

   `vcremote`

   隨即會以 ~/vcremote 的預設組建目錄啟動代理程式。 如需其他組態選項，請參閱 [Configure the remote agent on the Mac](#ConfigureMac)。

第一次啟動代理程式以及建立新的用戶端憑證時，會提供您在 Visual Studio 中設定代理程式的必要資訊，包括主機名稱、連接埠和 PIN 碼。

![使用 vcremote 產生安全性 PIN 碼](../cross-platform/media/cppmdd_vcremote_generateclientcert.png "CPPMDD_vcremote_generateClientCert")

如果您要使用主機名稱在 Visual Studio 中設定遠端代理程式，請使用主機名稱從 Windows ping 到 Mac 以確認可以存取。 如果不行，您可能要改用 IP 位址。

產生的 PIN 是供單次使用，並只在有限的期間內有效。 若您未在時效內將 Visual Studio 與遠端代理程式配對，則必須產生新的 PIN 碼。 如需詳細資訊，請參閱 [Generate a new security PIN](#GeneratePIN)。

您可以在不安全模式中使用遠端代理程式。 在不安全模式中，遠端代理程式可以在沒有 PIN 碼的情況下與 Visual Studio 配對。

#### <a name="to-disable-secured-connection-mode"></a>若要停用安全連線模式

- 若要停用 vcremote 的安全連接模式，請在 Mac 上的 Terminal 應用程式中輸入下列命令：

   `vcremote --secure false`

#### <a name="to-enable-secured-connection-mode"></a>若要啟用安全連線模式

- 若要啟用安全連線模式，請輸入下列命令：

   `vcremote --secure true`

一旦啟動遠端代理程式，您便可以從 Visual Studio 加以使用，直到您將其停止為止。

#### <a name="to-stop-the-remote-agent"></a>若要停止遠端代理程式

- 於正在執行 vcremote 的 [終端機] 視窗，輸入 **Control**+**C**。

## <a name="ConfigureVS"></a> 在 Visual Studio 中設定遠端代理程式

若要從 Visual Studio 連接到遠端代理程式，您必須在 Visual Studio 選項中指定遠端組態。

### <a name="to-configure-the-remote-agent-from-visual-studio"></a>若要從 Visual Studio 設定遠端代理程式

1. 如果 Mac 上的代理程式尚未執行，請遵循 [啟動遠端代理程式](#Start)中的步驟。 您的 Mac 必須為 Visual Studio 執行 vcremote，才可順利配對、連線並建置專案。

1. 在您的 Mac 上，取得 Mac 主機名稱或 IP 位址。

   您可以在 Terminal 視窗中使用 **ifconfig** 命令取得 IP 位址。 請使用作用中的網路介面底下所列的網際網路位址。

1. 在 Visual Studio 功能表列上，選擇 [工具]  、[選項]  。

1. 展開 [選項]  對話方塊中的 [跨平台]  、[C++]  、[iOS]  。

1. 在 [主機名稱]  和 [連接埠]  欄位中，輸入您啟動遠端代理程式時所指定的值。 主機名稱可能是您的 Mac DNS 名稱或 IP 位址。 預設連接埠是 3030。

   > [!NOTE]
   > 如果您無法使用主機名稱 ping 到 Mac，就需要使用 IP 位址。

1. 如果您是在預設的安全連線模式中使用遠端代理程式，請核取 [安全]  核取方塊，然後在 [Pin]  欄位中輸入遠端代理程式指定的 PIN 值。 如果您是在不安全的連線模式中使用遠端代理程式，請清除 [安全]  核取方塊，並將 [Pin]  欄位保留空白。

1. 若要啟用配對，請選擇 [配對]  。

   ![設定 iOS 組建的 vcremote 連線](../cross-platform/media/cppmdd_options_ios.PNG "CPPMDD_Options_iOS")

   配對會一直保存，直到您變更主機名稱或連接埠為止。 如果您變更 [選項]  對話方塊中的主機名稱或連接埠，要復原變更時，請選擇 [還原]  按鈕以還原為先前的配對。

   如果未成功配對，請遵循 [Start the remote agent](#Start)中的步驟，確認遠端代理程式正在執行。 如果在產生遠端代理程式 PIN 後經過太久時間，請在 Mac 上進行 [Generate a new security PIN](#GeneratePIN) 中的步驟並再試一次。 如果您是使用 Mac 的主機名稱，請嘗試改用 [主機名稱]  欄位中的 IP 位址。

1. 更新 [遠端根目錄]  欄位中的資料夾名稱，以指定 Mac 主目錄 ( *~* ) 中遠端代理程式所使用的資料夾。 根據預設，遠端代理程式會使用 /Users/`username`/vcremote 作為遠端根目錄。

1. 選擇 [確定]  以儲存配對的遠端連線設定。

每次使用時，Visual Studio 都會使用相同的資訊來連接 Mac 上的遠端代理程式。 您不需再次配對 Visual Studio 與遠端代理程式，除非您在 Mac 上產生新的安全性憑證或其主機名稱或 IP 位址有所變更。

## <a name="GeneratePIN"></a> Generate a new security PIN

第一次啟動遠端代理程式時，產生的 PIN 碼是有時效性的—預設為 10 分鐘。 若您未在時效內將 Visual Studio 與遠端代理程式配對，則必須產生新的安全 PIN 碼。

### <a name="to-generate-a-new-pin"></a>產生新的 PIN 碼

1. 停止代理程式，或在 Mac 上開啟第二個 Terminal 應用程式視窗，以在其中輸入命令。

1. 在 Terminal 應用程式中，輸入下列命令：

   `vcremote generateClientCert`

   遠端代理程式會產生新的暫存 PIN。 若要使用新的 PIN 碼配對 Visual Studio，請重複 [在 Visual Studio 中設定遠端代理程式](#ConfigureVS)中的步驟。

## <a name="GenerateCert"></a> 產生新的伺服器憑證

為了安全性目的，使用遠端代理程式配對出的 Visual Studio 伺服器憑證會與 Mac 的 IP 或主機名稱相關。 如果上述值有所變更，您就必須產生新的伺服器憑證，然後重新使用新值來設定 Visual Studio。

### <a name="to-generate-a-new-server-certificate"></a>若要產生新的伺服器憑證

1. 停止 vcremote 代理程式。

1. 在 Terminal 應用程式中，輸入下列命令：

   `vcremote resetServerCert`

1. 當提示確認時，請輸入 `Y`。

1. 在 Terminal 應用程式中，輸入下列命令：

   `vcremote generateClientCert`

   隨即產生新的暫存 PIN。

1. 若要使用新的 PIN 碼配對 Visual Studio，請重複 [在 Visual Studio 中設定遠端代理程式](#ConfigureVS)中的步驟。

## <a name="ConfigureMac"></a> Configure the remote agent on the Mac

您可以使用各種命令列選項來設定遠端代理程式。 例如，您可以指定要接聽組建要求的通訊埠，並指定要在檔案系統上維護的最大組建數目。 預設上限為 10 個組建。 遠端代理程式會在關閉時，移除超出上限的組建。

### <a name="to-configure-the-remote-agent"></a>若要設定遠端代理程式

- 若要查看遠端代理程式命令的完整清單，請在 Terminal 應用程式中輸入：

   `vcremote --help`

- 若要停用安全模式並啟用簡單 HTTP 連線，請輸入：

   `vcremote --secure false`

   當您在 Visual Studio 中設定代理程式時使用了此選項，請取消核取 [安全]  核取方塊，並將 [PIN 碼]  欄位保留空白。

- 若要指定遠端代理程式檔的位置，請輸入：

   `vcremote --serverDir directory_path`

   其中， *directory_path* 是 Mac 將會存放記錄檔、組建與伺服器憑證的位置。 根據預設，這個位置是 */Users/\<使用者名稱>/vcremote*。 在這個位置中，組建會依組建編號排列。

- 若要使用背景處理序將 `stdout` 和 `stderr` 擷取至名為 server.log 的檔案，請輸入：

   `vcremote > server.log 2>&1 &`

   server.log 檔可協助進行組建問題的疑難排解。

- 若要使用組態檔 (而不是命令列參數) 執行代理程式，請輸入：

   `vcremote --config config_file_path`

   其中， *config_file_path* 是 JSON 格式的組態檔路徑。 啟動選項及其值不得包含破折號。

## <a name="troubleshoot-the-remote-agent"></a>針對遠端代理程式進行疑難排解

### <a name="debugging-on-an-ios-device"></a>在 iOS 裝置上進行偵錯

若在 iOS 裝置上進行偵錯無法正常運作，則可能是 [ideviceinstaller](https://github.com/libimobiledevice/ideviceinstaller) 工具本身的問題，該工具會用來和 iOS 裝置通訊。 這項工具通常會在安裝 vcremote 期間從 Homebrew 進行安裝。 請遵循以下步驟作為因應措施。

開啟終端機應用程式，遵循下列順序執行命令來更新 ideviceinstaller 及其相依性：

1. 確認 Homebrew 已完成更新

   `brew update`

1. 解除安裝 libimobiledevice 和 usbmuxd

   `brew uninstall --ignore-dependencies libimobiledevice`

   `brew uninstall --ignore-dependencies usbmuxd`

1. 安裝最新版本的 libimobiledevice 和 usbmuxd

   `brew install --HEAD usbmuxd`

   `brew unlink usbmuxd`

   `brew link usbmuxd`

   `brew install --HEAD libimobiledevice`

1. 解除安裝並重新安裝 ideviceinstaller

   `brew uninstall ideviceinstaller`

   `brew install ideviceinstaller`

透過嘗試列出在裝置上安裝的應用程式，驗證 ideviceinstaller 可和裝置通訊：

`ideviceinstaller -l`

若 ideviceinstaller 傳回錯誤，顯示其無法存取資料夾 `/var/db/lockdown`，請使用以下命令變更資料夾上的權限：

`sudo chmod 777 /var/db/lockdown`
    
然後再次驗證 ideviceinstaller 是否可和裝置通訊。

## <a name="see-also"></a>另請參閱

- [安裝適用於跨平台行動裝置應用程式開發的 Visual C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
