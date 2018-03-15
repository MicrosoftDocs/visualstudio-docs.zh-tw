---
title: "逐步解說： 手動部署 ClickOnce 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 2e0035641a8ed374892060dbaabe79d808150cc2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>逐步解說：手動部署 ClickOnce 應用程式
如果您無法使用 Visual Studio 來部署您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式，或您需要使用進階的部署功能，例如受信任的應用程式部署，您應該使用 Mage.exe 命令列工具來建立您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]資訊清單。 本逐步解說描述如何建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]使用命令列版本 (Mage.exe) 或資訊清單產生和編輯工具的圖形化的版本 (MageUI.exe) 的部署。  
  
## <a name="prerequisites"></a>必要條件  
 本逐步解說包含一些必要條件和您要建置部署之前選擇的選項。  
  
-   安裝 Mage.exe 和 MageUI.exe。  
  
     Mage.exe 和 MageUI.exe 屬於[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]。 您必須有[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]安裝的版本或[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]隨附於 Visual Studio。 如需詳細資訊，請參閱[Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) MSDN 上。  
  
-   提供要部署應用程式。  
  
     本逐步解說假設您擁有您準備好要部署的 Windows 應用程式。 此應用程式會指 AppToDeploy。  
  
-   決定如何將分散式部署。  
  
     發佈選項包括： Web、 檔案共用或 CD。 如需詳細資訊，請參閱 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)。  
  
-   判斷應用程式是否需要更高的信任層級。  
  
     如果您的應用程式需要完全信任 — 例如，完整存取使用者的系統 — 您可以使用`-TrustLevel`Mage.exe 來設定此選項。 如果您想要定義設定應用程式的自訂權限，您可以複製網際網路或內部網路權限 > 一節，從另一個資訊清單、 加以修改以符合您的需求，和將它加入至應用程式資訊清單使用文字編輯器或 MageUI.exe。 如需詳細資訊，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
-   取得 Authenticode 憑證。  
  
     您應該簽署您的部署使用 Authenticode 憑證。 您可以使用 Visual Studio，MageUI.exe 中，或 MakeCert.exe Pvk2Pfx.exe 工具，以產生測試憑證，或者您可以取得憑證從憑證授權單位 (CA)。 如果您選擇使用受信任的應用程式部署，您也必須執行一次安裝到所有用戶端電腦上的憑證。 如需詳細資訊，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
    > [!NOTE]
    >  您也可以簽署您的部署，您可以從憑證授權單位取得的 CNG 憑證。  
  
-   請確定應用程式沒有與 UAC 資訊的資訊清單。  
  
     您必須決定是否應用程式包含資訊清單的使用者帳戶控制 (UAC) 資訊，例如`<dependentAssembly>`項目。 若要檢查應用程式資訊清單，您可以使用 Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035)公用程式。  
  
     如果您的應用程式包含資訊清單以 UAC 的詳細資訊，您必須重新建置它沒有 UAC 資訊。 針對 C# 專案在 Visual Studio 中，開啟專案屬性，然後選取 [應用程式] 索引標籤。在**資訊清單**下拉式清單中，選取**建立無資訊清單的應用程式**。 在 Visual Studio 中 Visual Basic 專案，請開啟 專案屬性，選取 應用程式 索引標籤，然後按一下**檢視 UAC 設定**。 在開啟資訊清單檔案中，移除所有項目內的單一`<asmv1:assembly>`項目。  
  
-   判斷應用程式是否需要用戶端電腦上的必要條件。  
  
     [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]從 Visual Studio 部署的應用程式可以包含必要的安裝啟動載入器 (setup.exe) 與您的部署。 這個逐步解說會建立兩個所需的資訊清單[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署。 您可以使用，以建立必要啟動載入器[GenerateBootstrapper 工作](../msbuild/generatebootstrapper-task.md)。  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>使用 Mage.exe 命令列工具的應用程式部署  
  
1.  建立的目錄，您將在其中儲存您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署檔案。  
  
2.  在您剛才建立的部署目錄，建立版本的子目錄。 如果這是您要部署應用程式第一次，名稱版本子目錄**1.0.0.0**。  
  
    > [!NOTE]
    >  您的部署版本可以從您的應用程式的版本不同。  
  
3.  將所有應用程式檔案複製到版本子目錄，包括可執行檔、 組件、 資源和資料檔案。 如有必要，您可以建立其他包含其他檔案的子目錄。  
  
4.  開啟[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]或 Visual Studio 命令提示字元，並將變更為版本子目錄。  
  
5.  建立應用程式資訊清單，Mage.exe 呼叫。 下列陳述式會建立在 Intel x86 處理器上執行編譯的程式碼的應用程式資訊清單。  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  務必包含句點 （.） 之後`-FromDirectory`選項，指出目前的目錄。 如果您未包含點，您必須在應用程式檔案中指定的路徑。  
  
6.  登入使用 Authenticode 憑證的應用程式資訊清單。 取代*mycert.pfx*與您的憑證檔案的路徑。 取代*passwd*憑證檔案的密碼。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     若要簽署的應用程式資訊清單使用 CNG 憑證，使用下列程式碼。 取代*cngCert.pfx*與您的憑證檔案的路徑。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7.  將變更部署目錄的根目錄。  
  
8.  產生的部署資訊清單，Mage.exe 呼叫。 根據預設，Mage.exe 會將標示您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署安裝的應用程式，因此它可以同時線上執行，並離線。 若要讓應用程式可用，只有當使用者在線上時，使用`-Install`選項值是`false`。 如果您使用預設值，而且使用者將從網站或檔案共用安裝您的應用程式，請確定值`-ProviderUrl`選項點位置的應用程式資訊清單上的 Web 伺服器或共用。  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. 簽署部署資訊清單使用 Authenticode 或 CNG 憑證。  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     或  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. 將複製的所有檔案在部署目錄到部署目的地或媒體。 這可能是網站或 FTP 站台、 檔案共用或 CD-ROM 上的資料夾。  
  
11. 為使用者提供 URL、 UNC 或安裝您的應用程式所需的實體媒體。 如果您提供的 URL 或 UNC，您必須讓使用者的完整路徑的部署資訊清單。 例如，如果 AppToDeploy 部署至 http://webserver01/ AppToDeploy 目錄中，完整的 URL 路徑將 http://webserver01/AppToDeploy/AppToDeploy.application。  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>使用 MageUI.exe 圖形化工具的應用程式部署  
  
1.  建立的目錄，您將在其中儲存您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署檔案。  
  
2.  在您剛才建立的部署目錄，建立版本的子目錄。 如果這是您要部署應用程式第一次，名稱版本子目錄**1.0.0.0**。  
  
    > [!NOTE]
    >  您部署的版本是可能不同於您的應用程式的版本。  
  
3.  將所有應用程式檔案複製到版本子目錄，包括可執行檔、 組件、 資源和資料檔案。 如有必要，您可以建立其他包含其他檔案的子目錄。  
  
4.  啟動 MageUI.exe 圖形化工具。  
  
    ```  
    MageUI.exe  
    ```  
  
5.  選取建立新的應用程式資訊清單**檔案**，**新增**，**應用程式資訊清單**從功能表。  
  
6.  在預設的**名稱**索引標籤上，輸入此部署的名稱和版本號碼。 也指定**處理器**x86，建置您的應用程式。  
  
7.  選取**檔案**索引標籤，然後按一下省略符號 (**...**) 旁邊**應用程式目錄**文字方塊。 瀏覽資料夾 對話方塊隨即出現。  
  
8.  選取包含您的應用程式檔案的版本子目錄，然後按一下**確定**。  
  
9. 如果您將部署從網際網路資訊服務 (IIS) 中，選取**時填入將.deploy 副檔名不需要任何檔案加入**核取方塊。  
  
10. 按一下**填入** 按鈕，將所有應用程式檔案新增至檔案清單。 如果您的應用程式包含一個以上的可執行檔，會標示主要可執行檔，此為啟動應用程式的部署選取**進入點**從**檔案類型**下拉式清單。 （如果您的應用程式包含只有一個可執行檔，MageUI.exe 會將它標記為您。）  
  
11. 選取**所需的權限**索引標籤上，選取您需要您的應用程式，可判斷提示的信任層級。 預設值是**FullTrust**，它將會是適用於大部分的應用程式。  
  
12. 選取**檔案**，**存**從功能表。 簽章的選項會出現對話方塊提示您簽署應用程式資訊清單。  
  
13. 如果您有儲存為檔案系統上檔案的憑證，使用**憑證檔案以簽署**選項，然後從檔案系統選取憑證，使用省略符號 (**...**) 按鈕。 然後輸入憑證密碼。  
  
     -或-  
  
     如果您的憑證保留在憑證存放區可從您的電腦存取，請選取**預存憑證以簽署**選項，並從提供的清單中選取的憑證。  
  
14. 按一下**確定**來簽署應用程式資訊清單。 [另存新檔] 對話方塊隨即出現。  
  
15. 在 [另存新檔] 對話方塊中指定版本的目錄，然後**儲存**。  
  
16. 選取**檔案**，**新增**，**部署資訊清單**功能表來建立您的部署資訊清單。  
  
17. 在**名稱**索引標籤上，指定此部署的名稱和版本號碼 (**1.0.0.0**在此範例中)。 也指定**處理器**x86，建置您的應用程式。  
  
18. 選取**描述**索引標籤，並指定值**發行者**和**Produc * * * t**。 (**產品**是供離線使用的用戶端電腦上安裝的應用程式時，您在 Windows [開始] 功能表上的應用程式指定的名稱。)  
  
19. 選取**部署選項** 索引標籤，然後在**開始位置**文字方塊中，指定在 Web 伺服器或共用上的應用程式資訊清單的位置。 例如， \\\myServer\myShare\AppToDeploy.application。  
  
20. 如果您在上一個步驟中加入.deploy 副檔名，也選取**使用.deploy 副檔名**這裡。  
  
21. 選取**更新選項**索引標籤，然後指定您想要更新此應用程式的頻率。 如果您的應用程式使用<xref:System.Deployment.Application.UpdateCheckInfo>若要檢查更新本身，請清除**此應用程式應該檢查更新檔**核取方塊。  
  
22. 選取**應用程式參考**索引標籤，然後按一下 [**選取資訊清單**] 按鈕。 開啟的對話方塊隨即出現。  
  
23. 選取您稍早建立的應用程式資訊清單，然後按一下**開啟**。  
  
24. 選取**檔案**，**存**從功能表。 簽章的選項會出現對話方塊提示您簽署部署資訊清單。  
  
25. 如果您有儲存為檔案系統上檔案的憑證，使用**憑證檔案以簽署**選項，然後從檔案系統選取憑證，使用省略符號 (**...**) 按鈕。 然後輸入憑證密碼。  
  
     -或-  
  
     如果您的憑證保留在憑證存放區可從您的電腦存取，請選取**預存憑證以簽署**選項，並從提供的清單中選取的憑證。  
  
26. 按一下**確定**來簽署部署資訊清單。 [另存新檔] 對話方塊隨即出現。  
  
27. 在**存**對話方塊，移一層目錄至您的部署，然後再按一下根**儲存**。  
  
28. 將複製的所有檔案在部署目錄到部署目的地或媒體。 這可能是網站或 FTP 站台、 檔案共用或 CD-ROM 上的資料夾。  
  
29. 為使用者提供 URL、 UNC 或安裝您的應用程式所需的實體媒體。 如果您提供的 URL 或 UNC，您必須讓使用者在部署資訊清單的完整路徑。 例如，如果 AppToDeploy 部署至 http://webserver01/ AppToDeploy 目錄中，完整的 URL 路徑將 http://webserver01/AppToDeploy/AppToDeploy.application。  
  
## <a name="next-steps"></a>後續步驟  
 當您需要部署新版應用程式時，建立名為新版本之後的新目錄，例如 1.0.0.1—and 新應用程式檔案複製到新的目錄。 接著，您必須遵循上述步驟，建立和簽署新的應用程式資訊清單，並更新並簽署部署資訊清單。 小心指定在這兩個 Mage.exe 相同的更高版本`-New`和`-Update`呼叫，為[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]更高版本中，只會更新具有最重要的最左邊的整數。 如果您使用 MageUI.exe，您可以更新部署資訊清單開啟它，選取**應用程式參考**索引標籤上，按一下**選取資訊清單**按鈕，然後再選取 更新應用程式資訊清單。  
  
## <a name="see-also"></a>請參閱  
 [Mage.exe (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)