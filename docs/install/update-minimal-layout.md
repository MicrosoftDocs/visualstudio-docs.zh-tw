---
title: 使用最小離線版面配置來更新 Visual Studio
description: 瞭解如何使用基本的離線版面配置來更新 Visual Studio。
ms.date: 07/21/2020
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 27a9c0de35bb6f9944015391c5f933bef28f4b9d
ms.sourcegitcommit: 645303f47a5258d4b65cc56bf9e2303865587e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2021
ms.locfileid: "99533561"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>使用最小離線版面配置來更新 Visual Studio

針對未連線到網際網路的電腦，建立最基本的版面配置是更新離線 Visual Studio 實例的最簡單且最快速的方式。

最基本的版面組態工具會產生專為您小組的需求量身打造的版面配置。 企業系統管理員可以使用此工具，為 Visual Studio 2017 和2019的大部分版本建立更新配置 (s) 。 不同于完整的 Visual Studio 配置，最小的版面配置只會包含更新的套件，因此它一律會以較小且更快速的方式產生和部署。 您可以只指定所需的語言、工作負載和元件，進一步將更新配置的大小降到最低。

## <a name="how-to-generate-a-minimal-layout"></a>如何產生基本版面配置

> [!IMPORTANT]
> 這些指示假設您先前已建立並使用版面配置。 如需如何進行的詳細資訊，請參閱 [更新 Visual Studio 頁面的網路型安裝](update-a-network-installation-of-visual-studio.md) 。
>
> 若要進一步瞭解 Visual Studio 生命週期，請參閱 [Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing) 頁面。
>

此工具會建立 Visual Studio 2017 (15.9) 和更新版本的更新版面配置。 版面配置可以部署到網路/離線電腦，以更新 Visual Studio 實例。 在 [一般配置建立](update-a-network-installation-of-visual-studio.md)期間，會下載該特定版本的所有套件。 在 Visual Studio 實例上進行修復、卸載和其他標準作業時，需要建立標準版面配置。 最小版面配置只會下載更新的套件，因此較小且更容易複製到離線電腦。

### <a name="installing-the-minimal-layout-tool"></a>安裝最基本的版面組態工具
 
 1. 首先，請下載最基本的版面組態工具，位於 [此處](https://aka.ms/vs/installer/minimallayout)。 請務必在出現提示時選擇 [ **儲存** ]，然後選取 [ **執行**]。

     ![儲存基本的版面組態工具](media/save-minimal-layout.png)

 2. 接下來，按一下 [ **是]** 接受 [使用者帳戶控制] 提示。

     ![接受使用者帳戶控制](media/accept-user-account-control.png)

 3. 最基本的版面組態工具將會安裝至 `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` 。

### <a name="how-to-use-the-minimal-layout-tool"></a>如何使用最基本的版面組態工具

`MinimalLayout.exe` 使用下列命令和選項來產生版面配置。 至少需要一個命令才能執行工具。 以下是您將執行此工具的方式：

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>命令
* **預覽**：使用此命令可預覽要下載的套件數目，以及用來建立此配置的總空間。 
* **產生**：使用此命令來產生更新 Visual Studio 的最基本版面配置。
* **重新** 產生：使用此命令可使用現有的基本版面配置回應檔來重新產生配置。 每個最基本的版面配置都會產生一個 `MinimalLayout.json` 回應檔案，其中包含原始的最基本版面配置輸入參數。 您可以使用 [ **重新** 產生] 命令和 `MinimalLayout.json` 回應檔來重新產生最基本的版面配置。 如果您想要根據先前最基本的版面配置回應檔，建立新 Visual Studio 更新的最基本配置，這會很有用。

   此命令 `MinimalLayout.json` 需要已產生之配置的檔案路徑。 

    ```cmd
    MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
    ```

* **確認**：使用此命令來判斷版面配置資料夾是否已損毀。
* **修正**：使用此命令來修正損毀的版面配置資料夾，包括從版面配置資料夾取代任何遺漏的封裝。

#### <a name="options"></a>選項 

|選項。    |描述    |必要/選用 |範例 |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |指定要在其中建立基本離線版面配置的目錄。       |必要        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt; 版本&gt;|從這個版本開始，將會產生最基本的離線版面配置。   |必要|--baseVersion 16.4.0 版 |
|--targetVersion &lt; 版本&gt;|將會產生最基本的離線配置，包括此版本。|必要|--targetVersion 16.4.4 版|
|--語言    |指定要包含在最基本離線配置中的語言。 您可以指定多個值，並以空格分隔。    |必要    |--語言 en-us fr-fr |
|--productId &lt; 識別碼&gt;    |將從中產生最基本離線配置之產品的識別碼。 <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|必要|--productId VisualStudio Enterprise |
|--filePath    |從已建立的版面配置，檔案 MinimalLayout.js檔案路徑。 此選項只適用于重新產生命令。     |重新產生命令的必要參數    |--filePath C:\VSLayout\minimalLayout.js開啟 <br><br> **請注意，[重新產生] 命令只會採用--filePath 作為選項。** |
|--新增 &lt; 一或多個工作負載或元件識別碼&gt;    |指定要新增的一或多個工作負載或元件識別碼。 您可以使用--includeRecommended 和/或，全域新增其他元件 <br> –-includeOptional。 您可以指定多個工作負載或元件識別碼，並以空格分隔。    |選擇性    |--新增 VisualStudio ManagedDesktop VisualStudio. NetWeb 元件。元件。 VisualStudio |
|--includeRecommended    |包含所安裝任何工作負載的建議元件，但不包含選擇性元件。    |選擇性    |針對特定工作負載： <br> --新增 VisualStudio 工作負載。 ManagedDesktop; includeRecommended <br><br> 適用于所有工作負載：--includeRecommended |
|--includeOptional |針對任何已安裝的工作負載（包括建議的元件），包含選用的元件。    |選擇性    |針對特定工作負載： <br>--新增 VisualStudio 工作負載。 ManagedDesktop; includeOptional <br><br> 適用于所有工作負載：--includeOptional |

### <a name="generating-a-minimal-layout"></a>產生基本版面配置

> [!IMPORTANT]
>  這些指示假設您先前已建立網路安裝版面配置。 如需如何進行這項操作的詳細資訊，請參閱 [建立 Visual Studio 的網路安裝](create-a-network-installation-of-visual-studio.md) 頁面。

使用指定版本範圍的 [ **產生** ] 命令建立最基本的版面配置。 您也需要瞭解 productId、語言和任何需要的特定工作負載。 這種最基本的版面配置會將基底版本的任何 Visual Studio 實例更新為目標版本，並包含目標版本。

建立版面配置之前，您可以找出下載的總大小，以及使用 [ **預覽** ] 命令所包含的套件數目。 此命令會使用與 [ **產生** ] 命令相同的選項，並將詳細資料寫入主控台。

讓我們逐步解說一些範例，說明如何預覽、產生和重新產生最基本的版面配置：

::: moniker range="vs-2019"

- 首先，我們將示範如何預覽16.4.0 版至僅16.4.4 版英文版的 Visual Studio Enterprise 版本版面配置。

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- 以下說明如何使用一個工作負載來產生相同的版面配置。

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- 以下說明如何使用現有的回應檔重新產生最基本的離線配置。 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

使用 [ **產生** ] 命令的其他幾個範例：

- 以下說明如何新增額外的工作負載，並只包含建議的封裝。 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- 最後，以下是您在最基本的版面配置中包含多種語言的方式。 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

::: moniker range="vs-2017"

- 首先，我們將示範如何預覽15.0.0 版至僅15.9.31 英文版的 Visual Studio Enterprise 版本版面配置。

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
    ```

- 以下說明如何使用一個工作負載來產生相同的版面配置。

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- 以下說明如何使用現有的回應檔重新產生最基本的離線配置。 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

使用 [ **產生** ] 命令的其他幾個範例：

- 以下說明如何新增額外的工作負載，並只包含建議的封裝。 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- 最後，以下是您在最基本的版面配置中包含多種語言的方式。 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>如何維持基本的版面配置

在建立之後，請使用 [ **驗證** ] 和 [ **修正** ] 命令來維持最基本的版面配置。 **Verify** 命令可判斷最基本配置中是否有任何損毀或遺漏的套件。 如果您在執行 [ **驗證** ] 命令之後遇到任何問題，請使用 [ **修正** ] 命令來更正遺失或損毀的封裝。

- 以下是如何驗證配置是否損毀或遺失套件： 

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- 以下是修正該配置的方法：

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE] 
> 此配置不能用來修復 Visual Studio 安裝。 若要修復 Visual Studio 的現有實例，請參閱 [修復 Visual Studio](repair-visual-studio.md)。
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>如何使用基本的離線配置來更新現有的 Visual Studio 安裝

產生最基本的版面配置之後，您可以將整個最基本的版面配置資料夾複製到用戶端電腦。 如果電腦無法存取其原始位置中最基本的版面配置資料夾，則這是必要的。

流覽至資料夾，並找出啟動載入器應用程式名稱。 啟動載入器應用程式的名稱，取決於產生最基本版面配置時指定的 ProductId 值。 請參閱下表中的常見範例。

|ProductId 值    |應用程式名稱|
|:-----------|:------------|
|Microsoft.VisualStudio.Product.Enterprise    |vs_enterprise.exe|
|Microsoft.VisualStudio.Product.Professional    |vs_professional.exe|
|Microsoft.VisualStudio.Product.BuildTools    |vs_buildtools.exe|

更新會以兩個步驟套用至 Visual Studio 實例。 從更新 Visual Studio 安裝程式開始，然後更新 Visual Studio。

1. **更新 Visual Studio 安裝程式** 

    如有必要，請執行下列命令， `vs_enterprise.exe`  並以正確的啟動載入器應用程式名稱取代。 

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **更新 Visual Studio 應用程式**

    若要更新 Visual Studio，您必須指定要更新 Visual Studio 實例的 installPath。 如果安裝了多個 Visual Studio 實例，每一個實例都需要個別更新。 強烈建議您以 `–noWeb` update 命令指定選項，以防止安裝不是最基本配置的元件。 這可防止您離開 Visual Studio 處於無法使用的狀態。

    執行下列命令，適當地替代 installPath 命令列參數。 也請務必使用正確的啟動載入器應用程式名稱。

    ```cmd
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [用於偵測及管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
* [如何在回應檔中定義設定](automated-installation-with-response-file.md)
* [控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing/)
