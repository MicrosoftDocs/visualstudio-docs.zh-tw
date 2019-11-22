---
title: DSL 的 MSI 和 VSIX 部署 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4917fc81f439ef0185a753fb1c4c85e460eb7681
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297733"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL 的 MSI 和 VSIX 部署
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在自己的電腦或其他電腦上安裝特定領域語言。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 必須已安裝在目的電腦上。

## <a name="which"></a>在 VSIX 和 MSI 部署之間選擇
 部署特定領域語言的方法有兩種：

|方法|優點|
|------------|--------------|
|VSX （[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組）|非常容易部署：從 DslPackage 專案複製並執行 **.vsix**檔案。<br /><br /> 如需詳細資訊，請參閱[使用 VSX 安裝和卸載 DSL](#Installing)。|
|MSI （安裝程式檔案）|-允許使用者按兩下 DSL 檔案以開啟 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。<br />-將圖示與目的電腦中的 DSL 檔案類型產生關聯。<br />-將 XSD （XML 架構）與 DSL 檔案類型產生關聯。 這可避免在將檔案載入 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]時出現警告。<br /><br /> 您必須將安裝專案新增至您的解決方案，才能建立 MSI。<br /><br /> 如需詳細資訊，請參閱[使用 MSI 檔案部署 DSL](#msi)。|

## <a name="Installing"></a>使用 VSX 安裝和卸載 DSL
 當您使用此方法安裝 DSL 時，使用者可以從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中開啟 DSL 檔案，但無法從 Windows Explorer 開啟該檔案。

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>若要使用 VSX 安裝 DSL

1. 在您的電腦中，尋找您的 DSL 封裝專案所建立的 **.vsix**檔案。

    1. 在**方案總管**中，以滑鼠右鍵按一下**DslPackage**專案，然後按一下 [**在 Windows Explorer 中開啟資料夾**]。

    2. 找出 **\*\\yourproject。的 bin\\** **。DslPackage .vsix**

2. 將 .vsix 檔案複製到您要安裝 DSL 的目的電腦 **。** 這可以是您自己的電腦或另一部電腦。

    - 目的電腦必須具有在執行時間支援 Dsl 的其中一個 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 版本。 如需詳細資訊，請參閱[支援的 Visual Studio 版本 & 模型 SDK 的視覺效果](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)。

    - 目的電腦必須具有**DslPackage\source.extensions.manifest**中指定的其中一個 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 版本。

3. 在目的電腦上，按兩下 **.vsix**檔案。

     [Visual Studio 擴充功能安裝程式] 會隨即開啟並安裝擴充功能。

4. 啟動或重新啟動 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]。

5. 若要測試 DSL，請使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 建立新的檔案，該檔案具有您為 DSL 定義的副檔名。

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>卸載使用 VSX 安裝的 DSL

1. 在 [工具]功能表上，按一下 [擴充管理員]。

2. 展開 [已安裝的擴充功能]。

3. 選取用來定義 DSL 的延伸模組，然後按一下 [**卸載**]。

   在很少見的情況下，錯誤的擴充功能會無法載入，並且在錯誤視窗中建立報表，但不會顯示在擴充管理員中。 在此情況下，您可以藉由從下列位置刪除檔案來移除擴充功能：

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a>在 MSI 中部署 DSL
 藉由定義 DSL 的 MSI （Windows Installer）檔案，您可以允許使用者從 Windows Explorer 開啟 DSL 檔案。 您也可以將圖示和簡短描述與您的副檔名建立關聯。 此外，MSI 也可以安裝可用於驗證 DSL 檔案的 XSD。 如有需要，您可以將其他元件新增至將同時安裝的 MSI。

 如需 MSI 檔案和其他部署選項的詳細資訊，請參閱[部署應用程式、服務和元件](../deployment/deploying-applications-services-and-components.md)。

 若要建立 MSI，您可以將安裝專案新增至 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 解決方案。 建立安裝專案最簡單的方法是使用 CreateMsiSetupProject.tt 範本，您可以從[VMSDK 網站](https://go.microsoft.com/fwlink/?LinkID=186128)下載。

#### <a name="to-deploy-a-dsl-in-an-msi"></a>在 MSI 中部署 DSL

1. 在擴充功能資訊清單中設定 `InstalledByMsi`。 這可防止安裝和卸載 VSX （MSI 除外）。 如果您將在 MSI 中包含其他元件，這就很重要。

   1. 開啟 DslPackage\source.extension.tt

   2. 在 `<SupportedProducts>`之前插入下列這一行：

       ```
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. 建立或編輯會在 Windows Explorer 中代表您的 DSL 的圖示。 例如，編輯**DslPackage\Resources\File.ico**

3. 請確定 DSL 的下列屬性是正確的：

   - 在 DSL Explorer 中，按一下根節點，然後在 屬性視窗中，檢查：

       - 描述

       - 版本

   - 按一下 **編輯器** 節點，然後在 屬性視窗中，按一下 **圖示**。 設定值以參考**DslPackage\Resources**中的圖示檔，例如**file .ico**

   - 在 [**建立**] 功能表上，開啟 [ **Configuration Manager**]，然後選取您要建立的設定，例如 [**發行**] 或 [ **Debug**]。

4. 移至 [[視覺效果和模型 SDK](https://go.microsoft.com/fwlink/?LinkID=186128)] 首頁，然後從 [**下載**] 索引標籤下載**CreateMsiSetupProject.tt**。

5. 將**CreateMsiSetupProject.tt**新增至您的 Dsl 專案。

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 將會建立名為**CreateMsiSetupProject. vdproj**的檔案。

6. 在 Windows Explorer 中，將 Dsl\\*. vdproj 複製到名為 Setup 的新資料夾。

    （如有需要，您現在可以從 Dsl 專案中排除 CreateMsiSetupProject.tt）。

7. 在**方案總管**中，以現有專案的形式新增**安裝程式 \*\\vdproj** 。

8. 在 [**專案**] 功能表上，按一下 [專案相依性 **]** 。

    在 [**專案**相依性] 對話方塊中，選取 [安裝] 專案。

    選取 [ **DslPackage**] 旁的方塊。

9. 重建方案。

10. 在 Windows Explorer 中，于您的安裝專案中找出建立的 MSI 檔案。

     將 MSI 檔案複製到您要安裝 DSL 的電腦。 按兩下 MSI 檔案。 安裝程式會執行。

11. 在目的電腦中，建立副檔名為 DSL 的新檔案。 確認：

    - 在 Windows Explorer 清單視圖中，檔案會以您定義的圖示和描述顯示。

    - 當您按兩下該檔案時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會啟動，並在 DSL 編輯器中開啟 DSL 檔案。

    如果您想要的話，也可以手動建立安裝專案，而不是使用文字模板。 如需包含此程式的逐步解說，請參閱[視覺效果和模型化 SDK 實驗室](https://go.microsoft.com/fwlink/?LinkId=208878)的第5章。

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>卸載從 MSI 安裝的 DSL

1. 在 Windows 中，開啟 [**程式和功能**] 控制台。

2. 卸載 DSL。

3. 重新啟動 Visual Studio。
