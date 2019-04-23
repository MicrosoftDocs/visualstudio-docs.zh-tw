---
title: 逐步解說：手動部署 ClickOnce 應用程式不需要重新簽署而且會保留商標資訊 |Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 773a9f5a990b3432484c1ff13012b173c9fac1cb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076220"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>逐步解說：手動部署 ClickOnce 應用程式，而無須重新簽署而且會保留商標資訊
當您建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式並再將它提供給客戶發行並部署，客戶有以往都會需要更新部署資訊清單，並重新簽署資訊清單。 同時，仍然是慣用的方法，在大部分情況下，.NET Framework 3.5 可讓您建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]客戶可以部署而不需要重新產生新的部署資訊清單的部署。 如需詳細資訊，請參閱 <<c0> [ 部署 ClickOnce 應用程式，但不重新簽署的測試和生產環境伺服器](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)。

 當您建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式，然後將它交給客戶來發佈和部署，應用程式可以使用客戶的商標或保留您的品牌。 比方說，如果應用程式是單一的專屬應用程式，您可能想要保留您的品牌。 如果應用程式高度自訂的每個客戶中，您可能想要使用客戶的商標。 .NET Framework 3.5 可讓您保留您的品牌、 發行者資訊和安全性簽章，當您為組織部署的應用程式。 如需詳細資訊，請參閱 <<c0> [ 建立 ClickOnce 應用程式供其他人部署](../deployment/creating-clickonce-applications-for-others-to-deploy.md)。

> [!NOTE]
>  在此逐步解說中您建立部署以手動方式使用其中一種命令列工具*Mage.exe*或圖形化工具*MageUI.exe*。 如需有關手動部署的詳細資訊，請參閱[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。

## <a name="prerequisites"></a>必要條件
 若要執行本逐步解說中的步驟您需要下列項目：

- 您準備好要部署在 Windows Forms 應用程式。 此應用程式會稱為*WindowsFormsApp1*。

- Visual Studio 或 Windows SDK。

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>若要部署 ClickOnce 應用程式與多個部署使用 Mage.exe 的品牌支援

1. 開啟 Visual Studio 命令提示字元或[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]命令提示字元，並切換至目錄，您將在其中儲存您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]檔案。

2. 建立名為目前的版本，您的部署。 如果這是您要部署應用程式的第一次，您可能會選擇**1.0.0.0**。

   > [!NOTE]
   >  您部署的版本可能不同於您的應用程式檔案的版本。

3. 建立名為子目錄**bin**並複製所有的應用程式檔案，包括可執行檔、 組件、 資源和資料檔案。

4. 產生應用程式資訊清單，Mage.exe 呼叫。

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. 登入您的數位簽名的應用程式資訊清單。

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. 產生部署資訊清單，藉由呼叫*Mage.exe*。 根據預設， *Mage.exe*會將標示您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署安裝的應用程式，讓它可以執行同時上線與離線狀態。 若要讓應用程式可用，只有當使用者在線上時，使用`-i`引數的值與`f`。 此應用程式會利用多個部署功能，因為排除`-providerUrl`引數*Mage.exe*。 (在舊版.NET Framework 3.5 版之前，不包括`-providerUrl`離線應用程式將會導致錯誤。)

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. 未簽署部署資訊清單。

8. 提供的所有檔案提供給客戶，將部署自己的網路上的應用程式。

9. 到目前為止，客戶必須簽署部署資訊清單，使用自己自我產生的憑證。 例如，如果客戶適用於名為 Adventure Works 的公司，他可以產生自我簽署的憑證，使用*MakeCert.exe*工具。 接下來，使用*Pvk2pfx.exe*工具，以結合所建立的檔案*MakeCert.exe*成 PFX 檔案，可以傳遞給*Mage.exe*。

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. 接下來，客戶會使用此憑證來簽署部署資訊清單。

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. 在部署應用程式給使用者。

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>若要部署 ClickOnce 應用程式與多個部署使用 MageUI.exe 的品牌支援

1. 開啟 Visual Studio 命令提示字元或[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]命令提示字元，並瀏覽至目錄，您將在其中儲存您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]檔案。

2. 建立名為子目錄**bin**並複製所有的應用程式檔案，包括可執行檔、 組件、 資源和資料檔案。

3. 建立目前的部署版本命名的子目錄。 如果這是您要部署應用程式的第一次，您可能會選擇**1.0.0.0**。

   > [!NOTE]
   >  您部署的版本可能不同於您的應用程式檔案的版本。

4. 移動\\ **bin**目錄到您在步驟 2 中建立的目錄。

5. 啟動圖形化工具*MageUI.exe*。

   ```cmd
   MageUI.exe
   ```

6. 選取 建立新的應用程式資訊清單**檔案**，**新增**，**應用程式資訊清單**從功能表。

7. 預設值**名稱**索引標籤上，輸入此部署的名稱和版本號碼。 此外，提供一個值**發行者**，用來作為資料夾名稱，在 [開始] 功能表中的應用程式的快顯連結部署時。

8. 選取 **應用程式選項**索引標籤，然後按一下**使用應用程式資訊清單信任資訊**。 這會讓 淛鵸葺爦這個[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。

9. 選取 **檔案**索引標籤，然後按一下**瀏覽**旁**應用程式目錄**文字方塊。

10. 選取包含您在步驟 2 中建立的應用程式檔案的目錄，然後按一下**確定**上資料夾的 [選取項目] 對話方塊。

11. 按一下 [**填入**] 按鈕，將您所有的應用程式檔案新增至檔案清單。 如果您的應用程式包含一個以上的可執行檔，將此部署的啟動應用程式的主要可執行檔標記選取**進入點**從**檔案類型**下拉式清單。 (如果您的應用程式只包含一個可執行檔*MageUI.exe*會將它標示為您。)

12. 選取 **所需的權限**索引標籤，然後選取您需要您的應用程式，來判斷提示的信任層級。 預設值是**完全信任**，它會是適用於大部分的應用程式。

13. 選取 **檔案**，**儲存**從功能表中，並儲存應用程式資訊清單。 系統會提示您登入應用程式資訊清單，當您將它儲存。

14. 如果您有儲存為檔案系統上的檔案，請使用**簽章為憑證檔案**選項，然後選取 從檔案系統使用的省略符號 憑證 (**...**) 按鈕。

     -或-

     如果您的憑證會保存在可從您的電腦存取的憑證存放區中，選取**使用預存的憑證選項簽署**，並從提供的清單中選取的憑證。

15. 選取 **檔案**，**新增**，**部署資訊清單**從建立您的部署資訊清單中的功能表，然後按一下**名稱**索引標籤上，提供名稱和版本號碼 (**1.0.0.0**在此範例中)。

16. 若要切換**更新**索引標籤，然後指定您要更新此應用程式的頻率。 如果您的應用程式會使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署 API 來檢查更新檔本身，清除核取方塊**此應用程式應該檢查更新檔**。

17. 若要切換**應用程式參考**] 索引標籤。您可以按一下，預先填入的值，此索引標籤上的所有**選取資訊清單**上一個步驟中建立按鈕，然後選取 [應用程式資訊清單。

18. 選擇**儲存**並儲存到磁碟的部署資訊清單。 系統會提示您登入應用程式資訊清單，當您將它儲存。 按一下 **取消**儲存資訊清單，但不簽署。

19. 提供給客戶的所有應用程式的檔案。

20. 到目前為止，客戶必須簽署部署資訊清單，使用自己自我產生的憑證。 例如，如果客戶適用於名為 Adventure Works 的公司，他可以產生自我簽署的憑證，使用*MakeCert.exe*工具。 接下來，使用*Pvk2pfx.exe*工具，以結合所建立的檔案*MakeCert.exe*成 PFX 檔案，可以傳遞給*MageUI.exe*。

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. 使用產生的憑證，客戶現在簽署部署資訊清單開啟中的部署資訊清單*MageUI.exe*，並予以儲存。 [簽署] 對話方塊出現時，會選取客戶**簽章憑證檔為**選項，然後選擇他已儲存在磁碟的 PFX 檔案。

22. 在部署應用程式給使用者。

## <a name="see-also"></a>另請參閱
- [Mage.exe (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [MakeCert](/windows/desktop/SecCrypto/makecert)