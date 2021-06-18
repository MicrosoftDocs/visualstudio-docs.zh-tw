---
title: 建立網路型安裝
description: 了解如何建立網路安裝點以在企業內部署 Visual Studio。
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 080c4450cfcdca28386811865229af75303beb6a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307527"
---
# <a name="create-a-network-installation-of-visual-studio"></a>建立 Visual Studio 的網路安裝

有時候企業系統管理員想要建立一個網路安裝點，其中包含可部署至用戶端工作站的 Visual Studio 檔案。 這是為了協助用戶端電腦對網際網路的許可權有限或有限存取，或在內部小組想要在其組織在特定版本的開發人員工具組上進行標準化之前進行相容性測試。 我們已設計 Visual Studio，讓系統管理員可以 _建立網路_ 配置，其主要是建立位於內部靜態網路共用上的檔案快取，其中包含初始安裝和未來所有產品更新的所有 Visual Studio 檔。

 > [!NOTE]
 >  - 如果您的企業 (使用多個版本的 Visual Studio，例如 Visual Studio 2019 Professional 和 Visual Studio 2019 Enterprise) ，則必須為每個版本建立個別的網路安裝共用。
 >  - 建議您在進行初始用戶端安裝 _之前_ ，決定用戶端接收產品更新的方式。  這可讓您更輕鬆地確保設定選項的設定正確無誤。 您的選擇包括讓用戶端從網路設定位置或從網際網路取得更新。 
 >  - 原始的 Visual Studio 安裝配置和所有後續的產品更新都必須位於相同的網路目錄中，以確保修復和卸載功能正常運作。

## <a name="download-the-visual-studio-bootstrapper"></a>下載 Visual Studio 啟動載入器

下載您想要的 Visual Studio 版本的啟動載入器檔案。 請務必選擇 [ **儲存**]，然後選擇 [ **開啟資料夾**]。

::: moniker range="vs-2017"

若要取得 Visual Studio 2017 15.9 版的最新啟動載入器，請移至 [Visual Studio 的舊版](https://visualstudio.microsoft.com/vs/older-downloads/) 頁面，並下載下列其中一個啟動載入器檔案：

| 版本                                      | 檔案名稱            |
|----------------------------------------------|---------------------|
| Visual Studio 2017 Enterprise 15.9 版   | vs_enterprise.exe   |
| Visual Studio 2017 Professional 15.9 版 | vs_professional.exe |
| Visual Studio 2017 Build Tools 15.9 版  | vs_buildtools.exe   |

其他支援的啟動載入器包括 vs_feedbackclient.exe、vs_teamexplorer.exe、vs_testagent.exe、vs_testcontroller.exe 和 vs_testprofessional.exe。

::: moniker-end

::: moniker range="vs-2019"

一開始請從 [Visual Studio 下載] 頁面](https://visualstudio.microsoft.com/downloads) 或 [Visual Studio 2019 發行](/visualstudio/releases/2019/history#installing-an-earlier-release) 版頁面下載 Visual Studio 2019 啟動載入器，以供您選擇的版本和版本的 Visual Studio 使用。  您的安裝程式可執行 &mdash; 檔或更具體來說，啟動載入器檔案 &mdash; 將會符合或類似下列其中一項：

| 版本                    | 下載                                                                                                                                                                                                                           |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019)     |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools  | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

其他支援的啟動載入器包括 [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe)、 [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)和 [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe)。

::: moniker-end

::: moniker range=">=vs-2022"

>![!TIP]
> Visual Studio 2022 的發行版本尚無法使用，以下啟動載入器適用于 Visual Studio 2022 的預覽版本。
從 [Visual Studio 下載] 頁面](https://aka.ms/vs2022preview)下載 Visual Studio 2022 啟動載入器開始。

| 版本                    | 下載                                                                             |
|----------------------------|--------------------------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/preview/bootstrapper/vs_enterprise.exe)     |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/17/preview/bootstrapper/vs_professional.exe) |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>如果您先前已下載啟動載入器檔案，而且想要確認它的版本，請參閱。 在 Windows 中，開啟檔案總管，以滑鼠右鍵按一下啟動載入器檔案，選擇 [ **屬性**]，選擇 [ **詳細資料** ] 索引標籤，然後查看 **產品版本** 號碼。 若要將該數位符合 Visual Studio 的版本，請參閱 [Visual Studio 組建編號和發行日期](visual-studio-build-numbers-and-release-dates.md)。

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>如果您先前已下載啟動載入器檔案，而且想要確認它的版本，請參閱。 在 Windows 中，開啟檔案總管，以滑鼠右鍵按一下啟動載入器檔案，選擇 [ **屬性**]，選擇 [ **詳細資料** ] 索引標籤，然後查看 **產品版本** 號碼。 若要將該號碼符合 Visual Studio 的版本，請參閱 [Visual Studio 2019 版本](/visualstudio/releases/2019/history)。

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>如果您先前已下載啟動載入器檔案，而且想要確認它的版本，請參閱。 在 Windows 中，開啟檔案總管，以滑鼠右鍵按一下啟動載入器檔案，選擇 [ **屬性**]，選擇 [ **詳細資料** ] 索引標籤，然後查看 **產品版本** 號碼。 若要將該號碼符合 Visual Studio 的版本，請參閱 [Visual Studio 2022 版本](/visualstudio/releases/2022/history)。

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>建立離線安裝資料夾

您必須連接網際網路，才能完成此步驟。

開啟命令提示字元，流覽至您下載啟動載入器的目錄，並使用啟動載入器的參數，如 [使用命令列參數](../install/use-command-line-parameters-to-install-visual-studio.md) 中所定義，以安裝 Visual Studio 頁面來建立和維護您的網路安裝快取。 以下說明建立初始配置的常見範例，以及 [Visual Studio 安裝的命令列參數範例](../install/command-line-parameter-examples.md)。  

   > [!IMPORTANT]
   > 單一語言地區設定的完整初始配置需要大約 35 GB 的磁碟空間，Visual Studio Community 和 42 GB 的 Visual Studio Enterprise。 其他 [語言地區](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) 設定每個都需要大約一半的 GB。 如需詳細資訊，請參閱 [自訂網路](#customize-the-network-layout) 配置一節。 請注意，後續的版面配置更新也必須儲存在相同的網路位置中，如此一來，網路設定位置的目錄內容可能會在一段時間內變得很大。  

- 若要建立包含所有語言和所有功能之 Visual Studio Enterprise 的初始配置，請執行：

  ```vs_enterprise.exe --layout c:\VSLayout```

- 若要建立包含所有語言和所有功能之 Visual Studio Professional 的初始配置，請執行：

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>修改 response.json 檔案

您可以修改檔案， `response.json` 以設定執行安裝程式時所使用的預設值。  例如，您可以將檔案設定 `response.json` 為選取應自動選取的一組特定工作負載。 您也可以設定， `response.json` 以指定用戶端是否應該只從網路設定位置接收更新的檔案。 如需詳細資訊，請參閱 [使用回應檔自動化 Visual Studio 安裝](../install/automated-installation-with-response-file.md)。 

如果您在將它與檔案配對時發生 Visual Studio 啟動載入器擲回錯誤的問題 `response.json` ，請參閱在 [安裝或使用 Visual Studio 頁面時疑難排解網路相關錯誤](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) ，以取得詳細資訊。

## <a name="copy-the-layout-to-a-network-share"></a>將配置複製到網路共用

在網路共用上裝載配置，讓它可以從用戶端電腦執行。

下列範例會使用 [`xcopy`](/windows-server/administration/windows-commands/xcopy/) 。 如果 [`robocopy`](/windows-server/administration/windows-commands/robocopy/) 您想要的話，也可以使用。

::: moniker range="vs-2017"

範例：

```shell
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```shell
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

::: moniker range=">=vs-2022"

```shell
xcopy /e c:\VSLayout \\server\products\VS2022
```

::: moniker-end

> [!IMPORTANT]
> 為了防止發生錯誤，完整安裝路徑請務必少於 80 個字元。

## <a name="customize-the-network-layout"></a>自訂網路配置

有數個選項可供您用來自訂網路配置。 您可以建立部分配置，以便只包含一組特定[語言地區設定](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)、[工作負載、元件，及其建議或選擇性相依性](workload-and-component-ids.md)。 如果您知道只會在用戶端工作站部署一部分的工作負載，這可能十分有用。 用於自訂配置的一般命令列參數包括：

* `--add` 指定 [工作負載或元件識別碼](workload-and-component-ids.md)。 <br>如果使用 `--add`，則只會下載使用 `--add` 指定的工作負載和元件。  如未使用 `--add`，則會下載所有工作負載和元件。
* `--includeRecommended` 可包含指定工作負載識別碼的所有建議元件
* `--includeOptional` 可包含指定工作負載識別碼的所有建議和選擇性元件。
* `--lang` 可指定[語言地區設定](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)。

下列範例示範如何建立自訂部分配置。

* 若要下載僅適用於一種語言的所有工作負載和元件，請執行：

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* 若要下載適用於多種語言的所有工作負載和元件，請執行：

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* 若要下載適用於所有語言的單一工作負載，請執行：

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* 若要下載適用於三種語言的兩個工作負載和一個選擇性元件，請執行：

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* 下載兩個工作負載及其所有建議元件：

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* 若要下載兩個工作負載及其所有建議和選擇性原件，請執行：

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

### <a name="save-your-layout-options"></a>儲存您的配置選項

當您執行配置命令時，會儲存您指定的選項 (例如工作負載和語言)。 後續配置命令會包含所有先前的選項。  以下是只包含一份英文工作負載的配置範例：

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

當您想要將該配置更新為較新版本時，不需要指定任何其他命令列參數。 會儲存先前的設定，並供這個配置資料夾中的任何後續配置命令使用。  下列命令會更新現有的部分配置。

```shell
vs_enterprise.exe --layout c:\VSLayout
```

當您想要新增額外的工作負載時，以下是做法範例。 在此情況下，我們將新增 Azure 工作負載和當地語系化語言。  現在，Managed 桌面和 Azure 都會包含在此配置中。  所有這些工作負載都會包含英文和德文的語言資源。 配置會更新為最新的可用版本。

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

如果您想要將現有配置更新為完整配置，請使用 --all 選項，如下列範例所示。

```shell
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>從網路安裝部署

系統管理員可以在執行安裝指令碼時，將 Visual Studio 部署到用戶端工作站。 或者，具有系統管理員權限的使用者可以直接從共用執行安裝程式，以在其電腦上安裝 Visual Studio。

* 使用者可以執行下列命令來安裝： <br>

    ```shell
    \\server\products\VS\vs_enterprise.exe
    ```

* 系統管理員可以執行下列命令，以便使用自動模式來安裝：

    ```shell
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> 為了防止發生錯誤，完整安裝路徑請務必少於 80 個字元。

> [!TIP]
> 作為批次檔的一部分執行時，`--wait` 選項可確保 `vs_enterprise.exe` 程序先等到安裝完成，再傳回結束代碼。
>
> 如果企業系統管理員想要對已完成的安裝執行進一步動作 (例如，[將產品金鑰套用至成功安裝](automatically-apply-product-keys-when-deploying-visual-studio.md))，則這十分有用，但是必須等待安裝完成才能處理來自該安裝的傳回碼。
>
> 如果您未使用 `--wait`，則 `vs_enterprise.exe` 程序會在安裝完成之前結束，並傳回未代表安裝作業狀態的不正確結束代碼。
>

::: moniker range=">=vs-2019"
> [!IMPORTANT]
> 針對離線安裝，如果您收到錯誤訊息，指出「找不到符合下列參數的產品」，請確定您使用的是 `--noweb` 16.3.5 版版或更新版本的參數。
>
::: moniker-end

當您從配置進行安裝時，會從配置中取得已安裝的內容。 不過，如果您選取的元件不在配置中，則會從網際網路取得。  如果您想要防止 Visual Studio 安裝程式下載您配置中遺漏的任何內容，請使用 `--noWeb` 選項。 如果使用 `--noWeb`，而且配置遺失已選取要安裝的任何內容，則安裝程式會失敗。

> [!TIP]
> 如果您想要從非網際網路連線電腦上的離線來源進行安裝，請同時指定 `--noWeb` 和 `--noUpdateInstaller` 選項。 前者會防止下載更新的工作負載、元件等等。 後者會防止安裝程式從 web 自行進行更新。

> [!IMPORTANT]
> 此 `--noWeb` 選項不會在連線到網際網路的電腦上停止 Visual Studio 安裝程式，以檢查是否有更新。 如需詳細資訊，請參閱[控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)頁面。

### <a name="error-codes"></a>錯誤碼

如果已使用 `--wait` 參數，則會根據作業的結果，將 `%ERRORLEVEL%` 環境變數設定為下列其中一個值：

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>更新網路安裝配置

當產品更新可用時，您可以[更新網路安裝配置](update-a-network-installation-of-visual-studio.md)，以納入更新的套件。

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>如何建立舊版 Visual Studio 的配置

首先，您必須瞭解有兩種類型的 Visual Studio 啟動載入器：一個可依「最新」、「目前」、「長達」和「提示」等字，以及基本上表示「固定版本」的文字。 這兩種類型的啟動載入器檔案都有完全相同的名稱，而用來區別類型的最佳方式，就是要注意您的所在位置。 [Visual Studio 下載] 頁面](https://visualstudio.microsoft.com/downloads)上提供的 Visual Studio 啟動載入器會被視為長 Visual Studio 啟動載入器，而且一律會在執行啟動載入器時，安裝 (或更新) 通道中可用的最新版本。 [Visual Studio 2019 版](/visualstudio/releases/2019/history) [Visual Studio 2022 版](/visualstudio/releases/2022/history)頁面上提供的 Visual Studio 啟動載入器，或內嵌在 Microsoft Update 目錄中的系統管理員更新內的可安裝特定的固定版本產品。

因此，如果您今天下載了長時間的 Visual Studio 啟動載入器，並在六個月後執行，則會在執行啟動載入器時安裝最新的 Visual Studio 版本。 它是設計來一律安裝最新的位，並讓您保持最新版本。

如果您下載固定連結啟動載入器，或您執行從 Microsoft Catalog 下載的系統管理員更新，則一律會安裝特定版本的產品，而不需要執行任何作業。

最後，您可以使用這些啟動載入器中的任何一個來建立網路設定，而將在配置中建立的版本取決於您所使用的啟動載入器，例如，它將會是固定版本或最新版本。 然後，您可以使用任何稍後的啟動載入器來更新網路設定，也可以使用 Microsoft Update 目錄中的系統管理員更新套件。 無論您如何更新版面配置，產生的更新版面配置將會是包含特定產品版本的套件快取，而且其行為就像是固定的連結啟動載入器。 因此，每當用戶端從配置進行安裝時，用戶端就會安裝存在於配置 (的特定 Visual Studio 版本，即使有較新版本可能存在於線上) 也一樣。

### <a name="how-to-get-support-for-your-offline-installer"></a>如何取得離線安裝程式的支援

如果您的離線安裝發生問題，我們會想要進行了解。 告訴我們的最簡單方式就是使用[回報問題](../ide/how-to-report-a-problem-with-visual-studio.md)工具。 使用此工具時，您可以將我們所需的遙測和記錄檔傳送給我們，來協助我們診斷及修正問題。

我們也提供 [**安裝聊天**](https://visualstudio.microsoft.com/vs/support/#talktous) (僅限英文) 支援選項，可回答安裝的相關問題。

我們也提供其他支援選項。 如需清單，請參閱我們的[意見反應](../ide/feedback-options.md)頁面。

## <a name="see-also"></a>另請參閱

- [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
- [更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)
- [當您安裝或使用 Visual Studio 時針對網路相關錯誤進行疑難排解](troubleshooting-network-related-errors-in-visual-studio.md)
- [控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
- [Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing/)
- [在維護基底上時更新 Visual Studio](update-servicing-baseline.md)
- [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)
- [安裝 Visual Studio 離線安裝所需的憑證](install-certificates-for-visual-studio-offline.md)
