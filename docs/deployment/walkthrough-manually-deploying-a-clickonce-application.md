---
title: 手動部署 ClickOnce 應用程式
description: 瞭解如何使用命令列版本或圖形化版本的資訊清單產生和編輯工具來建立 ClickOnce 部署。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d1555a7ef1f942e4be0b7cf929e0e1730f99d1d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917281"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>逐步解說：手動部署 ClickOnce 應用程式
如果您無法使用 Visual Studio 來部署 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，或需要使用 advanced 部署功能（例如「信任的應用程式部署」），則應該使用 *Mage.exe* 命令列工具來建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 資訊清單。 本逐步解說將說明如何 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用命令列版本 (*Mage.exe*) 或圖形版本 (MageUI.exe *) 資訊清單產生和編輯工具來* 建立部署。

## <a name="prerequisites"></a>必要條件
 本逐步解說有一些必要條件和選項，讓您在建立部署之前需要選擇。

- 安裝 *Mage.exe* 並 *MageUI.exe*。

   *Mage.exe* 和 *MageUI.exe* 是的一部分 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 。 您必須有已 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 安裝的或 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 隨附于 Visual Studio 的版本。 如需詳細資訊，請參閱 MSDN 上的 [Windows SDK](https://www.microsoft.com/download/details.aspx?id=8279) 。

- 提供要部署的應用程式。

   本逐步解說假設您已準備好要部署的 Windows 應用程式。 此應用程式將稱為 AppToDeploy。

- 決定部署的散發方式。

   發佈選項包括： Web、檔案共用或 CD。 如需詳細資訊，請參閱 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)。

- 判斷應用程式是否需要較高的信任層級。

   如果您的應用程式需要完全信任（例如，完整存取使用者的系統），您可以使用 `-TrustLevel` *Mage.exe* 的選項來設定此選項。 如果您想要為應用程式定義自訂許可權集合，您可以從另一個資訊清單複製 [網際網路或內部網路] 許可權區段、修改它以符合您的需求，並使用文字編輯器或 *MageUI.exe* 將它新增至應用程式資訊清單。 如需詳細資訊，請參閱 [受信任的應用程式部署總覽](../deployment/trusted-application-deployment-overview.md)。

- 取得 Authenticode 憑證。

   您應使用 Authenticode 憑證來簽署您的部署。 您可以使用 Visual Studio、 *MageUI.exe* 或 *MakeCert.exe* 和 *Pvk2Pfx.exe* 工具來產生測試憑證，也可以從憑證授權單位單位 () CA 取得憑證。 如果您選擇使用受信任的應用程式部署，您也必須在所有用戶端電腦上執行一次的憑證安裝。 如需詳細資訊，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。

  > [!NOTE]
  > 您也可以使用您可以從憑證授權單位單位取得的 CNG 憑證來簽署您的部署。

- 請確定應用程式沒有具有 UAC 資訊的資訊清單。

   您必須判斷您的應用程式是否包含具有使用者帳戶控制的資訊清單 (UAC) 資訊（例如 `<dependentAssembly>` 元素）。 若要檢查應用程式資訊清單，您可以使用 Windows Sysinternals [Sigcheck](/sysinternals/downloads/sigcheck) 公用程式。

   如果您的應用程式包含具有 UAC 詳細資料的資訊清單，您必須在沒有 UAC 資訊的情況下重新建立它。 針對 Visual Studio 中的 c # 專案，開啟專案屬性，然後選取 [應用程式] 索引標籤。在 [ **資訊清單** ] 下拉式清單中，選取 [ **建立沒有資訊清單的應用程式**]。 針對 Visual Studio 中的 Visual Basic 專案，開啟專案屬性，選取 [應用程式] 索引標籤，然後按一下 [ **查看 UAC 設定**]。 在開啟的資訊清單檔中，移除單一元素內的所有專案 `<asmv1:assembly>` 。

- 判斷應用程式是否需要用戶端電腦上的必要條件。

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 從 Visual Studio 部署的應用程式可能會包含必要條件安裝啟動載入器 (*setup.exe*) 部署。 本逐步解說會建立部署所需的兩個資訊清單 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 您可以使用 [GenerateBootstrapper](../msbuild/generatebootstrapper-task.md)工作來建立必要條件啟動載入器。

### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>使用 Mage.exe 命令列工具部署應用程式

1. 建立您將在其中儲存部署檔案的目錄 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

2. 在您剛才建立的部署目錄中，建立版本子目錄。 如果這是您第一次部署應用程式，請將版本子目錄命名為 **1.0.0.0**。

   > [!NOTE]
   > 您的部署版本可能與應用程式的版本不同。

3. 將所有應用程式檔案複製到版本子目錄，包括可執行檔、元件、資源和資料檔案。 如有必要，您可以建立其他包含其他檔案的子目錄。

4. 開啟 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 或 Visual Studio 命令提示字元，並變更為版本子目錄。

5. 使用 *Mage.exe* 的呼叫來建立應用程式資訊清單。 下列語句會建立編譯成在 Intel x86 處理器上執行之程式碼的應用程式資訊清單。

   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .
   ```

   > [!NOTE]
   > 請務必在選項之後包含點 ( ) `-FromDirectory` ，這會指出目前的目錄。 如果您未包含點，則必須指定應用程式檔的路徑。

6. 使用您的 Authenticode 憑證簽署應用程式資訊清單。 以您的憑證檔案路徑取代 *mycert.cer .pfx* 。 以 *您的憑證檔案密碼取代密碼* 。

   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd
   ```

   從隨 Visual Studio 和 Windows SDK 一起散發的 .NET Framework 4.6.2 SDK 開始， *mage.exe* 會使用 CNG 以及 Authenticode 憑證來簽署資訊清單。 使用與 Authenticode 憑證相同的命令列參數。

7. 變更為部署目錄的根目錄。

8. 使用 *Mage.exe* 的呼叫來產生部署資訊清單。 根據預設， *Mage.exe* 會將您的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署標示為已安裝的應用程式，讓它可以在線上和離線執行。 若只要使用者在線上，才可使用此應用程式，請使用 `-Install` 選項並將值設為 `false` 。 如果您使用預設值，而且使用者將從網站或檔案共用安裝您的應用程式，請確定選項的值 `-ProviderUrl` 指向 web 伺服器或共用上的應用程式資訊清單位置。

   ```cmd
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application
   ```

9. 使用您的 Authenticode 或 CNG 憑證來簽署部署資訊清單。

    ```cmd
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd
    ```

10. 將部署目錄中的所有檔案複製到部署目的地或媒體。 這可能是網站或 FTP 網站、檔案共用或 CD-ROM 上的資料夾。

11. 為您的使用者提供安裝應用程式所需的 URL、UNC 或實體媒體。 如果您提供 URL 或 UNC，您必須為使用者提供部署資訊清單的完整路徑。 例如，如果 AppToDeploy 部署到 http://webserver01/ AppToDeploy 目錄中，則完整的 URL 路徑為 http://webserver01/AppToDeploy/AppToDeploy.application 。

### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>使用 MageUI.exe 圖形化工具部署應用程式

1. 建立您將在其中儲存部署檔案的目錄 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

2. 在您剛才建立的部署目錄中，建立版本子目錄。 如果這是您第一次部署應用程式，請將版本子目錄命名為 **1.0.0.0**。

   > [!NOTE]
   > 您的部署版本可能與應用程式的版本不同。

3. 將所有應用程式檔案複製到版本子目錄，包括可執行檔、元件、資源和資料檔案。 如有必要，您可以建立其他包含其他檔案的子目錄。

4. 啟動 *MageUI.exe* 圖形化工具。

   ```cmd
   MageUI.exe
   ```

5. 從功能表選取 [檔案]、[**新增** **]、[****應用程式資訊清單**]，建立新的應用程式資訊清單。

6. 在 [預設 **名稱** ] 索引標籤上，輸入此部署的名稱和版本號碼。 此外，請指定您的應用程式所建立的 **處理器** ，例如 x86。

7. 選取 [**檔案] 索引** 標籤，然後選取 [**應用程式目錄**] 文字方塊旁的省略號 (**...**) 按鈕。 [ **流覽資料夾** ] 對話方塊隨即出現。

8. 選取包含應用程式檔的版本子目錄，然後選取 **[確定]**。

9. 如果您要從 Internet Information Services 部署 (IIS) ，請選取 [擴展 **時將 .deploy 副檔名新增至沒有它** 的檔案] 核取方塊。

10. 移至 [ **填入** ] 按鈕，將您所有的應用程式檔新增至檔案清單。 如果您的應用程式包含多個可執行檔，請從 [**檔案類型**] 下拉式清單中選取 [**進入點**]，將此部署的主要可執行檔標記為啟動應用程式。  (如果您的應用程式只包含一個可執行檔， *MageUI.exe* 會為您標示。 ) 

11. 選取 [ **必要許可權** ] 索引標籤，然後選取您需要應用程式判斷提示的信任層級。 預設值是 **FullTrust**，適用于大部分的應用程式。

12. 從 **功能表選取 [** 檔案]、[ **另存** 新檔]。 [簽署選項] 對話方塊隨即出現，提示您簽署應用程式資訊清單。

13. 如果您的憑證儲存為檔案系統上的檔案，請使用 [ **使用憑證簽署** 檔案] 選項，然後使用省略號 (**...**) 按鈕，從檔案系統中選取憑證。 然後輸入您的憑證密碼。

     -或-

     如果您的憑證保留在可從電腦存取的憑證存放區中，請選取 [ **使用預存憑證簽署** ] 選項，然後從提供的清單中選取憑證。

14. 選取 **[確定]** 以簽署您的應用程式資訊清單。 [另存新檔]  對話方塊隨即出現。

15. 在 [ **另存** 新檔] 對話方塊中，指定版本目錄，然後選取 [ **儲存**]。

16. 從 **功能表選取 [** 檔案]、[ **新增**]、[ **部署資訊清單** ]，以建立您的部署資訊清單。

17. 在 [ **名稱** ] 索引標籤上，指定此部署的名稱和版本號碼 (**1.0.0.0** ，此範例) 。 此外，請指定您的應用程式所建立的 **處理器** ，例如 x86。

18. 選取 [ **描述** ] 索引標籤，然後指定 **[發行者** ] 和 [ **產品**] 的值。 當您的應用程式安裝在用戶端電腦上以供離線使用時， (**產品** 是在 Windows [開始] 功能表上提供給您應用程式的名稱。 ) 

19. 選取 [ **部署選項** ] 索引標籤，然後在 [ **開始位置** ] 文字方塊中，指定應用程式資訊清單在 Web 服務器或共用上的位置。 例如， *\\ \myServer\myShare\AppToDeploy.application*。

20. 如果您在上一個步驟中加入了 *deploy* 延伸模組，也請選取 [在此 **使用. deploy** 副檔名]。

21. 選取 [ **更新選項** ] 索引標籤，並指定您希望此應用程式更新的頻率。 如果您的應用程式使用 <xref:System.Deployment.Application.UpdateCheckInfo> 來檢查更新本身，請清除 [ **此應用程式應該檢查更新** ] 核取方塊。

22. 選取 [ **應用程式參考** ] 索引標籤，然後移至 [ **選取資訊清單** ] 按鈕。 [開啟] 對話方塊隨即出現。

23. 選取您稍早建立的應用程式資訊清單，然後選取 [ **開啟**]。

24. 從 **功能表選取 [** 檔案]、[ **另存** 新檔]。 [ **簽署選項** ] 對話方塊隨即出現，提示您簽署部署資訊清單。

25. 如果您的憑證儲存為檔案系統上的檔案，請使用 [ **使用憑證簽署** 檔案] 選項，然後使用省略號 (**...**) 按鈕，從檔案系統中選取憑證。 然後輸入您的憑證密碼。

     -或-

     如果您的憑證保留在可從電腦存取的憑證存放區中，請選取 [ **使用預存憑證簽署** ] 選項，然後從提供的清單中選取憑證。

26. 移至 **[確定]** 以簽署部署資訊清單。 [另存新檔]  對話方塊隨即出現。

27. 在 [ **另存** 新檔] 對話方塊中，將一個目錄移至部署的根目錄，然後選取 [ **儲存**]。

28. 將部署目錄中的所有檔案複製到部署目的地或媒體。 這可能是網站或 FTP 網站、檔案共用或 CD-ROM 上的資料夾。

29. 為您的使用者提供安裝應用程式所需的 URL、UNC 或實體媒體。 如果您提供 URL 或 UNC，您必須為使用者提供部署資訊清單的完整路徑。 例如，如果 AppToDeploy 部署到 http://webserver01/ AppToDeploy 目錄中，則完整的 URL 路徑為 http://webserver01/AppToDeploy/AppToDeploy.application 。

## <a name="next-steps"></a>下一步
 當您需要部署應用程式的新版本時，請建立新的目錄（以新版本命名）（例如1.0.0.1），並將新的應用程式檔案複製到新的目錄。 接下來，您必須遵循先前的步驟來建立和簽署新的應用程式資訊清單，以及更新和簽署部署資訊清單。 請小心指定 *Mage.exe* 和呼叫中的相同較高版本 `-New` `-Update` ，因為只會 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 更新較高的版本，最重要的是最左邊的整數。 如果您使用 *MageUI.exe*，可以藉由開啟部署資訊清單來更新部署資訊清單，然後選取 [ **應用程式參考** ] 索引標籤，移至 [ **選取資訊清單** ] 按鈕，然後選取更新的應用程式資訊清單。

## <a name="see-also"></a>另請參閱
- [Mage.exe (資訊清單產生和編輯工具) ](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (資訊清單產生和編輯工具、圖形用戶端) ](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
