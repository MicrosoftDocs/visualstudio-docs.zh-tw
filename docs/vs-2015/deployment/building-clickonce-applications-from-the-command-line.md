---
title: 從命令列建立 ClickOnce 應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2625a8d4caa7dd53e9ce86395a98622f91d686b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155709"
---
# <a name="building-clickonce-applications-from-the-command-line"></a>從命令列建置 ClickOnce 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在中 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ，您可以從命令列建立專案，即使它們是在整合式開發環境中建立 (IDE) 。 事實上，您可以 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 在只安裝了的另一部電腦上重建以建立的專案 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。 這可讓您使用自動化的程式（例如，在中央組建實驗室中），或使用超越建立專案本身範圍的先進腳本技術來重現組建。  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>使用 MSBuild 重現 ClickOnce 應用程式部署  
 當您在命令列上叫用 msbuild/target： publish 時，它會告知 MSBuild 系統建立專案，並 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 在 [發行] 資料夾中建立應用程式。 這相當於在 IDE 中選取 [ **發行** ] 命令。  
  
 此命令會執行 msbuild.exe，在 Visual Studio 命令提示字元環境中的路徑上。  
  
 「目標」是 MSBuild 的指標，可處理此命令。 主要目標是 "build" 目標和 "publish" 目標。 組建目標相當於選取組建命令 (或在 IDE 中按 F5) 。 如果您只想要建立您的專案，您可以鍵入來達成 `msbuild` 。 此命令的運作方式是因為組建目標是所產生之所有專案的預設目標 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 。 這表示您不需要明確地指定組建目標。 因此，輸入 `msbuild` 的操作與輸入的作業相同 `msbuild /target:build` 。  
  
 此 `/target:publish` 命令會告知 MSBuild 叫用發行目標。 發佈目標視組建目標而定。 這表示發行作業是組建作業的超集合。 例如，如果您對其中一個 Visual Basic 或 c # 原始程式檔進行了變更，則發行作業會自動重建對應的元件。  
  
 如需 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 使用 Mage.exe 命令列工具來建立資訊清單以產生完整部署的詳細資訊 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ，請參閱 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>使用 MSBuild 建立和建立基本 ClickOnce 應用程式  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>建立和發佈 ClickOnce 專案  
  
1. 按一下 [檔案] 功能表**中的**[**新增專案**]。 [新增專案]  對話方塊隨即出現。  
  
2. 選取 [ **Windows 應用程式** ]，並為其命名 `CmdLineDemo` 。  
  
3. 在 [ **組建** ] 功能表中，按一下 [ **發行** ] 命令。  
  
    此步驟可確保專案已正確設定，以產生 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式部署。  
  
    [發行精靈] 隨即出現。  
  
4. 在 [發行] 嚮導中，按一下 **[完成]**。  
  
    Visual Studio 會產生並顯示預設的網頁，稱為 Publish.htm。  
  
5. 儲存您的專案，並記下儲存的資料夾位置。  
  
   上述步驟會建立 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 第一次發行的專案。 現在您可以在 IDE 之外重現組建。  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>從命令列重現組建  
  
1. 結束 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]。  
  
2. 在 Windows [ **開始** ] 功能表中，依序按一下 [ **所有程式**] 和 [ **Microsoft Visual Studio**]，然後 **Visual Studio Tools**，然後 **Visual Studio 命令提示**字元]。 這應該會在目前使用者的根資料夾中開啟命令提示字元。  
  
3. 在 **Visual Studio 命令提示**字元中，將目前的目錄變更為您剛剛建立之專案的位置。 例如，輸入 `chdir My Documents\Visual Studio\Projects\CmdLineDemo`。  
  
4. 若要移除「建立和發行專案」中產生的現有檔案 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ，請輸入 `rmdir /s publish` 。  
  
    這個步驟是選擇性的，但它可確保新的檔案全都由命令列組建所產生。  
  
5. 輸入 `msbuild /target:publish`。  
  
   上述步驟會 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 在名為 **Publish**之專案的子資料夾中，產生完整的應用程式部署。 CmdLineDemo：應用程式是 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署資訊清單。 CmdLineDemo_1 的資料夾包含檔案 CmdLineDemo.exe 和 CmdLineDemo.exe 資訊清單（ [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式資訊清單）。 Setup.exe 是啟動載入器，預設會設定為安裝 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。 Dotnetfx.exe 資料夾包含的可轉散發套件 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。 這是您透過 Web 或透過 UNC 或 CD/DVD 部署應用程式所需的完整檔案集。  
  
## <a name="publishing-properties"></a>發佈屬性  
 當您在上述程式中發佈應用程式時，[發行] 嚮導會將下列屬性插入至您的專案檔。 這些屬性會直接影響 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式的產生方式。  
  
 在 CmdLineDemo. vbproj/CmdLineDemo .csproj 中：  
  
```  
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
  
 您可以在命令列覆寫任何這些屬性，而不需要改變專案檔本身。 例如，下列程式會在沒有啟動載入器的情況下建立 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式部署：  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 您可以 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 從 [**專案設計**工具] 的 [**發行**]、[**安全性**] 和 [**簽署**] 屬性頁，來控制發行屬性。 以下是發行屬性的描述，以及如何在應用程式設計工具的各種屬性頁面上設定每個屬性的指示：  
  
- `AssemblyOriginatorKeyFile` 決定用來簽署 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式資訊清單的金鑰檔。 您也可以使用這個相同的金鑰，將強式名稱指派給您的元件。 這個屬性是在 [**專案設計**工具] 的 [**簽署**] 頁面上設定。  
  
  下列屬性會在 [ **安全性** ] 頁面上設定：  
  
- **啟用 ClickOnce 安全性設定** 可決定是否 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 要產生資訊清單。 最初建立專案時， [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 資訊清單產生預設為關閉。 當您第一次發行時，嚮導會自動開啟此旗標。  
  
- **>targetzone** 可決定要發出至 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式資訊清單的信任層級。 可能的值為「網際網路」、「LocalIntranet」和「自訂」。 網際網路和 LocalIntranet 會將預設許可權集合發出到您的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式資訊清單。 LocalIntranet 是預設值，基本上表示完全信任。 自訂指定只將基底應用程式資訊清單檔案中明確指定的許可權發出至 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式資訊清單。 App.config 檔案是僅包含信任資訊定義的部分資訊清單檔案。 它是隱藏的檔案，當您在 [ **安全性** ] 頁面上設定許可權時，會自動新增至您的專案。  
  
  下列是在 [ **發佈** ] 頁面上設定的屬性：  
  
- `PublishUrl` 是要在 IDE 中發行應用程式的位置。 如果沒有指定或屬性，則會將它插入 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式資訊清單 `InstallUrl` `UpdateUrl` 。  
  
- `ApplicationVersion` 指定應用程式的版本 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 。 這是四位數的版本號碼。 如果最後一個數位為 "*"，則 `ApplicationRevision` 會取代在組建階段插入資訊清單中的值。  
  
- `ApplicationRevision` 指定修訂。 這是每次在 IDE 中發行時遞增的整數。 請注意，它不會針對在命令列執行的組建自動遞增。  
  
- `Install` 判斷應用程式是已安裝的應用程式或從 Web 執行的應用程式。  
  
- `InstallUrl` (不會顯示) 是使用者安裝應用程式的位置。 如果有指定，此值會在已啟用屬性的情況下，將此值燒錄到 setup.exe 啟動載入器中 `IsWebBootstrapper` 。 如果未指定，也會將它插入應用程式資訊清單 `UpdateUrl` 。  
  
- `SupportUrl` (未顯示) 是在已安裝應用程式的 [ **新增/移除程式** ] 對話方塊中連結的位置。  
  
  以下是在 [ **應用程式更新** ] 對話方塊中設定的屬性，可從 [ **發佈** ] 頁面存取。  
  
- `UpdateEnabled` 指出應用程式是否應該檢查更新。  
  
- `UpdateMode` 指定前景更新或背景更新。  
  
- `UpdateInterval` 指定應用程式檢查更新的頻率。  
  
- `UpdateIntervalUnits` 指定 `UpdateInterval` 值是以小時、天或周為單位。  
  
- `UpdateUrl` (未顯示) 是應用程式將接收更新的位置。 如果有指定，此值會插入應用程式資訊清單中。  
  
- 下列屬性是在 [ **發行選項** ] 對話方塊中設定的，可從 [ **發行** ] 頁面存取。  
  
- `PublisherName` 指定安裝或執行應用程式時，顯示在提示字元中的發行者名稱。 如果是已安裝的應用程式，它也會用來指定 [ **開始** ] 功能表上的資料夾名稱。  
  
- `ProductName` 指定安裝或執行應用程式時，顯示在提示字元中的產品名稱。 如果是已安裝的應用程式，它也會用來指定 [ **開始** ] 功能表上的快捷方式名稱。  
  
- 以下是在 [ **必要條件** ] 對話方塊中設定的屬性，可從 [ **發佈** ] 頁面存取。  
  
- `BootstrapperEnabled` 決定是否要產生 setup.exe 啟動載入器。  
  
- `IsWebBootstrapper` 判斷 setup.exe 啟動載入器是否可在 Web 或以磁片為基礎的模式下運作。  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL、SupportUrl、PublishURL 和 UpdateURL  
 下表顯示 ClickOnce 部署的四個 URL 選項。  
  
|URL 選項|描述|  
|----------------|-----------------|  
|`PublishURL`|如果您要將 ClickOnce 應用程式發佈至網站，則為必要。|  
|`InstallURL`|選擇性。 如果安裝網站與不同，請設定此 URL 選項 `PublishURL` 。 例如，您可以將設定 `PublishURL` 為 FTP 路徑，並將設定 `InstallURL` 為 Web URL。|  
|`SupportURL`|選擇性。 如果支援網站與不同，請設定此 URL 選項 `PublishURL` 。 例如，您可以將設定 `SupportURL` 為公司的客戶支援網站。|  
|`UpdateURL`|選擇性。 如果更新位置與不同，請設定此 URL 選項 `InstallURL` 。 例如，您可以將設定 `PublishURL` 為 FTP 路徑，並將設定 `UpdateURL` 為 Web URL。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
