---
title: 逐步解說： 手動部署 ClickOnce 應用程式不需要重新簽署，而且會保留商標資訊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb4838e44549f762e609913c92d677832d897edb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>逐步解說：手動部署不需要重新簽署而且會保留商標資訊的 ClickOnce 應用程式
當您建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式，然後將它交給客戶發行和部署，客戶以往都會需要更新的部署資訊清單，並重新簽署。 雖然仍是慣用的方法，在大部分情況下，.NET Framework 3.5 可讓您建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]客戶可以部署而不需要重新產生新的部署資訊清單的部署。 如需詳細資訊，請參閱[部署 ClickOnce 應用程式的測試和實際執行伺服器，而 Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)。  
  
 當您建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式，然後將它交給客戶發行和部署、 應用程式可以使用客戶的商標或保留您的品牌。 比方說，如果應用程式是單一的專屬應用程式，您可能想要保留您的品牌。 如果應用程式高度自訂的每個客戶，您可能想要使用客戶的品牌。 .NET Framework 3.5 可讓您保留您的品牌、 「 發行者 」 資訊和安全性簽章，提供對組織要部署應用程式時。 如需詳細資訊，請參閱[建立 ClickOnce 應用程式供其他人部署](../deployment/creating-clickonce-applications-for-others-to-deploy.md)。  
  
> [!NOTE]
>  在此逐步解說中您建立部署以手動方式使用命令列工具 Mage.exe 或 MageUI.exe 的圖形工具。 如需手動部署的詳細資訊，請參閱[逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本逐步解說中的步驟您需要下列項目：  
  
-   您準備好要部署 Windows Form 應用程式。 此應用程式會指 WindowsFormsApp1。  
  
-   Visual Studio 或 Windows SDK。  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>若要部署 ClickOnce 應用程式與多個部署使用 Mage.exe 商標的支援  
  
1.  開啟 Visual Studio 命令提示字元或[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]命令提示字元，並將變更為目錄，您將會儲存您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]檔案。  
  
2.  建立名為您的部署的目前版本的目錄。 如果這是您要部署應用程式第一次，您可能會選擇**1.0.0.0**。  
  
    > [!NOTE]
    >  您部署的版本可能會有別於應用程式檔案的版本。  
  
3.  建立名為子目錄**bin**並複製所有的應用程式檔案，包括可執行檔、 組件、 資源和資料檔案。  
  
4.  產生應用程式資訊清單，Mage.exe 呼叫。  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  簽署應用程式資訊清單與您的數位憑證。  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  產生的部署資訊清單，Mage.exe 呼叫。 根據預設，Mage.exe 會將標示您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署安裝的應用程式，因此它可以同時線上執行，並離線。 若要讓應用程式可用，只有當使用者在線上時，使用`-i`引數的值與`f`。 此應用程式會利用多個部署功能，因為排除`-providerUrl`Mage.exe 引數。 (排除之前的版本 3.5、.NET Framework 版本中`-providerUrl`離線應用程式將會導致錯誤。)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  未簽署部署資訊清單。  
  
8.  提供的客戶，會將其網路上的應用程式部署的所有檔案。  
  
9. 此時，客戶必須登入他自己自我產生的憑證與部署資訊清單。 例如，如果客戶適用於公司名稱為 Adventure Works，他可以產生自我簽署的憑證透過 MakeCert.exe 工具。 接下來，使用 Pvk2pfx.exe 工具來結合成 PFX 檔，可以傳遞至 Mage.exe MakeCert.exe 所建立的檔案。  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. 客戶接著會使用此憑證來簽署部署資訊清單。  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. 客戶應用程式部署至使用者。  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>若要部署 ClickOnce 應用程式與多個部署使用 MageUI.exe 的版本支援  
  
1.  開啟 Visual Studio 命令提示字元或[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]命令提示字元，並瀏覽至目錄，您將會儲存您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]檔案。  
  
2.  建立名為子目錄**bin**並複製所有的應用程式檔案，包括可執行檔、 組件、 資源和資料檔案。  
  
3.  建立您的部署的目前版本命名的子目錄。 如果這是您要部署應用程式第一次，您可能會選擇**1.0.0.0**。  
  
    > [!NOTE]
    >  您部署的版本可能會有別於應用程式檔案的版本。  
  
4.  移動\\ **bin**目錄至您在步驟 2 中建立的目錄。  
  
5.  啟動的圖形工具 MageUI.exe。  
  
    ```  
    MageUI.exe  
    ```  
  
6.  選取建立新的應用程式資訊清單**檔案**，**新增**，**應用程式資訊清單**從功能表。  
  
7.  在預設的**名稱**索引標籤上，輸入此部署的名稱和版本號碼。 此外，提供的值**發行者**，用來做為資料夾名稱，在 [開始] 功能表中的應用程式的捷徑連結在部署時。  
  
8.  選取**應用程式選項**索引標籤上，按一下 **使用應用程式資訊清單供信任資訊**。 這會讓 淛鵸葺爦這個[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。  
  
9. 選取**檔案**索引標籤上，按一下 **瀏覽**應用程式目錄文字方塊旁邊的按鈕。  
  
10. 選取包含您在步驟 2 中建立的應用程式檔案的目錄，然後按一下**確定**資料夾選取對話方塊上。  
  
11. 按一下**填入** 按鈕，將所有應用程式檔案新增至檔案清單。 如果您的應用程式包含一個以上的可執行檔，會標示主要可執行檔，此為啟動應用程式的部署選取**進入點**從**檔案類型**下拉式清單。 （如果您的應用程式僅包含一個可執行檔，MageUI.exe 會將它標記為您。）  
  
12. 選取**所需的權限**索引標籤，選取您要讓應用程式判斷提示的信任層級。 預設值是**完全信任**，它將會是適用於大部分的應用程式。  
  
13. 選取**檔案**，**儲存**從功能表中，並儲存應用程式資訊清單。 系統會提示您登入應用程式資訊清單，當您將其儲存。  
  
14. 如果您有儲存為檔案系統上檔案的憑證，使用**簽章為憑證檔**選項，然後選取 從檔案系統使用的省略符號 憑證 (**...**) 按鈕。  
  
     -或-  
  
     如果您的憑證保留在可從您的電腦存取的憑證存放區中，選取**以預存的憑證選項簽**，並從提供的清單中選取的憑證。  
  
15. 選取**檔案**，**新增**，**部署資訊清單**從建立您的部署資訊清單中的功能表，然後再針對**名稱**索引標籤上，提供名稱和版本號碼 (**1.0.0.0**在此範例中)。  
  
16. 切換至**更新**索引標籤，然後指定您要更新此應用程式的頻率。 如果您的應用程式使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署 API 來檢查更新檔本身，清除核取方塊標示為**此應用程式應該檢查更新檔**。  
  
17. 切換至**應用程式參考** 索引標籤。您可以預先填入所有的值，這個索引標籤上按一下**選取資訊清單**先前步驟中建立按鈕，選取應用程式資訊清單。  
  
18. 選擇**儲存**並儲存到磁碟的部署資訊清單。 系統會提示您登入應用程式資訊清單，當您將其儲存。 按一下**取消**儲存資訊清單，但不簽署。  
  
19. 提供給客戶的所有應用程式檔案。  
  
20. 此時，客戶必須登入他自己自我產生的憑證與部署資訊清單。 例如，如果客戶適用於公司名稱為 Adventure Works，他可以產生自我簽署的憑證透過 MakeCert.exe 工具。 接下來，使用 Pvk2pfx.exe 工具來結合成 PFX 檔，可以傳遞至 MageUI.exe MakeCert.exe 所建立的檔案。  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. 使用產生的憑證，客戶現在簽署部署資訊清單在 MageUI.exe 中，開啟部署資訊清單，然後儲存檔案。 客戶 簽署 對話方塊出現時，請選取**簽章為憑證檔**選項，然後選擇 儲存在磁碟的 PFX 檔案。  
  
22. 客戶應用程式部署至使用者。  
  
## <a name="next-steps"></a>後續步驟  
  
## <a name="see-also"></a>另請參閱  
 [Mage.exe (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx)