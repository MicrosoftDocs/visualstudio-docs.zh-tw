---
title: 從命令列建立 ClickOnce 應用程式 |Microsoft Docs
description: 瞭解如何從命令列建立 Visual Studio 專案，讓您可以使用自動化程式重現組建。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 13b057f0a688c3a1ae855215ac226a4d31993ea1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895150"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>從命令列建置 ClickOnce 應用程式

在中 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ，您可以從命令列建立專案，即使它們是在整合式開發環境中建立 (IDE) 。 事實上，您可以 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 在僅安裝 .NET Framework 的另一部電腦上重建以建立的專案。 這可讓您使用自動化的程式（例如，在中央組建實驗室中），或使用超越建立專案本身範圍的先進腳本技術來重現組建。

## <a name="use-msbuild-to-reproduce-net-framework-clickonce-application-deployments"></a>使用 MSBuild 重現 .NET Framework ClickOnce 應用程式部署

 當您在命令列上叫用 msbuild/target： publish 時，它會告知 MSBuild 系統建立專案，並 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 在 [發行] 資料夾中建立應用程式。 這相當於在 IDE 中選取 [ **發行** ] 命令。

 此命令會執行 *msbuild.exe*，在 Visual Studio 命令提示字元環境中的路徑上。

 「目標」是 MSBuild 的指標，可處理此命令。 主要目標是 "build" 目標和 "publish" 目標。 組建目標相當於選取組建命令 (或在 IDE 中按 F5) 。 如果您只想要建立您的專案，您可以鍵入來達成 `msbuild` 。 此命令的運作方式是因為組建目標是所產生之所有專案的預設目標 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 。 這表示您不需要明確地指定組建目標。 因此，輸入 `msbuild` 的操作與輸入的作業相同 `msbuild /target:build` 。

 此 `/target:publish` 命令會告知 MSBuild 叫用發行目標。 發佈目標視組建目標而定。 這表示發行作業是組建作業的超集合。 例如，如果您對其中一個 Visual Basic 或 c # 原始程式檔進行了變更，則發行作業會自動重建對應的元件。

 如需 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用 Mage.exe 命令列工具來建立資訊清單以產生完整部署的詳細資訊 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ，請參閱 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>使用 MSBuild 建立和建立基本 ClickOnce 應用程式

### <a name="to-create-and-publish-a-clickonce-project"></a>建立和發佈 ClickOnce 專案

1. 開啟 Visual Studio 並建立新專案。

    選擇 [ **Windows 桌面應用程式** ] 專案範本，然後為專案命名 `CmdLineDemo` 。

1. 在 [ **組建** ] 功能表中，按一下 [ **發行** ] 命令。

    此步驟可確保專案已正確設定，以產生 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式部署。

    [發行精靈] 隨即出現。

1. 在 [發行] 嚮導中，按一下 **[完成]**。

    Visual Studio 會產生並顯示預設的網頁，稱為 *Publish.htm*。

1. 儲存您的專案，並記下儲存的資料夾位置。

   上述步驟會建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 第一次發行的專案。 現在您可以在 IDE 之外重現組建。

#### <a name="to-reproduce-the-build-from-the-command-line"></a>從命令列重現組建

1. 結束 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。

2. 在 Windows [ **開始** ] 功能表中，依序按一下 [ **所有程式**] 和 [ **Microsoft Visual Studio**]，然後 **Visual Studio Tools**，然後 **Visual Studio 命令提示** 字元]。 這應該會在目前使用者的根資料夾中開啟命令提示字元。

3. 在 **Visual Studio 命令提示** 字元中，將目前的目錄變更為您剛剛建立之專案的位置。 例如，輸入 `chdir My Documents\Visual Studio\Projects\CmdLineDemo`。

4. 若要移除「建立和發行專案」中產生的現有檔案 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ，請輸入 `rmdir /s publish` 。

    這個步驟是選擇性的，但它可確保新的檔案全都由命令列組建所產生。

5. 輸入 `msbuild /target:publish`。

   上述步驟會 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 在名為 **Publish** 之專案的子資料夾中，產生完整的應用程式部署。 *CmdLineDemo：應用程式* 是 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署資訊清單。 *CmdLineDemo_1* 的資料夾包含檔案 *CmdLineDemo.exe* 和 *CmdLineDemo.exe 指令* 清單（ [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單）。 *Setup.exe* 是啟動載入器，預設會設定為安裝 .NET Framework。 Dotnetfx.exe 資料夾包含 .NET Framework 的可轉散發套件。 這是您透過 Web 或透過 UNC 或 CD/DVD 部署應用程式所需的完整檔案集。

> [!NOTE]
> 例如，MSBuild 系統會使用 **PublishDir** 選項來指定輸出的位置 `msbuild /t:publish /p:PublishDir="<specific location>"` 。

::: moniker range=">=vs-2019"

## <a name="build-net-clickonce-applications-from-the-command-line"></a>從命令列建立 .NET ClickOnce 應用程式

從命令列建立 .NET ClickOnce 應用程式是類似的經驗，但您必須在 MSBuild 命令列上提供發行設定檔的額外屬性。 建立發行設定檔最簡單的方式是使用 Visual Studio。  如需詳細資訊，請參閱 [使用 ClickOnce 部署 .Net Windows 應用程式](quickstart-deploy-using-clickonce-folder.md) 。

一旦建立發行設定檔之後，您就可以在 msbuild 命令列上提供 .pubxml 檔案作為屬性。 例如：

```cmd
    msbuild /t:publish /p:PublishProfile=<pubxml file> /p:PublishDir="<specific location>"
```
::: moniker-end

## <a name="publish-properties"></a>發佈屬性

 當您在上述程式中發佈應用程式時，[發佈嚮導] 或 .NET Core 3.1 或更新版本專案的發行設定檔中，會將下列屬性插入至您的專案檔。 這些屬性會直接影響 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的產生方式。

 在 *CmdLineDemo 中 vbproj*  /  *CmdLineDemo .csproj*：

```xml
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>
<GenerateManifests>true</GenerateManifests>
<TargetZone>LocalIntranet</TargetZone>
<PublisherName>Microsoft</PublisherName>
<ProductName>CmdLineDemo</ProductName>
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>
<Install>true</Install>
<ApplicationVersion>1.0.0.*</ApplicationVersion>
<ApplicationRevision>1</ApplicationRevision>
<UpdateEnabled>true</UpdateEnabled>
<UpdateRequired>false</UpdateRequired>
<UpdateMode>Foreground</UpdateMode>
<UpdateInterval>7</UpdateInterval>
<UpdateIntervalUnits>Days</UpdateIntervalUnits>
<UpdateUrlEnabled>false</UpdateUrlEnabled>
<IsWebBootstrapper>true</IsWebBootstrapper>
<BootstrapperEnabled>true</BootstrapperEnabled>
```

 針對 .NET Framework 的專案，您可以在命令列覆寫任何這些屬性，而不需要改變專案檔本身。 例如，下列程式會在沒有啟動載入器的情況下建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式部署：

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
 ```

::: moniker range=">=vs-2019"
若為 .NET Core 3.1 或更新版本，則會在 .pubxml 檔案中提供這些設定專案。

 您可以 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 從 [**專案設計** 工具] 的 [**發行**]、[**安全性**] 和 [**簽署**] 屬性頁，來控制發行屬性。 以下是發行屬性的描述，以及如何在應用程式設計工具的各種屬性頁面上設定每個屬性的指示：

> [!NOTE]
> 針對 .NET Windows 桌面專案，現在可以在 [發佈嚮導] 中找到這些設定。
::: moniker-end

- `AssemblyOriginatorKeyFile` 決定用來簽署 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單的金鑰檔。 您也可以使用這個相同的金鑰，將強式名稱指派給您的元件。 這個屬性是在 [**專案設計** 工具] 的 [**簽署**] 頁面上設定。
::: moniker range=">=vs-2019"
針對 .NET windows 應用程式，此設定會保留在專案檔中
::: moniker-end

  下列屬性會在 [ **安全性** ] 頁面上設定：

- **啟用 ClickOnce 安全性設定** 可決定是否 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 要產生資訊清單。 最初建立專案時， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 資訊清單產生預設為關閉。 當您第一次發行時，嚮導會自動開啟此旗標。

- **>targetzone** 可決定要發出至 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單的信任層級。 可能的值為「網際網路」、「LocalIntranet」和「自訂」。 網際網路和 LocalIntranet 會將預設許可權集合發出到您的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單。 LocalIntranet 是預設值，基本上表示完全信任。 自訂指定只將基底應用程式指令 *清單* 檔案中明確指定的許可權發出至 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單。 *App.config* 檔案是僅包含信任資訊定義的部分資訊清單檔案。 它是隱藏的檔案，當您在 [ **安全性** ] 頁面上設定許可權時，會自動新增至您的專案。
-
::: moniker range=">=vs-2019"
> [!NOTE]
> 若為 .NET Core 3.1 或更新版本，則為 Windows 桌面專案，不支援這些安全性設定。
::: moniker-end

  下列是在 [ **發佈** ] 頁面上設定的屬性：

- `PublishUrl` 是要在 IDE 中發行應用程式的位置。 如果沒有指定或屬性，則會將它插入 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單 `InstallUrl` `UpdateUrl` 。

- `ApplicationVersion` 指定應用程式的版本 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 這是四位數的版本號碼。 如果最後一個數位為 "*"，則 `ApplicationRevision` 會取代在組建階段插入資訊清單中的值。

- `ApplicationRevision` 指定修訂。 這是每次在 IDE 中發行時遞增的整數。 請注意，它不會針對在命令列執行的組建自動遞增。

- `Install` 判斷應用程式是已安裝的應用程式或從 Web 執行的應用程式。

- `InstallUrl` (不會顯示) 是使用者安裝應用程式的位置。 如果有指定，此值會在已啟用屬性的情況下，將此值燒錄到 *setup.exe* 啟動載入器中 `IsWebBootstrapper` 。 如果未指定，也會將它插入應用程式資訊清單 `UpdateUrl` 。

- `SupportUrl` (未顯示) 是在已安裝應用程式的 [ **新增/移除程式** ] 對話方塊中連結的位置。

  以下是在 [ **應用程式更新** ] 對話方塊中設定的屬性，可從 [ **發佈** ] 頁面存取。

- `UpdateEnabled` 指出應用程式是否應該檢查更新。

- `UpdateMode` 指定前景更新或背景更新。
::: moniker range=">=vs-2019"
   若為 .NET Core 3.1 或更新版本，則不支援專案、背景。  
::: moniker-end
- `UpdateInterval` 指定應用程式檢查更新的頻率。
::: moniker range=">=vs-2019"
   若為 .NET Core 3.1 或更新版本，則不支援此設定。
::: moniker-end

- `UpdateIntervalUnits` 指定 `UpdateInterval` 值是以小時、天或周為單位。
::: moniker range=">=vs-2019"
   若為 .NET Core 3.1 或更新版本，則不支援此設定。
::: moniker-end

- `UpdateUrl` (未顯示) 是應用程式將接收更新的位置。 如果有指定，此值會插入應用程式資訊清單中。

  下列屬性是在 [ **發行選項** ] 對話方塊中設定的，可從 [ **發行** ] 頁面存取。

- `PublisherName` 指定安裝或執行應用程式時，顯示在提示字元中的發行者名稱。 如果是已安裝的應用程式，它也會用來指定 [ **開始** ] 功能表上的資料夾名稱。

- `ProductName` 指定安裝或執行應用程式時，顯示在提示字元中的產品名稱。 如果是已安裝的應用程式，它也會用來指定 [ **開始** ] 功能表上的快捷方式名稱。

  以下是在 [ **必要條件** ] 對話方塊中設定的屬性，可從 [ **發佈** ] 頁面存取。

- `BootstrapperEnabled` 決定是否要產生 *setup.exe* 啟動載入器。

- `IsWebBootstrapper` 判斷 *setup.exe* 啟動載入器是否可在 Web 或以磁片為基礎的模式下運作。

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL、SupportUrl、PublishURL 和 UpdateURL

 下表顯示 ClickOnce 部署的四個 URL 選項。

|URL 選項|Description|
|----------------|-----------------|
|`PublishURL`|如果您要將 ClickOnce 應用程式發佈至網站，則為必要。|
|`InstallURL`|選擇性。 如果安裝網站與不同，請設定此 URL 選項 `PublishURL` 。 例如，您可以將設定 `PublishURL` 為 FTP 路徑，並將設定 `InstallURL` 為 Web URL。|
|`SupportURL`|選擇性。 如果支援網站與不同，請設定此 URL 選項 `PublishURL` 。 例如，您可以將設定 `SupportURL` 為公司的客戶支援網站。|
|`UpdateURL`|選擇性。 如果更新位置與不同，請設定此 URL 選項 `InstallURL` 。 例如，您可以將設定 `PublishURL` 為 FTP 路徑，並將設定 `UpdateURL` 為 Web URL。|

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
