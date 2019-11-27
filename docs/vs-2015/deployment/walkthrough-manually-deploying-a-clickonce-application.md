---
title: 逐步解說：手動部署 ClickOnce 應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e1099eaf8d766088612abbb399bdf004e6378e4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294674"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>逐步解說：手動部署 ClickOnce 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您無法使用 Visual Studio 部署您的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，或需要使用 advanced 部署功能（例如受信任的應用程式部署），您應該使用 Mage.exe 命令列工具來建立您的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 資訊清單。 本逐步解說說明如何使用命令列版本（Mage.exe）或資訊清單產生和編輯工具的圖形化版本（Mageui.exe）來建立 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署。  
  
## <a name="prerequisites"></a>必要條件  
 這個逐步解說有一些必要條件和選項，您必須在建立部署之前選擇。  
  
- 安裝 Mage.exe 和 Mageui.exe。  
  
     Mage.exe 和 Mageui.exe 是 [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]的一部分。 您必須安裝 [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] 或包含 Visual Studio 的 [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] 版本。 如需詳細資訊，請參閱 MSDN 上的[Windows SDK](https://go.microsoft.com/fwlink/?LinkId=158044) 。  
  
- 提供要部署的應用程式。  
  
     本逐步解說假設您已準備好要部署的 Windows 應用程式。 此應用程式會被稱為 AppToDeploy。  
  
- 決定部署的散發方式。  
  
     散發選項包括： Web、檔案共用或 CD。 如需詳細資訊，請參閱 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)。  
  
- 判斷應用程式是否需要更高的信任層級。  
  
     如果您的應用程式需要完全信任（例如，使用者系統的完整存取權），您可以使用 Mage.exe 的 `-TrustLevel` 選項來設定此項。 如果您想要定義應用程式的自訂許可權集合，可以從另一個資訊清單複製 [網際網路] 或 [內部網路] 許可權區段，修改它以符合您的需求，然後使用文字編輯器或 Mageui.exe 將它加入至應用程式資訊清單。 如需詳細資訊，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
- 取得 Authenticode 憑證。  
  
     您應該使用 Authenticode 憑證來簽署您的部署。 您可以使用 Visual Studio、Mageui.exe 或 MakeCert 和 Pvk2Pfx 工具來產生測試憑證，也可以從憑證授權單位單位（CA）取得憑證。 如果您選擇使用信任的應用程式部署，您也必須在所有用戶端電腦上執行一次憑證的安裝。 如需詳細資訊，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
    > [!NOTE]
    > 您也可以使用可從憑證授權單位單位取得的 CNG 憑證來簽署您的部署。  
  
- 請確定應用程式沒有具有 UAC 資訊的資訊清單。  
  
     您必須判斷您的應用程式是否包含含有使用者帳戶控制（UAC）資訊的資訊清單，例如 `<dependentAssembly>` 元素。 若要檢查應用程式資訊清單，您可以使用 Windows Sysinternals [Sigcheck](https://go.microsoft.com/fwlink/?LinkId=158035)公用程式。  
  
     如果您的應用程式包含具有 UAC 詳細資料的資訊清單，您必須在不使用 UAC 資訊的情況下重新建立它。 針對 Visual Studio C#中的專案，開啟 [專案屬性]，然後選取 [應用程式] 索引標籤。在 [**資訊清單**] 下拉式清單中，選取 [**建立沒有資訊清單的應用程式**]。 若為 Visual Studio 中的 Visual Basic 專案，請開啟專案屬性、選取 [應用程式] 索引標籤，然後按一下 [**查看 UAC 設定**]。 在開啟的資訊清單檔中，移除單一 `<asmv1:assembly>` 元素內的所有專案。  
  
- 判斷應用程式是否需要用戶端電腦上的必要條件。  
  
     從 Visual Studio 部署的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，可以包含必要條件安裝啟動載入器（setup.exe）與您的部署。 此逐步解說會建立 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署所需的兩個資訊清單。 您可以使用[GenerateBootstrapper](../msbuild/generatebootstrapper-task.md)工作來建立必要的啟動載入器。  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>使用 Mage.exe 命令列工具部署應用程式  
  
1. 建立將用來儲存 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署檔案的目錄。  
  
2. 在您剛才建立的部署目錄中，建立版本子目錄。 如果這是您第一次部署應用程式，請將版本的子目錄命名為**1.0.0.0**。  
  
    > [!NOTE]
    > 您的部署版本可能與您的應用程式版本不同。  
  
3. 將所有應用程式檔案複製到版本子目錄，包括可執行檔、元件、資源和資料檔案。 如有需要，您可以建立包含其他檔案的其他子目錄。  
  
4. 開啟 [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] 或 Visual Studio 命令提示字元，並變更為版本子目錄。  
  
5. 使用 Mage.exe 的呼叫來建立應用程式資訊清單。 下列語句會建立編譯成在 Intel x86 處理器上執行之程式碼的應用程式資訊清單。  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    > 請務必在 `-FromDirectory` 選項後面加上點（.），這會指出目前的目錄。 如果您不包含點，則必須指定應用程式檔的路徑。  
  
6. 使用您的 Authenticode 憑證簽署應用程式資訊清單。 將*mycert.cer*取代為您的憑證檔案路徑。 將*passwd*取代為憑證檔案的密碼。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     若要使用 CNG 憑證簽署應用程式資訊清單，請使用下列。 將*cngCert*取代為您的憑證檔案路徑。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7. 切換至部署目錄的根目錄。  
  
8. 使用 Mage.exe 的呼叫產生部署資訊清單。 根據預設，Mage.exe 會將您的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署標示為已安裝的應用程式，使其可在線上和離線狀態下執行。 若要讓應用程式僅在使用者上線時可用，請使用 [`-Install`] 選項，並將值設為 [`false`]。 如果您使用預設值，而且使用者將從網站或檔案共用安裝您的應用程式，請確定 [`-ProviderUrl`] 選項的值指向 Web 服務器或共用上應用程式資訊清單的位置。  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. 使用您的 Authenticode 或 CNG 憑證簽署部署資訊清單。  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     或  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. 將部署目錄中的所有檔案複製到部署目的地或媒體。 這可能是網站或 FTP 網站、檔案共用或 CD-ROM 上的資料夾。  
  
11. 為您的使用者提供安裝應用程式所需的 URL、UNC 或實體媒體。 如果您提供 URL 或 UNC，您必須為使用者提供部署資訊清單的完整路徑。 例如，如果 AppToDeploy 部署至 AppToDeploy 目錄中 http://webserver01/，則完整的 URL 路徑會是 http://webserver01/AppToDeploy/AppToDeploy.application。  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>使用 Mageui.exe 圖形化工具部署應用程式  
  
1. 建立將用來儲存 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署檔案的目錄。  
  
2. 在您剛才建立的部署目錄中，建立版本子目錄。 如果這是您第一次部署應用程式，請將版本的子目錄命名為**1.0.0.0**。  
  
    > [!NOTE]
    > 您的部署版本可能與您的應用程式版本不同。  
  
3. 將所有應用程式檔案複製到版本子目錄，包括可執行檔、元件、資源和資料檔案。 如有需要，您可以建立包含其他檔案的其他子目錄。  
  
4. 啟動 Mageui.exe 圖形化工具。  
  
    ```  
    MageUI.exe  
    ```  
  
5. 從功能表選取 [檔案]、[**新增** **]、[** **應用程式資訊清單**]，以建立新的應用程式資訊清單  
  
6. 在 [預設**名稱**] 索引標籤上，輸入此部署的名稱和版本號碼。 也請指定用來建立應用程式的**處理器**，例如 x86。  
  
7. 選取 [**檔案] 索引**標籤，然後按一下 [**應用程式目錄**] 文字方塊旁的省略號（ **...** ）按鈕。 [流覽資料夾] 對話方塊隨即出現。  
  
8. 選取包含應用程式檔的版本子目錄，然後按一下 **[確定]** 。  
  
9. 如果您將從 Internet Information Services （IIS）部署，請選取 [填入**時將副檔名新增至任何沒有該檔案的**檔案] 核取方塊。  
  
10. 按一下 [**填入**] 按鈕，將您所有的應用程式檔新增至檔案清單。 如果您的應用程式包含一個以上的可執行檔，請從 [**檔案類型**] 下拉式清單中選取 [**進入點**]，將此部署的主要可執行檔標記為啟動應用程式。 （如果您的應用程式只包含一個可執行檔，Mageui.exe 會為您標記）。  
  
11. 選取 [**必要許可權**] 索引標籤，然後選取您需要應用程式判斷提示的信任層級。 預設值為**FullTrust**，這適用于大部分的應用程式。  
  
12. 從功能表**中選取 [** 檔案]、[**另存**新檔]。 [簽署選項] 對話方塊隨即出現，提示您簽署應用程式資訊清單。  
  
13. 如果您將憑證儲存為檔案系統上的檔案，請使用 [使用**憑證檔案簽署**] 選項，然後使用省略號（ **...** ）按鈕從檔案系統中選取憑證。 然後輸入您的憑證密碼。  
  
     -或-  
  
     如果您的憑證保存在您的電腦可存取的憑證存放區中，請選取 [**使用預存憑證簽署**] 選項，然後從提供的清單中選取憑證。  
  
14. 按一下 **[確定]** 以簽署您的應用程式資訊清單。 [另存新檔] 對話方塊隨即出現。  
  
15. 在 [另存新檔] 對話方塊中，指定版本目錄，然後按一下 [**儲存**]。  
  
16. 從功能表**中選取 [** 檔案]、[**新增**]、[**部署資訊清單**]，以建立部署資訊清單。  
  
17. 在 [**名稱**] 索引標籤上，指定此部署的名稱和版本號碼（在此範例中為**1.0.0.0** ）。 也請指定用來建立應用程式的**處理器**，例如 x86。  
  
18. 選取 [**描述**] 索引標籤，並指定 **[發行者**] 和 [**產品**] 的值。 （**產品**是當您的應用程式安裝在用戶端電腦上供離線使用時，在 Windows [開始] 功能表上提供給您的應用程式的名稱）。  
  
19. 選取 [**部署選項**] 索引標籤，然後在 [**開始位置**] 文字方塊中，指定 Web 服務器或共用上的應用程式資訊清單位置。 例如，\\\myServer\myShare\AppToDeploy.application。  
  
20. 如果您在上一個步驟中新增了. deploy 延伸模組，請在這裡選取 [**使用. 部署**副檔名]。  
  
21. 選取 [**更新選項**] 索引標籤，並指定您想要此應用程式更新的頻率。 如果您的應用程式使用 <xref:System.Deployment.Application.UpdateCheckInfo> 來檢查是否有更新，請清除 [**此應用程式應該檢查更新**] 核取方塊。  
  
22. 選取 [**應用程式參考**] 索引標籤，然後按一下 [**選取資訊清單**] 按鈕。 [開啟] 對話方塊隨即出現。  
  
23. 選取您稍早建立的應用程式資訊清單，然後按一下 [**開啟**]。  
  
24. 從功能表**中選取 [** 檔案]、[**另存**新檔]。 [簽署選項] 對話方塊隨即出現，提示您簽署部署資訊清單。  
  
25. 如果您將憑證儲存為檔案系統上的檔案，請使用 [使用**憑證檔案簽署**] 選項，然後使用省略號（ **...** ）按鈕從檔案系統中選取憑證。 然後輸入您的憑證密碼。  
  
     -或-  
  
     如果您的憑證保存在您的電腦可存取的憑證存放區中，請選取 [**使用預存憑證簽署**] 選項，然後從提供的清單中選取憑證。  
  
26. 按一下 **[確定]** 以簽署您的部署資訊清單。 [另存新檔] 對話方塊隨即出現。  
  
27. 在 [**另存**新檔] 對話方塊中，將一個目錄移至部署的根目錄，然後按一下 [**儲存**]。  
  
28. 將部署目錄中的所有檔案複製到部署目的地或媒體。 這可能是網站或 FTP 網站、檔案共用或 CD-ROM 上的資料夾。  
  
29. 為您的使用者提供安裝應用程式所需的 URL、UNC 或實體媒體。 如果您提供 URL 或 UNC，您必須為使用者提供部署資訊清單的完整路徑。 例如，如果 AppToDeploy 部署至 AppToDeploy 目錄中 http://webserver01/，則完整的 URL 路徑會是 http://webserver01/AppToDeploy/AppToDeploy.application。  
  
## <a name="next-steps"></a>後續步驟  
 當您需要部署新版本的應用程式時，請在新版本（例如1.0.0.1）上建立名為的新目錄，然後將新的應用程式檔案複製到新的目錄。 接下來，您必須遵循先前的步驟來建立和簽署新的應用程式資訊清單，並更新和簽署部署資訊清單。 請小心在 Mage.exe `-New` 和 `–Update` 呼叫中指定相同的較高版本，因為 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 只會更新較高的版本，最左邊的整數最重要。 如果您使用 Mageui.exe，可以藉由開啟、選取 [**應用程式參考**] 索引標籤、按一下 [**選取資訊清單**] 按鈕，然後選取已更新的應用程式資訊清單來更新部署資訊清單。  
  
## <a name="see-also"></a>另請參閱  
 [Mage.exe (資訊清單產生和編輯工具)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [ndptecclick](../deployment/clickonce-application-manifest.md)
