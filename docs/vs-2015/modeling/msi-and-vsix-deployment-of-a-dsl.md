---
title: MSI 和 VSIX 部署的 DSL |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3aaaf704e1ad8880ef7768ef9d7a23d325882a15
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094434"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL 的 MSI 和 VSIX 部署
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以安裝特定領域語言，在您自己的電腦或其他電腦上。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 已必須安裝在目標電腦上。  
  
## <a name="which"></a> VSIX 和 MSI 部署之間進行選擇  
 有兩種方法部署特定領域語言：  
  
|方法|優點|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../includes/vsprvs-md.md)]延伸模組)|非常容易部署：複製並執行 **.vsix** DslPackage 專案中的檔案。<br /><br /> 如需詳細資訊，請參閱[安裝和解除安裝 DSL 使用 VSX](#Installing)。|  
|MSI （安裝程式檔案）|-允許使用者開啟[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]按兩下 DSL 檔案。<br />-建立與目標電腦中的 DSL 檔案類型關聯圖示。<br />-將與 DSL 檔案類型關聯的 XSD （XML 結構描述）。 載入檔案時，這會避免警告[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。<br /><br /> 您必須將安裝專案加入方案以建立 MSI。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 使用 MSI 檔案部署 DSL](#msi)。|  
  
## <a name="Installing"></a> 安裝及解除安裝使用 VSX 的 DSL  
 這個方法所安裝 DSL 時，使用者可以開啟 DSL 檔案從[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，但無法從 Windows 檔案總管中開啟檔案。  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>若要使用的 VSX 安裝 DSL  
  
1. 在您的電腦，尋找 **.vsix** DSL 封裝專案所建置的檔案。  
  
    1. 在 **方案總管**，以滑鼠右鍵按一下**DslPackage**專案，然後再按一下**在 Windows 檔案總管中開啟資料夾**。  
  
    2. 找出檔案**筒\\\*\\**_YourProject_**。DslPackage.vsix**  
  
2. 複製 **.vsix**檔案至您要安裝 DSL 的目標電腦。 這可以是您自己的電腦或另一部電腦。  
  
    - 目標電腦必須具有其中一個版本[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]Dsl 支援在執行階段。 如需詳細資訊，請參閱 < [Visualization & Modeling SDK 支援 Visual Studio 版本](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)。  
  
    - 目標電腦必須具有其中一個版本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中指定**DslPackage\source.extensions.manifest**。  
  
3. 目標電腦上，按兩下 **.vsix**檔案。  
  
     [Visual Studio 擴充功能安裝程式] 會隨即開啟並安裝擴充功能。  
  
4. 啟動或重新啟動 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]。  
  
5. 若要測試 DSL，請使用[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]來建立新的檔案定義 DSL 的副檔名。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>若要解除安裝使用 VSX 所安裝的 DSL  
  
1. 在 **工具**功能表上，按一下**延伸模組管理員**。  
  
2. 展開 [已安裝的擴充功能] 。  
  
3. 選取擴充功能，在其中定義 DSL，然後按一下 **解除安裝**。  
  
   在很少見的情況下，故障的擴充功能無法載入並且會在錯誤視窗中建立報告，但不會顯示在擴充管理員中。 在此情況下，您可以藉由從下列位置刪除檔案來移除擴充功能：  
  
   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
## <a name="msi"></a> 部署 MSI 中的 DSL  
 藉由定義您的 dsl 的 MSI (Windows Installer) 檔案，您可以允許使用者從 Windows 檔案總管開啟 DSL 檔案。 您也可以將圖示和簡短描述您的副檔名。 此外，MSI 可以安裝可用於驗證 DSL 檔案的 XSD。 如果您想，您可以將其他元件新增到將會安裝在同一時間 MSI。  
  
 如需有關 MSI 檔案和其他部署選項的詳細資訊，請參閱[部署應用程式、 服務和元件](../deployment/deploying-applications-services-and-components.md)。  
  
 若要建立 MSI，您會新增安裝專案，以您[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]解決方案。 建立安裝專案的最簡單方法是使用 CreateMsiSetupProject.tt 範本中，您可以從下載[VMSDK 網站](http://go.microsoft.com/fwlink/?LinkID=186128)。  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>若要部署 MSI 中的 DSL  
  
1. 設定`InstalledByMsi`延伸模組資訊清單中。 這會讓 VSX 安裝和解除安裝 MSI 除外。 這很重要，如果您將會包含 MSI 中的其他元件。  
  
   1. 開啟 DslPackage\source.extension.tt  
  
   2. 插入下的面這一行之前`<SupportedProducts>`:  
  
       ```  
       <InstalledByMsi>true</InstalledByMsi>  
       ```  
  
2. 建立或編輯圖示，以代表您在 Windows 檔案總管中的 DSL。 例如，編輯**DslPackage\Resources\File.ico**  
  
3. 請確定您的 DSL 的下列屬性正確無誤：  
  
   - DSL 總管 中按一下 根 節點中，然後在 屬性 視窗中，檢閱：  
  
       - 描述  
  
       - 版本  
  
   - 按一下 **編輯器**節點，在 屬性 視窗中，按一下**圖示**。 將值設為參考中的圖示檔案**DslPackage\Resources**，例如**File.ico**  
  
   - 上**建置**功能表中，開啟**Configuration Manager**，然後選取您想要建置的例如組態**版本**或**偵錯**.  
  
4. 移至[Visualization and Modeling SDK 首頁](http://go.microsoft.com/fwlink/?LinkID=186128)，以及從**下載**索引標籤上，下載**CreateMsiSetupProject.tt**。  
  
5. 新增**CreateMsiSetupProject.tt**至您的 Dsl 專案。  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會建立名為**CreateMsiSetupProject.vdproj**。  
  
6. 在 Windows 檔案總管中，複製 Dsl\\*.vdproj 到新的資料夾，名為 「 安裝程式。  
  
    （如果您想，您現在可以排除 CreateMsiSetupProject.tt 從您的 Dsl 專案。）  
  
7. 在 [**方案總管] 中**，新增**安裝程式\\\*.vdproj**為現有的專案。  
  
8. 在 **專案**功能表上，按一下**專案相依性**。  
  
    在 **專案相依性**對話方塊方塊中，選取 安裝專案。  
  
    選取方塊旁**DslPackage**。  
  
9. 重建方案。  
  
10. 在 Windows 檔案總管中，找出內建的 MSI 檔案安裝專案中。  
  
     將 MSI 檔案複製到您想要安裝 DSL 時所在的電腦。 按兩下 MSI 檔案。 執行安裝程式。  
  
11. 在目標電腦，建立新的檔案具有您 DSL 的副檔名。 確認：  
  
    - 在 Windows 檔案總管 清單檢視中，檔案會顯示圖示和您所定義的描述。  
  
    - 當您按兩下檔案，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]啟動，並以您的 DSL 編輯器開啟 DSL 檔案。  
  
    如果您想，您可以在以手動的方式，而不是使用文字範本中建立安裝專案。 如需逐步解說，其中包含此程序，請參閱第 5 章的[Visualization and Modeling SDK 實驗室](http://go.microsoft.com/fwlink/?LinkId=208878)。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>若要解除安裝已從 MSI 安裝 DSL  
  
1. 在 Windows 中，開啟**程式和功能**控制台。  
  
2. 解除安裝 DSL。  
  
3. 重新啟動 Visual Studio。
