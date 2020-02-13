---
title: 安裝 Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: dc84fc135e59a43a05ce66186c4a44e9e31f8f2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851043"
---
# <a name="install-visual-studio-2015"></a>安裝 Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此頁面包含可協助您安裝 **Visual Studio 2015** 的詳細資訊，Visual Studio 2015 是適用於開發人員的生產力工具整合式套件。 其中也包含連結，協助您快速取得 [功能](https://www.visualstudio.com/news/vs2015-vs.aspx)、 [版本](https://visualstudio.microsoft.com/en-US/products/compare-visual-studio-products-vs)、 [系統需求](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)、 [下載](https://visualstudio.microsoft.com/downloads/)，以及其他項目的詳細資訊。

## <a name="quick-links"></a>快速連結

在我們深入了解詳細資料之前，以下是最常使用的連結清單。

|||
|------------------|----------------|
|![下載 Visual Studio](../install/media/downloads.png "下載") |**下載**：若要安裝 Visual Studio 2015，您可以從 [ [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) ] 頁面（需要訂用帳戶）下載產品可執行檔，或使用盒裝產品的安裝媒體。 [深入瞭解如何下載目前或舊版的 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)。|
|![深入瞭解功能](../install/media/features.png "功能") |**功能**：若要深入瞭解 Visual Studio 2015 中的功能，請參閱[RTM](https://www.visualstudio.com/news/vs2015-vs)、 [update 1](https://www.visualstudio.com/news/vs2015-update1-vs)、 [update 2](https://www.visualstudio.com/news/vs2015-update2-vs)和[update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs)的版本資訊。|
|![瞭解每個 SKU 的內容](../install/media/sku.png "SKU") |**SKU**：若要了解每一個版本的 Visual Studio 2015 有哪些可用功能，請參閱 [Compare Visual Studio Offerings](https://visualstudio.microsoft.com/en-US/products/compare-visual-studio-products-vs) (比較 Visual Studio 供應項目) 頁面。|
|![查看系統需求](../install/media/system-requirements.png "系統需求") |**系統需求**：若要查看每個版本 Visual Studio 2015 的系統需求，請參閱[Visual Studio 2015 相容性](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)頁面。|
|![找出您的產品金鑰](../install/media/product-keys.png "產品金鑰") |**產品金鑰**：若要尋找您的產品金鑰，請參閱[如何：找出 Visual Studio 產品金鑰](../install/how-to-locate-the-visual-studio-product-key.md)主題。|
|![瞭解授權](../install/media/licensing.png "授權") |**授權**：若要瞭解個人或企業客戶的授權選項，請參閱[Visual Studio 和 MSDN 授權](https://www.microsoft.com/download/details.aspx?id=13350)技術白皮書。|

## <a name="custom"></a>預設值與自訂設定
 當您安裝 Visual Studio 2015 時，您可以包含或排除您日常使用的元件。 這表示預設安裝通常會比自訂安裝更小，而且安裝速度更快。 這也意謂著在舊版中許多預設安裝的元件，在此版本中已改為您必須明確選取的「自訂」元件。

 ![Visual Studio 2015 安裝程式對話方塊](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 自訂元件包括 Visual C++、Visual F#、SQL Server Data Tools、跨平台行動工具和 SDK 以及協力廠商 SDK 和擴充功能。 如果您沒有在初始安裝期間選取任何自訂元件，仍可於稍後安裝。

> [!NOTE]
> 自訂安裝會自動包含預設安裝中的元件。

 自訂元件的完整清單如下所示：

|功能集|元件|
|------------------|----------------|
|**更新**|Visual Studio 2015 Update 3|
|**程式語言**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Windows 和 Web 開發**|ClickOnce 發行工具<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Microsoft Web Developer Tools<br />PowerShell Tools for Visual Studio （協力廠商）<br />Silverlight 開發套件<br />通用 Windows 應用程式開發工具<br />Windows 10 工具和 SDK<br />Windows 8.1 及 Windows Phone 8.0/8.1 工具<br />Windows 8.1 工具和 SDK|
|**跨平台行動開發**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />適用於 iOS / Android 的 Visual C++ 行動開發<br />Clang with Microsoft CodeGen|
|**一般工具和軟體發展工具組**|Android 原生開發工具組（協力廠商）<br /> Android SDK [協力廠商]<br />Android SDK 安裝程式 Api （協力廠商）<br />Apache Ant （協力廠商）<br /> JAVA SE 開發套件（協力廠商）<br /> Joyent node.js （協力廠商）|
|**通用工具**|適用于 Windows 的 Git （協力廠商）<br />適用于 Visual Studio 的 GitHub 延伸模組（協力廠商）<br /> Visual Studio 擴充性工具|

## <a name="installing"></a> 安裝 Visual Studio
 您可以使用安裝媒體（Dvd）來安裝 Visual Studio、從[My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)網站使用您的 Visual Studio 訂閱服務、從[Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)網站下載 web 安裝程式，或建立離線安裝配置（如需詳細資訊，請參閱[建立 Visual Studio 的離線安裝](../install/create-an-offline-installation-of-visual-studio.md)頁面）。

> [!IMPORTANT]
> 您必須擁有系統管理員認證才能安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 不過，在安裝之後，您不需要它們也可使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。

 您的本機系統管理員帳戶必須啟用下列權限，才能安裝 Visual Studio 中的所有項目。

|本機原則物件的顯示名稱|使用者權限|
|--------------------------------------|----------------|
|備份檔案和目錄|SeBackupPrivilege|
|偵錯程式|SeDebugPrivilege|
|管理稽核及安全性記錄|SeSecurityPrivilege|

 如需本機系統管理員帳戶需求的詳細資訊，請參閱知識庫文件 [如果安裝帳戶並沒有特定使用者權限，SQL Server 安裝會失敗](https://support.microsoft.com/kb/2000257)。

### <a name="BKMK_Media"></a>使用安裝媒體
 若要安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，請在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 安裝媒體的根目錄中，針對您想要的版本來執行安裝檔案：

|版本|安裝檔案|
|-------------|-----------------------|
|Visual Studio 企業版|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="BKMK_Website"></a>從產品網站下載
 流覽[Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面，然後選取您想要的 Visual Studio 版本。

### <a name="downloading-from-your-subscription-service"></a>從您的訂用帳戶服務下載
 流覽 [ [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) ] 頁面，然後選取您想要的 Visual Studio 版本。

### <a name="BKMK_Offline"></a>建立離線安裝版面配置
 如果您沒有 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 安裝媒體，或您沒有 Visual Studio 的訂用帳戶，或不想使用 web 安裝程式來安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，您可以藉由建立所謂的離線安裝版面配置來執行「中斷連線」安裝。 如需詳細資訊，請參閱[建立 Visual Studio 的離線安裝](../install/create-an-offline-installation-of-visual-studio.md)頁面。

## <a name="enterprise"></a>在企業中部署 Visual Studio
 如需有關如何透過網路部署 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的詳細資訊，請參閱[Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)。

### <a name="BKMK_Virtualized"></a>在虛擬化環境中安裝 Visual Studio
 **HYPER-V 的視訊問題**

 如果 Windows Server 2008 R2 是在啟用 Hyper-V 的情況下使用加速圖形卡來執行，您可能會感受到系統速度變慢。

 如需詳細資訊，請參閱 Microsoft 網站的下列網頁： [當 Windows Server 2008 或 Windows Server 2008 R2 電腦已啟用 Hyper-V 角色且有安裝加速顯示卡時，視訊效能可能會降低](https://support.microsoft.com/kb/961661)。

 **使用 HYPER-V 模擬裝置**

 當您在實際的硬體上安裝 Visual Studio 2015，但沒有虛擬化時，您可以使用 HYPER-V 選擇能模擬 Windows 和 Android 裝置的功能。 當您安裝到 HYPER-V 時，將無法模擬 Windows 或 Android 裝置。 這是因為模擬器本身是虛擬機器，您目前不能在另一個 VM 內裝載 VM。 因應措施是使用實際的 Windows 或 Android 裝置，您可以直接在上面部署和偵錯應用程式。

## <a name="optionalComponents"></a>安裝選用元件
 如果您想要安裝您在原始安裝期間可能未選取的元件，請使用下列程式。

#### <a name="to-install-optional-components"></a>若要安裝選用元件

1. 在 [控制台]的 [程式和功能] 頁面上，選擇要在其中加入一個或多個元件的產品版本，然後選擇 [變更]。

2. 在安裝精靈中，選擇 [修改]，然後選擇您要安裝的元件。

3. 選擇 [下一步]，然後依照其餘指示進行。

## <a name="helpContent"></a> 安裝離線說明內容
 安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]之後，您可以下載其他的說明內容，以便可以離線使用。

#### <a name="to-install-or-uninstall-help-content"></a>安裝或解除安裝說明內容

1. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 功能表列上，依序選擇 [說明]、[加入和移除說明內容]。

2. 在 [Microsoft 說明檢視器] 的 [管理內容]索引標籤上，選取適用於您說明內容的安裝來源。

3. 如果您要尋找特定的說明集合，請在 [搜尋] 文字方塊中輸入名稱或關鍵字，然後按 **Enter**。

4. 在您想要的說明集合名稱旁邊，選擇 [加入] 或 [移除] 連結。

5. 按一下 [**更新**] 按鈕。

   如需有關如何安裝或部署離線說明的詳細資訊，請參閱[Help Viewer 系統管理員指南](../ide/help-viewer-administrator-guide.md)。

## <a name="serviceReleases"></a> 檢查服務版本與產品更新
 因為並非所有延伸模組都相容，從舊版升級時，Visual Studio 不會自動升級延伸模組。 您必須從[Visual Studio Marketplace](https://marketplace.visualstudio.com/)或軟體發行者重新安裝擴充功能。

#### <a name="to-automatically-check-for-service-releases"></a>自動檢查版本更新服務

1. 在功能表列上選擇 [工具]、[選項]。

2. 在 [選項] 對話方塊中，展開 [環境]，然後選取 [擴充功能和更新]。 確定已選取 [自動檢查更新] 核取方塊，然後選擇 [確定]。

## <a name="registering-visual-studio"></a>註冊 Visual Studio

1. 在功能表列上，選取 [說明]、[關於]。

     [關於] 對話方塊會顯示產品識別碼 (PID)。 您將需要 PID 和 Windows 帳戶認證 (例如 Hotmail 或 Outlook.com 電子郵件地址和密碼) 以註冊產品。

2. 在功能表列上，選擇 [說明]、[註冊產品]。

## <a name="repair"></a> 修復 Visual Studio

#### <a name="to-repair-visual-studio"></a>若要修復 Visual Studio

1. 在 [控制台]的 [程式和功能] 頁面上，選取要修復的產品版本，然後選擇 [變更]。

2. 在安裝精靈中，依序選擇 [修復]、[下一步]，然後依照其餘指示進行。

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>若要以無訊息或被動模式修復 Visual Studio （也就是從來源修復）

1. 在安裝 Visual Studio 的電腦上，開啟 Windows 命令提示字元。

2. 輸入下列參數：

     *DVDRoot* \\< 安裝檔案\> \</quiet&#124;/passive > [/norestart]/Repair

## <a name="troubleshooting"></a>疑難排解安裝問題
 請使用下列資源來取得設定及安裝問題的協助：

- [Visual Studio 安裝程式和安裝](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) 論壇。 在 Visual Studio 社群中，檢閱其他人提供的問題和解答。 如果您找不到所需的資訊，請詢問您自己的問題。

- [Microsoft Visual Studio 支援](https://support.microsoft.com/ph/1117) 網站。 閱讀知識庫 (KB) 文章，並了解如何連絡 Microsoft 技術支援以取得 Visual Studio 安裝問題的相關資訊。

## <a name="relatedTopics"></a> 相關主題

|標題|描述|
|-----------|-----------------|
|[建立 Visual Studio 的離線安裝](../install/create-an-offline-installation-of-visual-studio.md)|描述當您未連線到網際網路時，如何安裝 Visual Studio。
|[並存安裝 Visual Studio 版本](../install/install-visual-studio-versions-side-by-side.md)|提供如何在同一部電腦上安裝多個 Visual Studio 版本的相關資訊。|
|[使用命令列參數來安裝 Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|列出當您從命令提示字元安裝 Visual Studio 時，可以使用的命令列參數。|
|[解除安裝 Visual Studio](../install/uninstall-visual-studio.md)|說明如何卸載 Visual Studio。|
|[Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)|提供 Visual Studio 部署選項的相關資訊。|
|[Visual Studio 影像庫](../designers/the-visual-studio-image-library.md)|提供如何安裝可在 Visual Studio 應用程式中使用之圖形的相關資訊。|
|[Visual Studio 使用者開發入門](../ide/get-started-developing-with-visual-studio.md)|包含可協助您更有效率地使用 Visual Studio 的資訊和連結。|

## <a name="see-also"></a>請參閱

- [登入 Visual Studio](../ide/signing-in-to-visual-studio.md)
