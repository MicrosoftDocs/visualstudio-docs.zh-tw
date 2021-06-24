---
title: 建立離線安裝
description: 了解如何在有不可靠網際網路連線或低頻寬時離線安裝 Visual Studio。
ms.date: 4/16/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b10fc1adbb0b4a6e053549749ea90acf3919d0c6
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602205"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>建立 Visual Studio 的離線安裝

::: moniker range="vs-2017"

我們已設計 Visual Studio 2017 可在各種網路和電腦組態中正常運作。 雖然我們建議您嘗試 Visual Studio 的[web 安裝程式](https://visualstudio.microsoft.com/vs/older-downloads)， &mdash; 這是一個小型檔案，可讓您隨時掌握我們瞭解的最新修正程式和功能， &mdash; 您可能無法使用。

::: moniker-end

::: moniker range=">=vs-2019"

我們設計 Visual Studio 2019 和更新版本，以便在各種網路和電腦設定中順利運作。 雖然我們建議您嘗試 Visual Studio 的[web 安裝程式](https://visualstudio.microsoft.com/downloads)， &mdash; 這是一個小型檔案，可讓您隨時掌握我們瞭解的最新修正程式和功能， &mdash; 您可能無法使用。

::: moniker-end

例如，您可能有不可靠網際網路連線，或具有低頻寬的連線。 因此，您有幾個選項：您可以使用新的 [全部下載後安裝] 功能來下載檔案後再安裝，也可以使用命令列來建立檔案的本機快取。

> [!NOTE]
> 如果您是企業系統管理員，想要將 Visual Studio 部署至已啟用網際網路防火牆的用戶端工作站網路，請參閱[建立 Visual Studio 的網路安裝](../install/create-a-network-installation-of-visual-studio.md)和[安裝 Visual Studio 離線安裝所需憑證](../install/install-certificates-for-visual-studio-offline.md)頁面。

## <a name="use-the-download-all-then-install-feature"></a>使用 [全部下載後安裝] 功能

::: moniker range="vs-2017"

[**15.8 版的新**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install)功能：下載 web 安裝程式之後，請從 Visual Studio 安裝程式選取 [ **全部下載]，然後** 選取 [安裝] 選項。 然後，繼續執行您的安裝。

   ![[全部下載後安裝] 選項](media/download-all-then-install.png)

::: moniker-end

::: moniker range=">=vs-2019"

在您下載 Web 安裝程式之後，請從 Visual Studio 安裝程式中選取新的 [全部下載後安裝] 選項。 然後，繼續執行您的安裝。

   ![[全部下載後安裝] 選項](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

我們設計了 [全部下載後安裝] 功能，讓您能夠針對下載 Visual Studio 的同一部電腦將 Visual Studio 下載成單一安裝。 如此一來，您便可以放心地先中斷與 Web 的連線，再安裝 Visual Studio。

> [!IMPORTANT]
> 請勿使用 [全部下載後安裝] 功能來建立要傳輸至另一部電腦的離線快取。 此功能並不是設計來進行該用途。 <br><br>如果您想要在本機電腦上建立離線快取，然後用來安裝 Visual Studio，請參閱下面的 [使用命令列來建立本機](#use-the-command-line-to-create-a-local-cache) 快取一節。  或者，[ [建立 Visual Studio 的網路安裝](../install/create-a-network-installation-of-visual-studio.md) ] 頁面提供如何在網路上建立快取的相關資訊。

## <a name="use-the-command-line-to-create-a-local-cache"></a>使用命令列來建立本機快取
::: moniker range="vs-2017"

在您下載小型啟動載入器之後，請使用命令列來建立本機快取。 然後，使用本機快取安裝 Visual Studio  (此程式會取代舊版) 可用的 ISO 檔案。 

::: moniker-end

::: moniker range=">=vs-2019"

下載小型啟動載入器檔案之後，請使用命令列來建立本機快取。 然後，使用本機快取安裝 Visual Studio

::: moniker-end

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>步驟 1 - 下載 Visual Studio 啟動載入器

您必須連接網際網路，才能完成此步驟。

::: moniker range="vs-2017"

若要取得 Visual Studio 2017 15.9 版的最新啟動載入器，請移至 [Visual Studio 的舊版](https://visualstudio.microsoft.com/vs/older-downloads/) 頁面，並下載下列其中一個啟動載入器檔案：

| 版本                                      | 檔案名稱            |
|----------------------------------------------|---------------------|
| Visual Studio Professional 2017 15.9 版 | vs_professional.exe |
| Visual Studio Enterprise 2017 15.9 版   | vs_enterprise.exe   |
| Visual Studio Build Tools 2017 15.9 版  | vs_buildtools.exe   |

::: moniker-end

::: moniker range="vs-2019"

一開始請從 [Visual Studio 下載] 頁面](https://visualstudio.microsoft.com/downloads) 或 [Visual Studio 2019 發行](/visualstudio/releases/2019/history#installing-an-earlier-release) 版頁面下載 Visual Studio 2019 啟動載入器，以供您選擇的版本和版本的 Visual Studio 使用。 您的安裝程式檔案或啟動載入器 &mdash; &mdash; 將會符合或類似于下列其中一項：

| 版本                         | 檔案                                                                                                                                                                                                                               |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Studio 2019 Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio 2019 Build Tools  | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
> Visual Studio 2022 的發行版本尚無法使用，以下啟動載入器適用于 Visual Studio 2022 的預覽版本。
>從 [Visual Studio 下載] 頁面](https://aka.ms/vs2022preview)下載 Visual Studio 2022 啟動載入器開始。

| 版本                         | 下載                                                            |
|---------------------------------|---------------------------------------------------------------------|
| Visual Studio 2022 專業版 | [vs_professional.exe](https://aka.ms/vs/17/pre/vs_professional.exe) |
| Visual Studio 2022 企業版   | [vs_enterprise.exe](https://aka.ms/vs/17/pre/vs_enterprise.exe)     |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>如果您先前已下載啟動載入器檔案，而且想要確認它的版本，請參閱。 在 Windows 中，開啟檔案總管，以滑鼠右鍵按一下啟動載入器檔案，選擇 [ **屬性**]，選擇 [ **詳細資料** ] 索引標籤，然後查看 **產品版本** 號碼。 若要將該號碼符合 Visual Studio 的版本，請參閱 [Visual Studio 組建編號和發行日期](/visual-studio-build-numbers-and-release-dates.md) ] 頁面。

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>如果您先前已下載啟動載入器檔案，而且想要驗證其版本，請參閱以下說明。 在 Windows 中，開啟檔案總管，以滑鼠右鍵按一下啟動載入器檔案，選擇 [ **屬性**]，選擇 [ **詳細資料** ] 索引標籤，然後查看 **產品版本** 號碼。 若要將該號碼符合 Visual Studio 的版本，請參閱 [Visual Studio 2019 版本](/visualstudio/releases/2019/history) 頁面。

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>如果您先前已下載啟動載入器檔案，而且想要驗證其版本，請參閱以下說明。 在 Windows 中，開啟檔案總管，以滑鼠右鍵按一下啟動載入器檔案，選擇 [ **屬性**]，選擇 [ **詳細資料** ] 索引標籤，然後查看 **產品版本** 號碼。 若要將該號碼符合 Visual Studio 的版本，請參閱 [Visual Studio 2022 版本](/visualstudio/releases/2022/history) 頁面。

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>步驟 2 - 建立本機安裝快取

您必須連接網際網路，才能完成此步驟。

開啟命令提示字元，並使用啟動載入器的參數，如 [使用命令列參數](use-command-line-parameters-to-install-visual-studio.md) 中所定義，以安裝 Visual Studio 頁面來建立本機安裝快取。 使用企業啟動載入器的常見範例如下所示，以及在 [命令列參數範例](command-line-parameter-examples.md) 頁面中。 您可以 `en-US` 從 [語言地區設定清單](#list-of-language-locales)中變更為地區設定，以安裝英文以外的語言，而且可以使用 [元件和工作負載的清單](workload-and-component-ids.md) 來進一步自訂您的快取。

> [!TIP]
> 為了防止發生錯誤，請確保完整安裝路徑少於 80 個字元。

- 針對 .NET Web 和 .NET 桌面開發，請執行：

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- 針對 .NET 桌面和 Office 開發，請執行：

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- 針對 C++ 桌面開發，請執行：

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- 若要建立完整的本機版面配置（僅限英文版）， (這項功能需要很長 &mdash; 的時間！ ) ，請執行： 

   ```shell
    vs_enterprise.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > 完整的 Visual Studio 配置至少需要 35 GB 磁碟空間。 如需詳細資訊，請參閱 [系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs/)。 

::: moniker-end

::: moniker range=">=vs-2019"

   > [!NOTE]
   > 完整的 Visual Studio 版面配置需要至少 41 GB 的磁碟空間。 如需詳細資訊，請參閱 [系統需求](/visualstudio/releases/2019/system-requirements/)。

::: moniker-end


### <a name="step-3---install-visual-studio-from-the-local-cache"></a>步驟 3 - 從本機快取安裝 Visual Studio
當您從本機安裝快取安裝 Visual Studio 時，Visual Studio 安裝程式會使用檔案的本機快取版本。 但是，如果您在安裝期間選取的元件不在快取中，則 Visual Studio 安裝程式會嘗試從網際網路下載它們。 為確保您只安裝先前下載的檔案，請使用您用來建立配置快取的相同 [命令列選項](use-command-line-parameters-to-install-visual-studio.md) 。 

例如，如果您使用下列命令來建立本機安裝快取：

```shell
vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

然後，使用此命令來執行安裝：

```shell
c:\vslayout\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!IMPORTANT]
> 如果您使用 Visual Studio Community，則必須在安裝後的30天內登入產品來啟用它。 啟用需要網際網路連線。

> [!NOTE]
> 如果您收到錯誤，表示簽章無效，則必須 [安裝更新的憑證](install-certificates-for-visual-studio-offline.md)。 開啟離線快取中的 [憑證] 資料夾。 按兩下每個憑證檔案，然後點選完成 [憑證管理員精靈]。 如果系統要求您輸入密碼，則請保留空白。

::: moniker range=">=vs-2019"
> [!TIP]
> 針對離線安裝，如果您收到錯誤訊息，指出「找不到符合下列參數的產品」，請確定您使用的是 `--noweb` 16.3.5 版版或更新版本的參數。

::: moniker-end

### <a name="list-of-language-locales"></a>語言地區設定清單

| **語言地區設定** | **Language**          |
|---------------------|-----------------------|
| cs-CZ               | 捷克文                 |
| de-DE               | 德文                |
| en-US               | 英文               |
| es-ES               | 西班牙文               |
| fr-FR               | 法文                |
| it-IT               | 義大利文               |
| ja-JP               | 日文              |
| ko-KR               | 韓文                |
| pl-PL               | 波蘭文                |
| pt-BR               | 葡萄牙文 - 巴西   |
| ru-RU               | 俄文               |
| tr-TR               | 土耳其文               |
| zh-CN               | 中文 - 簡體  |
| zh-TW               | 中文 - 繁體 |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

- [建立 Visual Studio 的網路安裝](../install/create-a-network-installation-of-visual-studio.md)
- [更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)
- [安裝 Visual Studio 離線安裝所需的憑證](../install/install-certificates-for-visual-studio-offline.md)
- [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)
