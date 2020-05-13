---
title: 建立網路型安裝
description: 了解如何建立網路安裝點以在企業內部署 Visual Studio。
ms.date: 03/27/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1f9c1ffc0252f0fcd92f026c876adfc8ad694c41
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759725"
---
# <a name="create-a-network-installation-of-visual-studio"></a>建立 Visual Studio 的網路安裝

一般而言，企業系統管理員會建立網路安裝點，以部署至用戶端工作站。 Visual Studio 設計為能讓您快取初始安裝之檔案以及單一資料夾的所有產品更新。 (這個程序也稱為「建立配置」__)。

我們已完成這項作業，因此，用戶端工作站可以使用相同的網路位置來管理其安裝，即使它們尚未更新為最新的服務更新也是一樣。

 > [!NOTE]
 > 如果您的企業內使用多個 Visual Studio 版本 (例如，同時有 Visual Studio Professional 和 Visual Studio Enteprise)，則必須針對每個版本建立個別的網路安裝共用。

## <a name="download-the-visual-studio-bootstrapper"></a>下載 Visual Studio 啟動載入器

下載您想要的可視化工作室版本的引導程式檔。 請確保選擇 **「儲存**」,然後選擇 **「打開資料夾**」。

::: moniker range="vs-2017"

要獲取 Visual Studio 2017 的引導者,請參閱[Visual Studio 早期版本的](https://visualstudio.microsoft.com/vs/older-downloads/)下載頁面,瞭解如何執行此操作的詳細資訊。

設置可執行檔&mdash;或更具體,引導程式&mdash;檔 應匹配或類似於以下檔之一。

| 版本 | 檔案名稱 |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise.exe** |
|Visual Studio Professional | **vs_professional.exe** |
|Visual Studio Build Tools   | **vs_buildtools.exe** |

其他支援的引導者包括vs_feedbackclient.exe、vs_teamexplorer.exe、vs_testagent.exe、vs_testcontroller.exe和**vs_testprofessional.exe。** **vs_feedbackclient.exe** **vs_teamexplorer.exe** **vs_testagent.exe** **vs_testcontroller.exe**

::: moniker-end

::: moniker range="vs-2019"

設置可執行檔&mdash;或更具體,引導程式&mdash;檔 應匹配或類似於以下檔之一。

|版本 | 下載|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [**vs_buildtools.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

其他支援的引導者包括[vs_teamexplorer.exe、vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe)和[vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe)。 [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)

::: moniker-end

>[!TIP]
>如果您以前下載了一個引導程式檔,並希望驗證其版本,請介紹如何。 在 Windows 中,打開檔案資源管理器,右鍵單擊引導程式檔,選擇 **「屬性**」,選擇 **「詳細資訊**」選項卡,然後查看**產品版本**號。 要將該編號與 Visual Studio 版本相匹配,請參閱[Visual Studio 生成編號和發佈日期](visual-studio-build-numbers-and-release-dates.md)頁面。

## <a name="create-an-offline-installation-folder"></a>建立離線安裝資料夾

您必須連接網際網路，才能完成此步驟。 要建立具有所有語言和所有功能的離線安裝,請使用類似於以下範例之一的命令。

   > [!IMPORTANT]
   > 完整的 Visual Studio 配置至少需要 35 GB 磁碟空間，且下載需要一些時間。 如需如何僅使用您想要安裝的元件來建立配置的詳細資料，請參閱[自訂網路配置](#customize-the-network-layout)一節。
   >
   > [!TIP]
   > 請確定您是從 [下載] 目錄執行命令。 通常在執行 Windows 10 的電腦上，這會是 `C:\Users\<username>\Downloads`。

- 針對 Visual Studio Enterprise，請執行：

  ```vs_enterprise.exe --layout c:\VSLayout```

- 針對 Visual Studio Professional，請執行：

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>修改 response.json 檔案

您可以修改 response.json，以設定安裝程式執行時所使用的預設值。  例如，您可以設定 `response.json` 檔案來自動選取所選的一組特定工作負載。 如需詳細資訊，請參閱[使用回應檔自動安裝 Visual Studio](automated-installation-with-response-file.md)。

此外,如果您在將 Visual Studio 引導器與回應.json 檔配對時遇到問題,[請參閱安裝或使用 Visual Studio 頁時疑難排解網路相關錯誤的](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process)「無法解析 ID」部分,瞭解有關操作操作的詳細資訊。

## <a name="copy-the-layout-to-a-network-share"></a>將配置複製到網路共用

在網路共用上裝載配置，以便能夠從其他電腦執行。

下列範例會使用 [xcopy](/windows-server/administration/windows-commands/xcopy/)。 如果您想要的話，也可以使用 [robocopy](/windows-server/administration/windows-commands/robocopy/)。  

::: moniker range="vs-2017"

範例：

```cmd
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```cmd
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

> [!IMPORTANT]
> 為了防止發生錯誤，完整安裝路徑請務必少於 80 個字元。

## <a name="customize-the-network-layout"></a>自訂網路配置

有數個選項可供您用來自訂網路配置。 您可以建立部分配置，以便只包含一組特定[語言地區設定](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)、[工作負載、元件，及其建議或選擇性相依性](workload-and-component-ids.md)。 如果您知道只會在用戶端工作站部署一部分的工作負載，這可能十分有用。 用於自訂配置的一般命令列參數包括：

* `--add`以指定[工作負載或元件的號。](workload-and-component-ids.md) <br>如果使用 `--add`，則只會下載使用 `--add` 指定的工作負載和元件。  如未使用 `--add`，則會下載所有工作負載和元件。
* `--includeRecommended` 可包含指定工作負載識別碼的所有建議元件
* `--includeOptional` 可包含指定工作負載識別碼的所有建議和選擇性元件。
* `--lang` 可指定[語言地區設定](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)。

下列範例示範如何建立自訂部分配置。

* 若要下載僅適用於一種語言的所有工作負載和元件，請執行：

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* 若要下載適用於多種語言的所有工作負載和元件，請執行：

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* 若要下載適用於所有語言的單一工作負載，請執行：

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* 若要下載適用於三種語言的兩個工作負載和一個選擇性元件，請執行：

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* 下載兩個工作負載及其所有建議元件：

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* 若要下載兩個工作負載及其所有建議和選擇性原件，請執行：

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>15.3 版的新功能

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>儲存您的配置選項

::: moniker-end

當您執行配置命令時，會儲存您指定的選項 (例如工作負載和語言)。 後續配置命令會包含所有先前的選項。  以下是只包含一份英文工作負載的配置範例：

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

當您想要將該配置更新為較新版本時，不需要指定任何其他命令列參數。 會儲存先前的設定，並供這個配置資料夾中的任何後續配置命令使用。  下列命令會更新現有的部分配置。

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

當您想要新增額外的工作負載時，以下是做法範例。 在此情況下，我們將新增 Azure 工作負載和當地語系化語言。  現在，Managed 桌面和 Azure 都會包含在此配置中。  所有這些工作負載都會包含英文和德文的語言資源。 配置會更新為最新的可用版本。

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

如果您想要將現有配置更新為完整配置，請使用 --all 選項，如下列範例所示。

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>從網路安裝部署

系統管理員可以在執行安裝指令碼時，將 Visual Studio 部署到用戶端工作站。 或者，具有系統管理員權限的使用者可以直接從共用執行安裝程式，以在其電腦上安裝 Visual Studio。

* 使用者可以執行下列命令來安裝： <br>

    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* 系統管理員可以執行下列命令，以便使用自動模式來安裝：

    ```cmd
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

::: moniker range="vs-2019"
> [!IMPORTANT]
> 對於離線安裝,如果收到一條錯誤消息,指出「找不到與以下參數匹配的產品」,請確保將`--noweb`交換機與版本 16.3.5 或更高版本一起使用。
>
::: moniker-end

當您從配置進行安裝時，會從配置中取得已安裝的內容。 不過，如果您選取的元件不在配置中，則會從網際網路取得。  如果您想要防止 Visual Studio 安裝程式下載您配置中遺漏的任何內容，請使用 `--noWeb` 選項。 如果使用 `--noWeb`，而且配置遺失已選取要安裝的任何內容，則安裝程式會失敗。

> [!TIP]
> 如果要在非 Internet 連接的電腦上從離線來源安裝,請同時`--noWeb``--noUpdateInstaller`指定和選項。 前者阻止下載更新的工作負載、元件等。 後者阻止安裝程式從 Web 自我更新。

> [!IMPORTANT]
> 該`--noWeb`選項不會阻止 Internet 電腦上的 Visual Studio 設置檢查更新。 如需詳細資訊，請參閱[控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)頁面。

### <a name="error-codes"></a>錯誤碼

如果已使用 `--wait` 參數，則會根據作業的結果，將 `%ERRORLEVEL%` 環境變數設定為下列其中一個值：

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>更新網路安裝配置

當產品更新可用時，您可以[更新網路安裝配置](update-a-network-installation-of-visual-studio.md)，以納入更新的套件。

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>如何建立舊版 Visual Studio 的配置

::: moniker range="vs-2017"

> [!NOTE]
> [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) 所提供 Visual Studio 啟動載入器，會下載並安裝執行時可用的最新版 Visual Studio。
>
> 因此，如果您今天下載 Visual Studio「啟動載入器」**，並在六個月後執行，則其會安裝您在執行啟動載入器時的最新版 Visual Studio。
>
> 但是，如果您建立「配置」** 並從該配置進行安裝，則會安裝存在於該配置中的特定 Visual Studio 版本。 即使線上可能有較新的版本，您仍會取得該配置中的 Visual Studio 版本。

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads) 所提供 Visual Studio 啟動載入器，會下載並安裝執行時可用的最新版 Visual Studio。
>
> 因此，如果您今天下載 Visual Studio「啟動載入器」**，並在六個月後執行，則其會安裝您在執行啟動載入器時的最新版 Visual Studio。
>
> 但是，如果您建立「配置」** 並從該配置進行安裝，則會安裝存在於該配置中的特定 Visual Studio 版本。 即使線上可能有較新的版本，您仍會取得該配置中的 Visual Studio 版本。

::: moniker-end

如果需要為舊版本的 Visual Studio 創建佈局,[https://my.visualstudio.com](https://my.visualstudio.com)請轉到 下載「固定」版本的 Visual Studio 引導器。

### <a name="how-to-get-support-for-your-offline-installer"></a>如何取得離線安裝程式的支援

如果您的離線安裝發生問題，我們會想要進行了解。 告訴我們的最簡單方式就是使用[回報問題](../ide/how-to-report-a-problem-with-visual-studio.md)工具。 使用此工具時，您可以將我們所需的遙測和記錄檔傳送給我們，來協助我們診斷及修正問題。

我們也提供[**安裝聊天**](https://visualstudio.microsoft.com/vs/support/#talktous) (僅限英文) 支援選項，可回答安裝的相關問題。

我們也提供其他支援選項。 如需清單，請參閱我們的[意見反應](../ide/feedback-options.md)頁面。

## <a name="see-also"></a>另請參閱

- [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
- [更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)
- [安裝或使用視覺化工作室時解決與網路相關的錯誤](troubleshooting-network-related-errors-in-visual-studio.md)
- [控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
- [視覺化工作室產品生命週期和服務](/visualstudio/releases/2019/servicing/)
- [在維護基底上時更新 Visual Studio](update-servicing-baseline.md)
- [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)
- [安裝 Visual Studio 離線安裝所需的憑證](install-certificates-for-visual-studio-offline.md)