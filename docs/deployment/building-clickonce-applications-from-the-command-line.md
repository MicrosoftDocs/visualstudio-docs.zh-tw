---
title: 從命令列建立 ClickOnce 應用程式 |Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d8ce0753c63f1dcc177f36149cad9789ec150ab
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787682"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>從命令列建置 ClickOnce 應用程式
在[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]中, 您可以從命令列建立專案, 即使它們是在整合式開發環境 (IDE) 中所建立。 事實上, 您可以在只安裝 .NET Framework 的另[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]一部電腦上重建以建立的專案。 這可讓您使用自動化程式來重現組建, 例如, 在中央組建實驗室中, 或使用超出組建專案本身範圍的先進腳本技術。

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>使用 MSBuild 重現 ClickOnce 應用程式部署
 當您在命令列中叫用 msbuild/target: publish 時, 它會告知 msbuild 系統建立專案, 並在[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publish 資料夾中建立應用程式。 這相當於選取 IDE 中的 [**發行**] 命令。

 此命令會執行*msbuild.exe*, 其位於 Visual Studio 命令提示字元環境中的路徑上。

 「目標」是 MSBuild 的指標, 用來處理命令。 金鑰目標是「組建」目標和「發行」目標。 組建目標等同于在 IDE 中選取 [組建] 命令 (或按 F5)。 如果您只想要建立專案, 可以輸入`msbuild`來達到這個目的。 此命令可運作, 因為組建目標是所產生[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]之所有專案的預設目標。 這表示您不需要明確指定組建目標。 因此, 鍵入`msbuild`的作業與輸入`msbuild /target:build`的作業相同。

 `/target:publish`命令會告訴 MSBuild 叫用發行目標。 發行目標取決於組建目標。 這表示發佈作業是組建作業的超集合。 例如, 如果您對其中一個 Visual Basic 或C#原始程式檔進行變更, 則發行作業會自動重建對應的元件。

 如需使用 mage.exe 命令列[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]工具產生完整部署以[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]建立資訊清單的詳細資訊, 請參閱[逐步解說:手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>使用 MSBuild 建立並建立基本 ClickOnce 應用程式

#### <a name="to-create-and-publish-a-clickonce-project"></a>建立和發行 ClickOnce 專案

1. 開啟 Visual Studio 並建立新專案。

    選擇 [ **Windows 桌面應用程式**] 專案範本, 並`CmdLineDemo`將專案命名為。

1. 從 [**建立**] 功能表中, 按一下 [**發行**] 命令。

    此步驟可確保專案已正確設定, 以產生[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式部署。

    [發行精靈] 隨即出現。

1. 在 [發行嚮導] 中, 按一下 **[完成]** 。

    Visual Studio 會產生並顯示預設的網頁, 稱為*Publish*。

1. 儲存您的專案, 並記下存放它的資料夾位置。

   上述步驟會建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]第一次發行的專案。 現在您可以在 IDE 外部重現組建。

#### <a name="to-reproduce-the-build-from-the-command-line"></a>從命令列重現組建

1. 結束 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。

2. 從 Windows **開始** 功能表, 依序按一下 **所有程式**、 **Microsoft Visual Studio**、 **Visual Studio Tools**, 然後**Visual Studio 命令提示**字元。 這應該會在目前使用者的根資料夾中開啟命令提示字元。

3. 在**Visual Studio 命令提示**字元中, 將目前的目錄變更為您剛才建立之專案的位置。 例如，輸入 `chdir My Documents\Visual Studio\Projects\CmdLineDemo`。

4. 若要移除「建立和發行[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]專案」中產生的現有檔案, 請輸入。 `rmdir /s publish`

    此步驟是選擇性的, 但它會確保新檔案全部都是由命令列組建所產生。

5. 輸入 `msbuild /target:publish`。

   上述步驟會在您專案的[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]子資料夾中, 產生名為**Publish**的完整應用程式部署。 *CmdLineDemo*是[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單。 資料夾*cmdlinedemo_ 1.0.0.0*包含*CmdLineDemo*和*CmdLineDemo*檔案, 也就是[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 Setup.exe 是啟動載入器, 預設會設定為安裝 .NET Framework。 Dotnetfx.exe 資料夾包含 .NET Framework 的可轉散發套件。 這是您透過 Web 或透過 UNC 或 CD/DVD 部署應用程式所需的整組檔案。
   
> [!NOTE]
> MSBuild 系統會使用**PublishDir**選項來指定輸出的位置, `msbuild /t:publish /p:PublishDir="<specific location>"`例如。

## <a name="publish-properties"></a>發佈屬性
 當您在上述程式中發行應用程式時, [發行嚮導] 會將下列屬性插入您的專案檔中。 這些屬性會直接影回應用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]程式的產生方式。

 在*CmdLineDemo 中 vbproj*  /  *CmdLineDemo .csproj*:

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

 您可以在命令列覆寫這些屬性中的任何一個, 而不需要改變專案檔案本身。 例如, 下列程式會建立不含[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]啟動載入器的應用程式部署:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 發行屬性是在 [ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **專案設計**工具] 的 [**發行**]、[**安全性**] 和 [**簽署**] 屬性頁中進行控制。 以下是發佈屬性的描述, 以及如何在應用程式設計工具的各種屬性頁中設定每個屬性的指示:

- `AssemblyOriginatorKeyFile`決定用來簽署[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單的金鑰檔。 您也可以使用這個相同的金鑰, 將強式名稱指派給您的元件。 這個屬性是在 [**專案設計**工具] 的 [**簽署**] 頁面上設定。

  下列屬性是在 [**安全性**] 頁面上設定:

- [**啟用 ClickOnce 安全性設定**] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]可決定是否要產生資訊清單。 最初建立專案時, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]資訊清單產生預設為關閉。 當您第一次發行時, 嚮導會自動開啟此旗標。

- **TargetZone**會決定要在[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單中發出的信任層級。 可能的值為 "Internet"、"LocalIntranet" 和 "Custom"。 Internet 和 LocalIntranet 會導致將預設許可權集合發出到您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]的應用程式資訊清單。 LocalIntranet 是預設值, 基本上表示完全信任。 Custom 指定只會將基底*應用* [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]程式資訊清單檔案中明確指定的許可權發出至應用程式資訊清單。 *App.config*檔案是只包含信任資訊定義的部分資訊清單檔案。 這是隱藏的檔案, 當您在 [**安全性**] 頁面上設定許可權時, 會自動新增至您的專案。

  下列屬性是在 [**發行**] 頁面上設定:

- `PublishUrl`是應用程式將在 IDE 中發行至的位置。 如果[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 沒有指定`UpdateUrl`或屬性, 則會將它插入應用程式資訊清單中。 `InstallUrl`

- `ApplicationVersion`指定[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式的版本。 這是四位數的版本號碼。 如果最後一個數位是 "*", `ApplicationRevision`則會取代在組建階段插入資訊清單中的值。

- `ApplicationRevision`指定修訂。 這是一個整數, 每次您在 IDE 中發行時都會遞增。 請注意, 在命令列執行的組建不會自動遞增。

- `Install`判斷應用程式是已安裝的應用程式, 還是從 Web 執行的應用程式。

- `InstallUrl`(未顯示) 是使用者將從中安裝應用程式的位置。 如果已指定, 此值會在啟用 `IsWebBootstrapper`屬性時, 燒錄到 setup.exe 啟動載入器中。 如果`UpdateUrl`未指定, 它也會插入應用程式資訊清單中。

- `SupportUrl`(未顯示) 是已安裝應用程式的 [**新增/移除程式**] 對話方塊中所連結的位置。

  下列屬性設定于 [**應用程式更新**] 對話方塊中, 從 [**發行**] 頁面存取。

- `UpdateEnabled`指出應用程式是否應該檢查更新。

- `UpdateMode`指定前景更新或背景更新。

- `UpdateInterval`指定應用程式檢查更新的頻率。

- `UpdateIntervalUnits``UpdateInterval`指定值是以小時、天或周為單位。

- `UpdateUrl`(未顯示) 是應用程式將接收更新的位置。 若已指定, 則會將此值插入應用程式資訊清單中。

- 下列屬性是在 [**發行選項**] 對話方塊中設定的, 從 [**發行**] 頁面存取。

- `PublisherName`指定安裝或執行應用程式時, 顯示在提示中的發行者名稱。 如果是已安裝的應用程式, 它也會用來指定 [**開始**] 功能表上的資料夾名稱。

- `ProductName`指定安裝或執行應用程式時, 顯示在提示中的產品名稱。 如果是已安裝的應用程式, 它也會用來指定 [**開始**] 功能表上的快捷方式名稱。

- 下列屬性設定于 [**必要條件**] 對話方塊中, 從 [**發行**] 頁面存取。

- `BootstrapperEnabled`判斷是否要產生*setup.exe*啟動載入器。

- `IsWebBootstrapper`判斷*setup.exe*啟動載入器是否可透過 Web 或以磁片為基礎的模式運作。

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL、SupportUrl、PublishURL 和 UpdateURL
 下表顯示 ClickOnce 部署的四個 URL 選項。

|URL 選項|說明|
|----------------|-----------------|
|`PublishURL`|如果您要將 ClickOnce 應用程式發行至網站, 則為必要。|
|`InstallURL`|選擇性。 如果安裝網站與不同`PublishURL`, 請設定此 URL 選項。 例如, 您可以將設定`PublishURL`為 FTP 路徑, 並`InstallURL`將設定為 Web URL。|
|`SupportURL`|選擇性。 如果支援網站與不同`PublishURL`, 請設定此 URL 選項。 例如, 您可以將設定`SupportURL`為貴公司的客戶支援網站。|
|`UpdateURL`|選擇性。 如果更新位置與不同`InstallURL`, 請設定此 URL 選項。 例如, 您可以將設定`PublishURL`為 FTP 路徑, 並`UpdateURL`將設定為 Web URL。|

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
