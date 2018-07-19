---
title: 建置 ClickOnce 應用程式，從命令列 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ceba7b3fd59c571b3541385cf6cd3946796a8e74
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079414"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>建置 ClickOnce 應用程式，從命令列
在  [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]，即使它們建立在整合式的開發環境 (IDE) 中，您可以建置專案，從命令列。 事實上，您可以重建專案，以建立[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]只有另一部電腦上[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]安裝。 這可讓您重現組建，使用自動化程序，比方說，在中央的組建實驗室，或使用進階指令碼撰寫技巧，建置專案本身的範圍之外。  
  
## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>使用 MSBuild 來重現 ClickOnce 應用程式部署  
 當您叫用 msbuild /target:publish，在命令列時，它會告訴 MSBuild 系統建置專案，並建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]publish 資料夾中的應用程式。 這相當於選取**發佈**命令在 IDE 中。  
  
 此命令會執行*msbuild.exe*，其位於 Visual Studio 命令提示字元環境中的路徑。  
  
 「 目標 」 是 MSBuild 中的指標如何處理命令。 索引鍵的目標是 「 建置 」 目標和 「 發行 」 的目標。 「 建置 」 目標相當於選取的組建在 IDE 中，命令 （或按 F5）。 如果您只想要建置專案時，您就可以達成此目標輸入`msbuild`。 此命令運作，因為 「 建置 」 目標所產生的所有專案的預設目標[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。 這表示您明確不需要指定 「 建置 」 目標。 因此，輸入`msbuild`是相同的作業，做為輸入`msbuild /target:build`。  
  
 `/target:publish`命令會告知 MSBuild，以叫用的發行目標。 發行目標取決於 「 建置 」 目標。 這表示在發行作業會建立作業的超集。 比方說，如果您對其中一個 Visual Basic 或 C# 原始程式檔進行變更，對應的組件自動會重建所發行作業。  
  
 如需產生完整的資訊[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署使用 Mage.exe 命令列工具來建立您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]資訊清單，請參閱[逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>建立並建置基本的 ClickOnce 應用程式，使用 MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>若要建立及發行 ClickOnce 專案  
  
1.  按一下 **新的專案**從**檔案**功能表。 [ **新增專案** ] 對話方塊隨即出現。  
  
2.  選取  **Windows 應用程式**並將它命名`CmdLineDemo`。  
  
3.  從**建置**功能表上，按一下**發佈**命令。  
  
     這個步驟可確保專案是否已正確設定來產生[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式部署。  
  
     [發行精靈] 隨即出現。  
  
4.  在 [發行精靈] 中，按一下**完成**。  
  
     Visual Studio 會產生並顯示預設的網頁，稱為*Publish.htm*。  
  
5.  儲存專案，並記下儲存所在的資料夾位置。  
  
 上述步驟建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]專案已發行的第一次。 現在您可以重現組建在 IDE 外面。  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>若要重新產生從命令列組建  
  
1.  結束 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。  
  
2.  從 Windows**開始**功能表上，按一下**所有程式**，然後**Microsoft Visual Studio**，然後**Visual Studio Tools**，則**Visual Studio 命令提示字元**。 這應該會在目前使用者的根資料夾中開啟命令提示字元。  
  
3.  在  **Visual Studio 命令提示字元**，將目前的目錄變更為您上方建置的專案的位置。 例如，輸入`chdir My Documents\Visual Studio\Projects\CmdLineDemo`。  
  
4.  若要移除現有的檔案中產生"來建立和發佈[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]專案中，「 型別`rmdir /s publish`。  
  
     這個步驟是選擇性的但它可確保，新的檔案所所有產生之命令列組建。  
  
5.  輸入 `msbuild /target:publish`。  
  
 上述步驟將會產生完整[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]的子資料夾中的應用程式部署，您的專案命名為**發行**。 *CmdLineDemo.application*是[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單。 資料夾*CmdLineDemo_1.0.0.0*包含的檔案*CmdLineDemo.exe*並*CmdLineDemo.exe.manifest*，則[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 *Setup.exe*是啟動載入器，其預設值設定為安裝[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 DotNetFX 資料夾包含的可轉散發套件[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 這是完整的部署您的應用程式，透過 Web 或透過 UNC 或 CD/DVD 所需的檔案。  
  
## <a name="publish-properties"></a>發行屬性  
 當您在上述程序中發佈應用程式時，下列屬性會插入到您的專案檔，發行精靈。 這些屬性會直接影響如何[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]產生的應用程式。  
  
 在  *CmdLineDemo.vbproj* / *CmdLineDemo.csproj*:  
  
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
  
 您可以而不需要變更專案檔本身來覆寫在命令列屬性的設定。 例如，下列會建置[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式部署，而不需要啟動載入器：  
  
```cmd  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 發行內容會以控制[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]從**發佈**，**安全性**，和**簽署** 屬性頁面**專案設計工具**. 以下是發行的內容，以及表示每個應用程式的設計工具的各種屬性頁面中的設定方式的描述：  
  
-   `AssemblyOriginatorKeyFile` 判斷用來簽署的金鑰檔您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 這個相同的索引鍵可能也可用來將強式名稱指派給您的組件。 設定此屬性**Signing**頁**專案設計工具**。  
  
 在時會設定下列屬性**安全性**頁面：  
  
-   **啟用 ClickOnce 安全性設定**決定是否[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]產生資訊清單。 一開始建立專案時，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]資訊清單產生預設為關閉。 精靈會自動開啟當您發行第一次這個旗標。  
  
-   **TargetZone**發出至信任的層級會決定您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 可能的值為 「 網際網路 」、 「 LocalIntranet 」 及 「 自訂 」。 網際網路與 LocalIntranet 會發出至設定的預設權限您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 LocalIntranet 是預設值，所以基本上完全信任。 自訂指定，只有在基底中明確指定的權限*app.manifest*檔案會發出至[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 *App.manifest*檔案是包含只信任資訊定義的部分資訊清單檔案。 它是隱藏的檔案，並自動新增至您的專案上設定權限時**安全性**頁面。  
  
 在時會設定下列屬性**發佈**頁面：  
  
-   `PublishUrl` 是，應用程式將會發行至在 IDE 中的位置。 它會插入[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單，如果既未`InstallUrl`或`UpdateUrl`指定屬性。  
  
-   `ApplicationVersion` 指定的版本[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。 這是四位數的版本號碼。 如果最後一個數字是"*"，則`ApplicationRevision`替換為插入資訊清單，在建置階段的值。  
  
-   `ApplicationRevision` 指定修訂版本。 這是整數，增加每次您在 IDE 中發行。 請注意，就會不會自動遞增組建在命令列執行。  
  
-   `Install` 判斷應用程式是否已安裝的應用程式或執行從 Web 應用程式。  
  
-   `InstallUrl` （未顯示） 是讓使用者安裝應用程式的位置。 如果指定，這個值燒錄到*setup.exe*啟動載入器如果`IsWebBootstrapper`屬性處於啟用狀態。 它也會插入至應用程式資訊清單 if`UpdateUrl`未指定。  
  
-   `SupportUrl` （未顯示） 位置連結**新增/移除程式**安裝的應用程式 對話方塊。  
  
 設定下列屬性**應用程式更新** 對話方塊中，從存取**發佈**頁面。  
  
-   `UpdateEnabled` 指出是否應該檢查更新的應用程式。  
  
-   `UpdateMode` 指定更新前景或背景更新。  
  
-   `UpdateInterval` 指定應用程式應該要檢查更新的頻率。  
  
-   `UpdateIntervalUnits` 指定是否`UpdateInterval`值是以小時、 天或週為單位。  
  
-   `UpdateUrl` （未顯示） 是應用程式將從其接收更新的位置。 如果指定，這個值會插入應用程式資訊清單中。  
  
-   設定下列屬性**發行選項** 對話方塊中，從存取**發佈**頁面。  
  
-   `PublisherName` 指定在安裝或執行應用程式時所顯示的提示中顯示 「 發行者 」 的名稱。 在已安裝的應用程式，它也會在指定的資料夾名稱**啟動**功能表。  
  
-   `ProductName` 指定在安裝或執行應用程式時所顯示的提示中顯示的產品名稱。 在已安裝的應用程式，它也會在指定的捷徑名稱**啟動**功能表。  
  
-   設定下列屬性**必要條件** 對話方塊中，從存取**發佈**頁面。  
  
-   `BootstrapperEnabled` 決定是否要產生*setup.exe*啟動載入器。  
  
-   `IsWebBootstrapper` 決定是否*setup.exe*啟動載入器適用於透過 Web 或以磁碟為基礎的模式。  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL、 SupportUrl、 PublishURL 和 UpdateURL  
 下表顯示 ClickOnce 部署的四個 URL 選項。  
  
|URL 選項|描述|  
|----------------|-----------------|  
|`PublishURL`|如果您要發行 ClickOnce 應用程式至網站的必要項。|  
|`InstallURL`|選擇性。 設定此 URL 選項，如果安裝的網站是不同於`PublishURL`。 例如，您可以設定`PublishURL`為 FTP 路徑並將`InstallURL`Web url。|  
|`SupportURL`|選擇性。 設定此 URL 選項，如果 「 支援 」 網站是不同於`PublishURL`。 例如，您可以設定`SupportURL`至貴公司的客戶支援的網站。|  
|`UpdateURL`|選擇性。 設定此 URL 選項，如果更新位置是不同於`InstallURL`。 例如，您可以設定`PublishURL`為 FTP 路徑並將`UpdateURL`Web url。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)