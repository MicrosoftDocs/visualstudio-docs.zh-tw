---
title: "建立 ClickOnce 應用程式，從命令列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 86dba79e6e8b7e3f3b2837e494cfeddd2692d0cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="building-clickonce-applications-from-the-command-line"></a>從命令列建置 ClickOnce 應用程式
在[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]，即使它們建立在整合式的開發環境 (IDE) 中，您可以建置專案，從命令列。 事實上，您可以重建專案，以建立[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]只剩的另一部電腦上[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]安裝。 這可讓您重現組建，使用自動化程序，比方說，在集中建置實驗室，或使用進階指令碼技術建置專案本身的範圍之外。  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>使用 MSBuild 來重現 ClickOnce 應用程式部署  
 當您叫用 msbuild /target:publish 在命令列時，它會告訴 MSBuild 系統建置專案，並建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式的發行資料夾中。 這相當於選取**發行**命令在 IDE 中。  
  
 此命令會執行 msbuild.exe，位於 Visual Studio 命令提示字元環境中的路徑。  
  
 「 目標 」 是 MSBuild 中的指標如何處理命令。 主要目標是 「 建置 」 目標和 「 發行 」 目標。 「 建置 」 目標相當於選取的組建在 IDE 中命令 （或按 F5）。 如果您只想要建置您的專案，您就可以達成此目標輸入`msbuild`。 這個命令可以運作，因為 「 建置 」 目標所產生的所有專案的預設目標[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。 這表示您明確地不需要指定 「 建置 」 目標。 因此，輸入`msbuild`是相同的操作，因為輸入`msbuild /target:build`。  
  
 `/target:publish`命令會告知 MSBuild 叫用發行的目標。 發行目標取決於 「 建置 」 目標。 這表示發行作業是建置作業的超集。 例如，如果您對其中一個 Visual Basic 或 C# 原始程式檔進行變更，對應的組件會自動重建，藉以發行作業。  
  
 如需產生完整資訊[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署使用 Mage.exe 命令列工具來建立您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]資訊清單，請參閱[逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>呤堙冓呤基本 ClickOnce 應用程式使用 MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>建立和發行 ClickOnce 專案  
  
1.  按一下**新專案**從**檔案**功能表。 [ **新增專案** ] 對話方塊隨即出現。  
  
2.  選取**Windows 應用程式**並將其命名`CmdLineDemo`。  
  
3.  從**建置**功能表上，按一下 **發行**命令。  
  
     這個步驟可確保此專案是否已正確設定來產生[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式部署。  
  
     [發行精靈] 隨即出現。  
  
4.  在 [發行精靈] 中，按一下**完成**。  
  
     Visual Studio 會產生，並顯示預設 Web 網頁呼叫 Publish.htm。  
  
5.  儲存專案，並記下儲存所在的資料夾位置。  
  
 上述的步驟建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]專案已發行的第一次。 現在就可以重現組建在 IDE 外面。  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>若要重新產生從命令列組建  
  
1.  結束 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。  
  
2.  從 Windows**啟動**功能表上，按一下 **所有程式**，然後**Microsoft Visual Studio**，然後**Visual Studio Tools**，然後**Visual Studio 命令提示字元**。 這應該會在目前使用者的根資料夾中開啟命令提示字元。  
  
3.  在**Visual Studio 命令提示字元**，將目前目錄變更到您剛才建置以上專案的位置。 例如，輸入`chdir My Documents\Visual Studio\Projects\CmdLineDemo`。  
  
4.  要移除現有的檔案所產生的 「 建立和發行[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]專案中，「 類型`rmdir /s publish`。  
  
     這個步驟是選擇性的但它可確保，新的檔案所有所產生的命令列組建。  
  
5.  輸入 `msbuild /target:publish`。  
  
 上述的步驟將會產生完整[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]子資料夾中的應用程式部署，您的專案名為 P**ublish**。 CmdLineDemo.application 是[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單。 資料夾 CmdLineDemo_1.0.0.0 包含檔案 CmdLineDemo.exe 和 CmdLineDemo.exe.manifest，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 Setup.exe 是在啟動載入器，其預設值設定為安裝[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 DotNetFX 資料夾包含的可轉散發套件[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 這是完整的部署您的應用程式，透過網頁或透過 UNC 或 CD/DVD 所需的檔案。  
  
## <a name="publishing-properties"></a>發行內容  
 當您發行應用程式中的上述程序時，下列屬性會插入到專案檔，發行精靈。 這些屬性會直接影響如何[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]產生的應用程式。  
  
 在 CmdLineDemo.vbproj / CmdLineDemo.csproj:  
  
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
  
 您可以覆寫這些屬性在命令列而不會變更專案檔本身。 例如，下列會建置[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]不啟動載入器的應用程式部署：  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 在控制發行內容[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]從**發行**，**安全性**，和**簽署**屬性頁的**專案設計工具**. 以下是發行的內容，並指出每個應用程式的設計工具的各種屬性頁面中的設定方式的描述：  
  
-   `AssemblyOriginatorKeyFile`用來簽署的金鑰檔會決定您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 此相同金鑰也可用來將強式名稱指派給您的組件。 設定此屬性**簽署**頁面**專案設計工具**。  
  
 下列屬性會設**安全性**頁面：  
  
-   **啟用 ClickOnce 安全性設定**決定是否[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]產生資訊清單。 一開始建立專案時，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]資訊清單產生預設為關閉。 精靈會自動開啟當您發行第一次這個旗標。  
  
-   **TargetZone**發出至信任的層級會決定您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 可能的值為"Internet"，"LocalIntranet"，"Custom"。 網際網路和 LocalIntranet 會導致發出至設定的預設權限您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 LocalIntranet 是預設值，而且基本上表示完全信任。 自訂指定基底資訊清單檔案中明確指定的權限會發出至[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單。 部分的資訊清單檔包含只信任資訊定義為 app.manifest 檔案。 這是隱藏的檔案，自動加入至您的專案上設定權限時**安全性**頁面。  
  
 下列屬性會設**發行**頁面：  
  
-   `PublishUrl`是其中的應用程式將會發行至 IDE 中的位置。 它會插入至[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式資訊清單，如果沒有`InstallUrl`或`UpdateUrl`指定屬性。  
  
-   `ApplicationVersion`指定的版本[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。 這是四位數的版本號碼。 如果最後一個數字是"*"，則`ApplicationRevision`替換為在建立時期插入資訊清單的值。  
  
-   `ApplicationRevision`指定修訂版本。 這是為您在 IDE 中發行每次遞增的整數。 請注意，它不會自動累加建置在命令列執行。  
  
-   `Install`判斷應用程式是否已安裝的應用程式或執行從 Web 應用程式。  
  
-   `InstallUrl`（未顯示） 是使用者安裝應用程式的位置。 如果指定，如果將這個值燒錄到 setup.exe 的啟動載入器`IsWebBootstrapper`屬性已啟用。 它也會插入至應用程式資訊清單 if`UpdateUrl`未指定。  
  
-   `SupportUrl`（未顯示） 已位置連結，以**新增/移除程式**安裝的應用程式 對話方塊。  
  
 下列屬性設定**應用程式更新**對話方塊中，從存取**發行**頁面。  
  
-   `UpdateEnabled`指出是否應該檢查更新的應用程式。  
  
-   `UpdateMode`指定更新前景或背景更新。  
  
-   `UpdateInterval`指定應用程式應該要檢查更新的頻率。  
  
-   `UpdateIntervalUnits`指定是否`UpdateInterval`值是以小時、 天或週為單位。  
  
-   `UpdateUrl`（未顯示） 是應用程式將從其接收更新的位置。 如果指定，這個值會插入應用程式資訊清單中。  
  
-   下列屬性設定**發行選項**對話方塊中，從存取**發行**頁面。  
  
-   `PublisherName`指定在安裝或執行應用程式時所顯示的提示中顯示 「 發行者 」 的名稱。 如果是已安裝的應用程式，它也用來指定資料夾名稱上**啟動**功能表。  
  
-   `ProductName`指定在安裝或執行應用程式時所顯示的提示中顯示的產品名稱。 如果是已安裝的應用程式，它也用於指定捷徑名稱上**啟動**功能表。  
  
-   下列屬性設定**必要條件**對話方塊中，從存取**發行**頁面。  
  
-   `BootstrapperEnabled`決定是否要產生的 setup.exe 啟動載入器。  
  
-   `IsWebBootstrapper`決定 setup.exe 啟動載入器是否可透過網頁或以磁碟為基礎的模式。  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL、 SupportUrl、 PublishURL 和 UpdateURL  
 下表顯示四個 ClickOnce 部署的 URL 選項。  
  
|URL 選項|說明|  
|----------------|-----------------|  
|`PublishURL`|如果您要發行 ClickOnce 應用程式至網站的必要項。|  
|`InstallURL`|選擇項。 設定此 URL 選項，如果安裝站台不同`PublishURL`。 例如，您可以設定`PublishURL`FTP 路徑並集中`InstallURL`至網頁的 URL。|  
|`SupportURL`|選擇項。 設定此 URL 選項，如果支援站台不同`PublishURL`。 例如，您可以設定`SupportURL`至貴公司的客戶支援的網站。|  
|`UpdateURL`|選擇項。 設定此 URL 選項，如果不同的更新位置`InstallURL`。 例如，您可以設定`PublishURL`FTP 路徑並集中`UpdateURL`至網頁的 URL。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)