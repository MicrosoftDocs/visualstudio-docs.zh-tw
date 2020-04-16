---
title: 安裝 Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 04/15/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bfc573c30281e5bc976ee25ea3a80a2f874ab25
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445073"
---
# <a name="install-visual-studio-2015"></a>安裝 Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此頁面包含可協助您安裝 **Visual Studio 2015** 的詳細資訊，Visual Studio 2015 是適用於開發人員的生產力工具整合式套件。 我們還提供了連結,可快速獲取有關[功能](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history)、[系統要求](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs)、[下載](https://visualstudio.microsoft.com/vs/older-downloads/)等的資訊。

## <a name="quick-links"></a>快速連結

在我們深入了解詳細資料之前，以下是最常使用的連結清單。

|||
|------------------|----------------|
|![下載 Visual Studio](../install/media/downloads.png "下載") |**下載**:要安裝 Visual Studio 2015,可以從[My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)頁面下載產品可執行檔(需要訂閱),或使用盒裝產品的安裝媒體。 [詳細瞭解如何下載目前或以前的 Visual Studio 版本](https://www.visualstudio.com/vs/older-downloads/)。|
|![瞭解有關功能的更多](../install/media/features.png "特性") |**功能**: 要瞭解有關 Visual Studio 2015 中功能的詳細資訊,請參閱[RTM、](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs)[更新 1、](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs)[更新 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)和更新[3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs)的發行說明。|
|![檢視系統要求](../install/media/system-requirements.png "系統需求") |**系統要求**:要查看每個版本的 Visual Studio 2015 的系統要求,請參閱[Visual Studio 2015 平臺定位和相容性](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)頁面。|
|![找到您的產品金鑰](../install/media/product-keys.png "產品金鑰") |**產品金鑰**:要查找產品密鑰,請參閱["如何操作:尋找可視化工作室產品金鑰"](../install/how-to-locate-the-visual-studio-product-key.md)主題。|
|![瞭解許可](../install/media/licensing.png "授權") |**許可**:要瞭解個人或企業客戶的許可選項,請參閱[Visual Studio 2015 許可白皮書](https://www.microsoft.com/download/details.aspx?id=13350)。|

## <a name="default-vs-custom-setup"></a><a name="custom"></a>預設設定與自訂設定
 當您安裝 Visual Studio 2015 時，您可以包含或排除您日常使用的元件。 這表示預設安裝通常會比自訂安裝更小，而且安裝速度更快。 這也意謂著在舊版中許多預設安裝的元件，在此版本中已改為您必須明確選取的「自訂」元件。

 ![Visual Studio 2015 的 [安裝] 對話方塊](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 自定義元件包括可視C++、可視 F#、SQL Server 資料工具、跨平台行動工具和 SDK 以及第三方 SDK 和擴展。 如果您沒有在初始安裝期間選取任何自訂元件，仍可於稍後安裝。

> [!NOTE]
> 自訂安裝會自動包含預設安裝中的元件。

 自訂元件的完整清單如下所示：

|功能集|元件|
|------------------|----------------|
|**更新**|Visual Studio 2015 Update 3|
|**程式設計語言**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Windows 和 Web 開發**|ClickOnce 發行工具<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Microsoft Web 開發人員工具<br />視覺工作室的 PowerShell 工具(第三方)<br />Silverlight 開發套件<br />通用 Windows App 開發工具<br />Windows 10 工具和 SDK<br />Windows 8.1 和 Windows Phone 8.0 工具<br />Windows 8.1 工具和 SDK|
|**跨平台行動開發**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />適用於 iOS / Android 的 Visual C++ 行動開發<br />Clang with Microsoft CodeGen|
|**通用工具與軟體開發工具套件**|Android 原生開發工具套件(第三方)<br /> 安卓 SDK [第三方]<br />Android SDK 設定 API(第三方)<br />阿帕奇螞蟻(第三方)<br /> Java SE 開發工具套件(第三方)<br /> Joyent Node.js (第三方)|
|**通用工具**|Windows 的 Git(第三方)<br />Visual Studio 的 GitHub 延伸(第三方)<br /> Visual Studio 擴充性工具|

## <a name="install-visual-studio"></a><a name="installing"></a>安裝視覺化工作室
 您可以使用安裝媒體 (DVD)安裝 Visual Studio),使用[My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)網站中的 Visual Studio 訂閱服務、從[Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/)網站下載 Web 安裝程式或創建離機安裝佈局(有關詳細資訊,請參閱[創建視覺化工作室的離線安裝](../install/create-an-offline-installation-of-visual-studio.md)頁面)。

> [!IMPORTANT]
> 您必須擁有系統管理員認證才能安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 不過，在安裝之後，您不需要它們也可使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。

 您的本機系統管理員帳戶必須啟用下列權限，才能安裝 Visual Studio 中的所有項目。

|本機原則物件的顯示名稱|使用者權限|
|--------------------------------------|----------------|
|備份檔案和目錄|SeBackupPrivilege|
|偵錯程式|SeDebugPrivilege|
|管理稽核和安全性記錄檔|SeSecurityPrivilege|

 如需本機系統管理員帳戶需求的詳細資訊，請參閱知識庫文件 [如果安裝帳戶並沒有特定使用者權限，SQL Server 安裝會失敗](https://support.microsoft.com/kb/2000257)。

### <a name="use-installation-media"></a><a name="BKMK_Media"></a>使用安裝媒體
 若要安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，請在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 安裝媒體的根目錄中，針對您想要的版本來執行安裝檔案：

|版本|安裝檔案|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a>從產品網站下載
 造[訪 視覺化工作室下載](https://visualstudio.microsoft.com/vs/older-downloads/)頁面,並選擇您想要的可視化工作室版本。

### <a name="download-from-your-subscription-service"></a>從訂閱服務下載
 訪問[My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)頁面,並選擇您想要的可視化工作室版本。

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a>建立離線安裝佈局
 如果您沒有[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]安裝媒體,或者沒有 Visual Studio 訂閱,或者您不想使用 Web[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]安裝程式進行安裝 ,則可以透過建立所謂的離線安裝佈局來執行「斷開連接」安裝。 有關詳細資訊,請參閱[創建可視化工作室的脫機安裝](../install/create-an-offline-installation-of-visual-studio.md)頁面。

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a>在企業中部署視覺化工作室
 有關如何通過網路進行部署[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的資訊,請參閱[可視化工作室管理員指南](../install/visual-studio-administrator-guide.md)。

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a>在虛擬化環境中安裝視覺化工作室
 **HYPER-V 的視訊問題**

 如果 Windows Server 2008 R2 是在啟用 Hyper-V 的情況下使用加速圖形卡來執行，您可能會感受到系統速度變慢。

 有關詳細資訊,請參閱[Windows 伺服器 2008 或基於 Windows Server 2008 R2 的電腦啟用了 Hyper-V 角色並安裝了加速顯示配接器時的影片性能可能會降低](https://support.microsoft.com/kb/961661)。

 **使用 HYPER-V 模擬裝置**

 當您在實際的硬體上安裝 Visual Studio 2015，但沒有虛擬化時，您可以使用 HYPER-V 選擇能模擬 Windows 和 Android 裝置的功能。 當您安裝到 HYPER-V 時，將無法模擬 Windows 或 Android 裝置。 這是因為模擬器本身是虛擬機器，您目前不能在另一個 VM 內裝載 VM。 因應措施是使用實際的 Windows 或 Android 裝置，您可以直接在上面部署和偵錯應用程式。

## <a name="install-optional-components"></a><a name="optionalComponents"></a>安裝選擇元件
 如果要安裝在原始安裝期間可能未選擇的元件,請使用以下步驟。

#### <a name="to-install-optional-components"></a>安裝選擇元件

1. 在 [控制台] **** 的 [程式和功能] **** 頁面上，選擇要在其中加入一個或多個元件的產品版本，然後選擇 [變更] ****。

2. 在安裝精靈中，選擇 [修改] ****，然後選擇您要安裝的元件。

3. 選擇 [下一步] ****，然後依照其餘指示進行。

## <a name="install-offline-help-content"></a><a name="helpContent"></a>安裝離線說明內容
 安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]之後，您可以下載其他的說明內容，以便可以離線使用。

#### <a name="to-install-or-uninstall-help-content"></a>安裝或解除安裝說明內容

1. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 功能表列上，依序選擇 [說明] ****、[加入和移除說明內容] ****。

2. 在 [Microsoft 說明檢視器] **** 的 [管理內容] **** 索引標籤上，選取適用於您說明內容的安裝來源。

3. 如果您要尋找特定的說明集合，請在 [搜尋]**** 文字方塊中輸入名稱或關鍵字，然後按 **Enter**。

4. 在您想要的說明集合名稱旁邊，選擇 [加入] **** 或 [移除] **** 連結。

5. 按下 **「更新**」按鈕。

   有關如何安裝或部署離線說明的詳細資訊,請參閱[說明檢視器管理員指南](../ide/help-viewer-administrator-guide.md)。

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a>檢查服務版本和產品更新
 因為並非所有延伸模組都相容，從舊版升級時，Visual Studio 不會自動升級延伸模組。 您必須從[可視化工作室應用商店](https://marketplace.visualstudio.com/)或軟體發行者重新安裝擴展。

#### <a name="to-automatically-check-for-service-releases"></a>自動檢查版本更新服務

1. 在功能表列上選擇 [工具] ****、[選項] ****。

2. 在 [選項] **** 對話方塊中，展開 [環境] ****，然後選取 [擴充功能和更新] ****。 確定已選取 [自動檢查更新] **** 核取方塊，然後選擇 [確定] ****。

## <a name="register-visual-studio"></a>註冊視覺工作室

1. 在功能表列上，選取 [說明] ****、[關於] ****。

     [關於] **** 對話方塊會顯示產品識別碼 (PID)。 您將需要 PID 和 Windows 帳戶認證 (例如 Hotmail 或 Outlook.com 電子郵件地址和密碼) 以註冊產品。

2. 在功能表列上，選擇 [說明] ****、[註冊產品] ****。

## <a name="repair-visual-studio"></a><a name="repair"></a>修復視覺工作室

#### <a name="to-repair-visual-studio"></a>若要修復 Visual Studio

1. 在 [控制台] **** 的 [程式和功能] **** 頁面上，選取要修復的產品版本，然後選擇 [變更] ****。

2. 在安裝精靈中，依序選擇 [修復] ****、[下一步] ****，然後依照其餘指示進行。

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>以靜音或被動模式修復 Visual Studio(即從源進行修復)

1. 在安裝 Visual Studio 的電腦上，開啟 Windows 命令提示字元。

2. 輸入下列參數：

     *DVDRoot*\\<*安裝檔案*\>\<>`norestart` `/quiet|/passive` [/ ]`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a>排除安裝故障
 請使用下列資源來取得設定及安裝問題的協助：

- [Visual Studio 安裝程式和安裝](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) 論壇。 在 Visual Studio 社群中，檢閱其他人提供的問題和解答。 如果您找不到所需的資訊，請詢問您自己的問題。

- [取得有關視覺工作室的説明](https://visualstudio.microsoft.com/vs/support/vs2015/)。 查找知識庫 (KB) 文章,瞭解如何聯繫 Microsoft 支援部門,瞭解有關 Visual Studio 安裝問題的資訊。

## <a name="related-topics"></a><a name="relatedTopics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[建立視覺化工作室的離線安裝](../install/create-an-offline-installation-of-visual-studio.md)|描述如何在未連接到 Internet 時安裝 Visual Studio。
|[並排安裝視覺化工作室版本](../install/install-visual-studio-versions-side-by-side.md)|提供如何在同一部電腦上安裝多個 Visual Studio 版本的相關資訊。|
|[使用命令列參數安裝視覺化工作室](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|列出從命令提示符安裝 Visual Studio 時可以使用的命令列參數。|
|[解除安裝 Visual Studio](../install/uninstall-visual-studio.md)|描述如何卸載可視化工作室。|
|[視覺工作室管理員指南](../install/visual-studio-administrator-guide.md)|提供 Visual Studio 部署選項的相關資訊。|
|[視覺工作室影像庫](../designers/the-visual-studio-image-library.md)|提供如何安裝可在 Visual Studio 應用程式中使用之圖形的相關資訊。|
|[開始使用視覺化工作室進行開發](../ide/get-started-developing-with-visual-studio.md)|包含可説明您更有效地使用可視化工作室的資訊和連結。|

## <a name="see-also"></a>另請參閱

- [登入 Visual Studio](../ide/signing-in-to-visual-studio.md)
