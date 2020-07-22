---
title: 使用最少的離線版面配置來更新 Visual Studio
description: 瞭解如何使用最少的離線版面配置來更新 Visual Studio。
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
ms.openlocfilehash: 849cad46463ffb52e2f4f2a930f05daf66f7d737
ms.sourcegitcommit: 363f3e6e30dd54366ade0d08920755da5951535c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86869879"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>使用最少的離線版面配置來更新 Visual Studio

對於未連線到網際網路的電腦，建立最基本的配置是更新離線 Visual Studio 實例的最簡單且最快速的方式。

「最小配置」工具會產生專為您小組的需求量身打造的版面配置。 企業系統管理員可以使用此工具，針對 Visual Studio 2017 和2019的大部分版本建立更新版面配置。 不同于完整的 Visual Studio 版面配置，最小的配置只包含更新的封裝，因此產生和部署的速度一律較小且更快速。 您可以只指定所需的語言、工作負載和元件，以進一步將更新配置的大小降至最低。

## <a name="how-to-generate-a-minimal-layout"></a>如何產生最小版面配置

> [!IMPORTANT]
> 這些指示假設您先前已建立並使用版面配置。 如需有關如何執行這項操作的詳細資訊，請參閱[更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)頁面。
>
> 若要進一步瞭解 Visual Studio 生命週期，請參閱[Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing)頁面。
>

此工具會建立 Visual Studio 2017 （15.9）和更新版本的更新配置。 版面配置可以部署到網路/離線電腦，以更新 Visual Studio 實例。 [建立一般版面](update-a-network-installation-of-visual-studio.md)配置時，會下載該特定版本的所有套件。 在 Visual Studio 實例上進行修復、卸載及其他標準作業時，需要建立一般配置。 最小版面配置只會下載更新的套件，因此較小且更容易複製到離線電腦。

### <a name="installing-the-minimal-layout-tool"></a>安裝最基本的版面組態工具
 
 1. 首先，下載最基本的版面組態工具，位於[此處](https://aka.ms/vs/installer/minimallayout)。 請務必在出現提示時選擇 [**儲存**]，然後選取 [**執行**]。

     ![儲存最基本的版面組態工具](media/save-minimal-layout.png)

 2. 接下來，按一下 **[是]** 接受 [使用者帳戶控制] 提示。

     ![接受使用者帳戶控制](media/accept-user-account-control.png)

 3. 最基本的版面組態工具將安裝到 `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` 。

### <a name="how-to-use-the-minimal-layout-tool"></a>如何使用最小版面組態工具

`MinimalLayout.exe`會使用下列命令和選項來產生版面配置。 至少需要一個命令，才能執行此工具。 以下是執行此工具的方式：

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>命令
* **預覽**：使用此命令可預覽要下載的套件數目，以及用來建立此版面配置的總空間。 
* **產生**：使用此命令來產生更新 Visual Studio 的最小版面配置。
* **重新**產生：使用此命令來重新產生使用現有最小版面配置回應檔案的配置。 每個最小版面配置都會產生 `MinimalLayout.json` 回應檔，其中包含原始的最小版面配置輸入參數。 您可以使用**重新**產生命令和 `MinimalLayout.json` 回應檔來重新產生最小版面配置。 如果您想要根據前一個最小版面配置的回應檔案來建立新 Visual Studio 更新的最小配置，這會很有用。 
   - 針對此命令， `MinimalLayout.json` 需要來自已產生配置的檔案路徑。 

        ```cmd
        MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
        ```

* **Verify**：使用此命令來判斷版面配置資料夾是否已損毀。
* **修正**：使用此命令修正損毀的版面配置資料夾，包括從版面配置資料夾取代任何遺漏的封裝。

#### <a name="options"></a>選項 

|選項。    |描述    |必要/選用 |範例 |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |指定要在其中建立最小離線版面配置的目錄。       |必要        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt; 版本&gt;|從這個版本開始，將會產生最小的離線版面配置。   |必要|--baseVersion 16.4.0 |
|--targetVersion &lt; 版本&gt;|最短的離線版面配置將會產生，並包含此版本。|必要|--targetVersion 16.4。4|
|--語言    |指定要包含在最低離線版面配置中的語言。 可以指定多個值，並以空格分隔。    |必要    |--語言 en-us fr-FR |
|--productId &lt; 識別碼&gt;    |將產生最小離線版面配置的產品識別碼。 <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|必要|--productId VisualStudio. Product. Enterprise |
|--filePath    |從已建立的版面配置，在檔案上 MinimalLayout.js檔案的檔案路徑。 此選項只會與重新產生命令搭配使用。     |重新產生命令所需    |--filePath C:\VSLayout\minimalLayout.js開啟 <br><br> **請注意，重新產生命令只接受--filePath 做為選項。** |
|--新增 &lt; 一或多個工作負載或元件識別碼&gt;    |指定一或多個要新增的工作負載或元件識別碼。 您可以使用--includeRecommended 和/或，全域新增其他元件 <br> --includeOptional。 可以指定多個工作負載或元件識別碼，並以空格分隔。    |選擇性    |--新增 VisualStudio ManagedDesktop VisualStudio. NetWeb 元件. GitHub. VisualStudio |
|--includeRecommended    |包含所安裝任何工作負載的建議元件，但不包含選擇性元件。    |選擇性    |針對特定的工作負載： <br> --新增 VisualStudio 工作負載。 ManagedDesktop; includeRecommended <br><br> 適用于所有工作負載：--includeRecommended |
|--includeOptional |包含已安裝之任何工作負載的選擇性元件，包括建議的元件。    |選擇性    |針對特定的工作負載： <br>--新增 VisualStudio 工作負載。 ManagedDesktop; includeOptional <br><br> 適用于所有工作負載：--includeOptional |

### <a name="generating-a-minimal-layout"></a>產生最小版面配置

> [!IMPORTANT]
>  這些指示假設您先前已建立網路安裝版面配置。 如需有關如何執行這項操作的詳細資訊，請參閱[建立 Visual Studio 的網路安裝](create-a-network-installation-of-visual-studio.md)頁面。

針對您指定的版本範圍，使用 [**產生**] 命令建立最小版面配置。 您也需要知道 productId、語言，以及任何需要的特定工作負載。 此最小版面配置會將任何 Visual Studio 實例從基底版本更新至目標版本，並將其包含在內。

建立版面配置之前，您可以使用 [**預覽**] 命令找出下載的大小總計，以及所包含的套件數目。 此命令會採用與**產生**命令相同的選項，而且詳細資料會寫入主控台。

讓我們逐步解說一些範例，說明如何預覽、產生和重新產生最小版面配置：

- 首先，以下範例示範如何預覽僅限英文版16.4.0 的 Visual Studio Enterprise 版本的版面配置。

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- 以下說明如何使用一個工作負載產生相同的版面配置。

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- 以下說明如何使用現有的回應檔重新產生最小的離線版面配置。 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

使用 [**產生**] 命令的一些其他範例：

- 以下說明如何新增額外的工作負載，並只包含建議的套件。 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- 最後，以下是您在最小版面配置中包含多種語言的方式。 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

### <a name="how-to-maintain-a-minimal-layout"></a>如何保持最小版面配置

使用 [**驗證**] 和 [**修正**] 命令，以在建立後維持最小的版面配置。 **Verify**命令會判斷最小版面配置中是否有任何損毀或遺失的套件。 如果您在執行 [**驗證**] 命令之後遇到任何問題，請使用 [**修正**] 命令來更正遺失或損毀的封裝。

- 以下是驗證配置是否已損毀或遺失套件的方法： 

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- 以下是修正該版面配置的方法：

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE] 
> 此配置不能用來修復 Visual Studio 安裝。 若要修復 Visual Studio 的現有實例，請參閱[repair Visual Studio](repair-visual-studio.md)。
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>如何使用最少的離線版面配置來更新現有的 Visual Studio 安裝

產生最小版面配置之後，您可以將整個最小版面配置資料夾複製到用戶端電腦。 如果電腦無法存取其原始位置中的最小版面配置資料夾，這就是必要的。

流覽至資料夾，並識別啟動載入器應用程式名稱。 啟動載入器應用程式的名稱，取決於產生最小版面配置時所指定的 ProductId 值。 如需常見的範例，請參閱下表。

|ProductId 值    |應用程式名稱|
|:-----------|:------------|
|Microsoft.VisualStudio.Product.Enterprise    |vs_enterprise.exe|
|Microsoft.VisualStudio.Product.Professional    |vs_professional.exe|
|Microsoft.VisualStudio.Product.BuildTools    |vs_buildtools.exe|

更新會以兩個步驟套用至 Visual Studio 實例。 一開始請先更新 Visual Studio 安裝程式，然後更新 Visual Studio。

1. **更新 Visual Studio 安裝程式** 

    執行下列命令， `vs_enterprise.exe` 並在必要時以正確的啟動載入器應用程式名稱取代。 

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **更新 Visual Studio 應用程式**

    若要更新 Visual Studio，您需要指定您想要更新之 Visual Studio 實例的 installPath。 如果已安裝 Visual Studio 的多個實例，則每個實例都需要個別更新。 我們強烈建議您 `–noWeb` 使用 update 命令來指定選項，以防止安裝不在最小版面配置中的元件。 這可防止您讓 Visual Studio 處於無法使用的狀態。

    執行下列命令，並適當地替代 installPath 命令列參數。 也請務必使用正確的啟動載入器應用程式名稱。

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
