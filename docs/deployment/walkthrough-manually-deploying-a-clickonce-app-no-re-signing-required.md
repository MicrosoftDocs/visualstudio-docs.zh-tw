---
title: 手動部署 ClickOnce 應用程式 & 保持商標
description: 瞭解如何建立由客戶部署的 ClickOnce 應用程式，而不需要產生新的部署資訊清單，也可以使用客戶商標。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0e8895f45524526fc8007ff909a9c541e9899b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917263"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>逐步解說：手動部署不需要重新簽署而且會保留商標資訊的 ClickOnce 應用程式
當您建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，並將它提供給客戶進行發佈和部署時，客戶通常必須更新部署資訊清單並重新簽署。 雖然這在大部分情況下仍是慣用的方法，但是 .NET Framework 3.5 可讓您建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 可由客戶部署的部署，而不需要重新產生新的部署資訊清單。 如需詳細資訊，請參閱 [部署 ClickOnce 應用程式以進行測試和實際執行伺服器，而不需](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)進行簽署。

 當您建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，並將它提供給客戶進行發佈和部署時，應用程式可以使用客戶的商標或保留您的商標。 例如，如果應用程式是單一專屬的應用程式，您可能會想要保留您的品牌。 如果每個客戶都有高度自訂的應用程式，您可能會想要使用客戶的商標。 當您將應用程式提供給組織進行部署時，.NET Framework 3.5 可讓您保留商標、發行者資訊和安全性簽章。 如需詳細資訊，請參閱 [建立 ClickOnce 應用程式供其他人部署](../deployment/creating-clickonce-applications-for-others-to-deploy.md)。

> [!NOTE]
> 在這個逐步解說中，您會使用命令列工具 *Mage.exe* 或圖形化工具 *MageUI.exe*，手動建立部署。 如需手動部署的詳細資訊，請參閱 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。

## <a name="prerequisites"></a>必要條件
 若要執行這個逐步解說中的步驟，您需要下列各項：

- 您可以部署的 Windows Forms 應用程式。 此應用程式將稱為 *WindowsFormsApp1*。

- Visual Studio 或 Windows SDK。

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>使用 Mage.exe 部署具有多個部署和商標支援的 ClickOnce 應用程式

1. 開啟 Visual Studio 命令提示字元或 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 命令提示字元，然後變更至您將在其中儲存檔案的目錄 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

2. 建立以目前的部署版本命名的目錄。 如果這是您第一次部署應用程式，您可能會選擇 **1.0.0.0**。

   > [!NOTE]
   > 您的部署版本可能與應用程式檔的版本不同。

3. 建立名為 **bin** 的子目錄，並將您所有的應用程式檔案複製到這裡，包括可執行檔、元件、資源和資料檔案。

4. 使用 Mage.exe 的呼叫來產生應用程式資訊清單。

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. 使用您的數位憑證簽署應用程式資訊清單。

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. 使用 *Mage.exe* 的呼叫來產生部署資訊清單。 根據預設， *Mage.exe* 會將您的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署標示為已安裝的應用程式，讓它可以在線上和離線執行。 若要讓應用程式只有在使用者在線上時才能使用，請使用 `-i` 具有值的引數 `f` 。 因為此應用程式會利用多個部署功能，所以請排除 `-providerUrl` *Mage.exe* 的引數。 在3.5 版之前的 .NET Framework 版本中 (， `-providerUrl` 離線應用程式的排除會導致錯誤。 ) 

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. 請勿簽署部署資訊清單。

8. 將所有的檔案提供給客戶，以在其網路上部署應用程式。

9. 此時，客戶必須使用自己本身產生的憑證來簽署部署資訊清單。 例如，如果客戶任職于名為「艾德公司」的公司，他可以使用 *MakeCert.exe* 工具產生自我簽署憑證。 接下來，使用 *Pvk2pfx.exe* 工具，將 *MakeCert.exe* 所建立的檔案結合成可傳遞至 *Mage.exe* 的 PFX 檔案。

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. 客戶接下來會使用此憑證來簽署部署資訊清單。

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. 客戶將應用程式部署到其使用者。

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>使用 MageUI.exe 部署具有多個部署和商標支援的 ClickOnce 應用程式

1. 開啟 Visual Studio 命令提示字元或 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 命令提示字元，然後流覽至您將在其中儲存檔案的目錄 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

2. 建立名為 **bin** 的子目錄，並將您所有的應用程式檔案複製到這裡，包括可執行檔、元件、資源和資料檔案。

3. 建立以目前的部署版本命名的子目錄。 如果這是您第一次部署應用程式，您可能會選擇 **1.0.0.0**。

   > [!NOTE]
   > 您的部署版本可能與應用程式檔的版本不同。

4. 將 \\ **bin** 目錄移至您在步驟2中建立的目錄。

5. 啟動圖形化工具 *MageUI.exe*。

   ```cmd
   MageUI.exe
   ```

6. 從功能表選取 [檔案]、[**新增** **]、[****應用程式資訊清單**]，建立新的應用程式資訊清單。

7. 在 [預設 **名稱** ] 索引標籤上，輸入此部署的名稱和版本號碼。 此外，請提供 **發行者** 的值，此值將會在部署時用來作為應用程式快捷方式 [開始] 功能表連結的資料夾名稱。

8. 選取 [ **應用程式選項** ] 索引標籤，然後按一下 [ **使用應用程式資訊清單取得信任資訊**] 這會啟用此應用程式的協力廠商商標 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

9. 選取 [**檔案] 索引** 標籤，然後按一下 [**應用程式目錄**] 文字方塊旁的 [**流覽]** 按鈕。

10. 選取您在步驟2中建立的應用程式檔所在的目錄，然後按一下 [資料夾選取專案] 對話方塊中的 **[確定]** 。

11. 按一下 [ **填入** ] 按鈕，將您所有的應用程式檔新增至檔案清單。 如果您的應用程式包含多個可執行檔，請從 [**檔案類型**] 下拉式清單中選取 [**進入點**]，將此部署的主要可執行檔標記為啟動應用程式。  (如果您的應用程式只包含一個可執行檔， *MageUI.exe* 會為您標示。 ) 

12. 選取 [ **必要許可權** ] 索引標籤，然後選取您需要應用程式判斷提示的信任層級。 預設為 **完全信任**，適用于大部分的應用程式。

13. 從 **功能表選取 [** 檔案]、[ **儲存** ]，然後儲存應用程式資訊清單。 當您儲存應用程式資訊清單時，系統會提示您簽署應用程式資訊清單。

14. 如果您的憑證儲存為檔案系統上的檔案，請使用 [ **簽署憑證** 檔案] 選項，然後使用省略號 (**...**) 按鈕，從檔案系統中選取憑證。

     -或-

     如果您的憑證保留在可從電腦存取的憑證存放區中，請選取 [ **使用預存憑證簽署] 選項**，然後從提供的清單中選取憑證。

15. 從 **功能表選取 [** 檔案]、[ **新增**]、[ **部署資訊清單** ] 以建立部署資訊清單，然後在 [ **名稱** ] 索引標籤上，提供此範例)  (**1.0.0.0** 的名稱和版本號碼。

16. 切換至 [ **更新** ] 索引標籤，並指定您想要此應用程式更新的頻率。 如果您的應用程式使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署 API 來檢查更新本身，請清除標示 [ **此應用程式應該檢查更新**] 的核取方塊。

17. 切換至 [ **應用程式參考** ] 索引標籤。您可以按一下 [ **選取資訊清單** ] 按鈕，然後選取您在先前步驟中建立的應用程式資訊清單，預先填入此索引標籤上的所有值。

18. 選擇 [ **儲存** ]，並將部署資訊清單儲存至磁片。 當您儲存應用程式資訊清單時，系統會提示您簽署應用程式資訊清單。 按一下 [ **取消** ] 以儲存資訊清單，而不加以簽署。

19. 將所有應用程式檔提供給客戶。

20. 此時，客戶必須使用自己本身產生的憑證來簽署部署資訊清單。 例如，如果客戶任職于名為「艾德公司」的公司，他可以使用 *MakeCert.exe* 工具產生自我簽署憑證。 接下來，使用 *Pvk2pfx.exe* 工具，將 *MakeCert.exe* 所建立的檔案結合成可傳遞至 *MageUI.exe* 的 PFX 檔案。

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. 在產生憑證之後，客戶現在會在 *MageUI.exe* 中開啟部署資訊清單，然後加以儲存，以簽署部署資訊清單。 當 [簽署] 對話方塊出現時，客戶會選取 [ **簽署為憑證** 檔案] 選項，然後選擇他已儲存在磁片上的 PFX 檔案。

22. 客戶將應用程式部署到其使用者。

## <a name="see-also"></a>另請參閱
- [Mage.exe (資訊清單產生和編輯工具) ](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (資訊清單產生和編輯工具、圖形用戶端) ](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [MakeCert](/windows/desktop/SecCrypto/makecert)
