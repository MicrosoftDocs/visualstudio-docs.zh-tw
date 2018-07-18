---
title: DSL 的 MSI 和 VSIX 部署
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ccd26814b8a6f06f896c661f2ca9eddb0de8a90d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31954580"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL 的 MSI 和 VSIX 部署
在您自己的電腦或其他電腦上，您可以安裝的網域特定定義域語言。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 已必須安裝在目標電腦上。

##  <a name="which"></a> VSIX 和 MSI 部署之間選擇
 有兩種方法部署的網域特定定義域語言：

|方法|優點|
|------------|--------------|
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]擴充功能)|非常容易部署： 複製並執行 **.vsix** DslPackage 專案檔案。<br /><br /> 如需詳細資訊，請參閱[安裝及解除安裝使用 VSX 的 DSL](#Installing)。|
|MSI （安裝程式檔案）|-可讓使用者開啟[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]按兩下 DSL 檔案。<br />-將在目標電腦的 DSL 檔案類型與關聯圖示。<br />-將 DSL 檔案類型與關聯的 XSD （XML 結構描述）。 這可避免警告時載入此檔案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。<br /><br /> 您必須安裝專案加入方案中，以便建立 MSI。<br /><br /> 如需詳細資訊，請參閱[使用 MSI 檔案部署 DSL](#msi)。|

##  <a name="Installing"></a> 安裝和解除安裝使用 VSX 的 DSL
 DSL 以此方式安裝時，使用者可以從開啟 DSL 檔案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，但無法從 Windows 檔案總管中開啟檔案。

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>若要使用 VSX 安裝 DSL

1.  在您的電腦，尋找 **.vsix** DSL 封裝專案所建置的檔案。

    1.  在**方案總管 中**，以滑鼠右鍵按一下**DslPackage**專案，然後再按一下**在 Windows 檔案總管 中開啟資料夾**。

    2.  找出檔案**bin\\\*\\***YourProject***。DslPackage.vsix**

2.  複製 **.vsix**檔案至您要安裝 DSL 的目標電腦。 這可以是您自己的電腦或另一部電腦。

    -   目標電腦必須有其中一個版本[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]Dsl 支援在執行階段。 如需詳細資訊，請參閱[的 Visualization & Modeling SDK 支援 Visual Studio 版本](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)。

    -   目標電腦必須有其中一個版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中所指定**DslPackage\source.extensions.manifest**。

3.  在目標電腦上按兩下 **.vsix**檔案。

     [Visual Studio 擴充功能安裝程式] 會隨即開啟並安裝擴充功能。

4.  啟動或重新啟動 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。

5.  若要測試 DSL，使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]建立新的檔案副檔名為 DSL 定義。

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>若要解除安裝使用 VSX 所安裝的 DSL

1.  在**工具**功能表上，按一下 **擴充管理員**。

2.  展開 [已安裝的擴充功能] 。

3.  選取擴充功能中定義的是 DSL，然後按一下 **解除安裝**。

 在很少見的情況下，故障的擴充功能無法載入並且會在錯誤視窗中建立報告，但不會顯示在擴充管理員中。 在此情況下，您可以藉由從下列位置刪除檔案來移除擴充功能：

 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

##  <a name="msi"></a> 部署在 MSI DSL
 DSL 定義 MSI (Windows Installer) 檔案，您可以允許使用者從 Windows 檔案總管開啟 DSL 檔案。 您也可以與您的檔案名稱副檔名關聯的圖示和簡短描述。 此外，MSI 可以安裝可以用來驗證 DSL 檔 XSD。 如果您想，您可以新增到將會安裝在同一時間 MSI 的其他元件。

 如需 MSI 檔案和其他部署選項的詳細資訊，請參閱[部署應用程式、 服務和元件](../deployment/deploying-applications-services-and-components.md)。

 若要建置 MSI，您加入安裝專案中的加入您[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]方案。 建立安裝專案的最簡單的方法是使用 CreateMsiSetupProject.tt 範本，您可以從下載[VMSDK 網站](http://go.microsoft.com/fwlink/?LinkID=186128)。

#### <a name="to-deploy-a-dsl-in-an-msi"></a>若要部署的 DSL MSI 中

1.  設定`InstalledByMsi`擴充功能資訊清單中。 這會讓 VSX 安裝和解除安裝 MSI 除外。 這很重要，如果您將會包含其他元件在 MSI。

    1.  開啟 DslPackage\source.extension.tt

    2.  插入下列這行之前`<SupportedProducts>`:

        ```
        <InstalledByMsi>true</InstalledByMsi>
        ```

2.  建立或編輯圖示表示在 Windows 檔案總管 DSL。 例如，編輯**DslPackage\Resources\File.ico**

3.  請確定正確的 DSL 的下列屬性：

    -   DSL 總管 中按一下根節點，然後在 屬性 視窗中，檢閱：

        -   描述

        -   版本

    -   按一下**編輯器**節點在 [屬性] 視窗中按一下**圖示**。 將值設為參考中的圖示檔案**DslPackage\Resources**，例如**File.ico**

    -   在**建置**功能表中，開啟**Configuration Manager**，再選取您想要建立這類組態**發行**或**偵錯**.

4.  移至[Visualization and Modeling SDK 首頁](http://go.microsoft.com/fwlink/?LinkID=186128)，以及從**下載**索引標籤上，下載**CreateMsiSetupProject.tt**。

5.  新增**CreateMsiSetupProject.tt** Dsl 專案。

     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 將會建立名為**CreateMsiSetupProject.vdproj**。

6.  在 Windows 檔案總管中，複製 Dsl\\*.vdproj 到新的資料夾，名為 「 安裝程式。

     （如果您想，您可以現在 CreateMsiSetupProject.tt 從專案中排除 Dsl。）

7.  在**方案總管 中**，新增**安裝\\\*.vdproj**做為現有的專案。

8.  在**專案**功能表上，按一下 **專案相依性**。

     在**專案相依性**對話方塊方塊中，選取 安裝專案。

     選取方塊旁的  **DslPackage**。

9. 重建方案。

10. 在 Windows 檔案總管 中，找出安裝專案中的內建的 MSI 檔案。

     將 MSI 檔案複製到您要安裝 DSL 的電腦。 按兩下 MSI 檔案。 安裝程式會執行。

11. 在目標電腦上，建立新的檔案有 DSL 的副檔名。 確認：

    -   在 Windows 檔案總管 清單檢視中，檔案會顯示圖示和您所定義的描述。

    -   當您按兩下該檔案，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]正常啟動，且在 DSL 編輯器中開啟 DSL 檔案。

 如果您想要的話，您可以在手動，而不是使用文字範本中建立安裝專案。 如需逐步解說，其中包含此程序，請參閱第 5 章的[Visualization and Modeling SDK 實驗室](http://go.microsoft.com/fwlink/?LinkId=208878)。

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>若要解除安裝的 MSI 安裝的 DSL

1.  在 Windows 中，開啟**程式和功能**控制台。

2.  解除安裝 DSL。

3.  重新啟動 Visual Studio。