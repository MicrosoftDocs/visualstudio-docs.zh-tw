---
title: 使用 Microsoft Endpoint Configuration Manager 將系統管理員更新套用至 Visual Studio
titleSuffix: ''
description: 瞭解如何將系統管理員更新套用至 Visual Studio。
ms.date: 04/16/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: c18c460ebcffdba93279aafec2f3d76503ab2383
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307683"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>套用使用 Microsoft Endpoint Configuration Manager 的系統管理員更新

本檔說明 Visual Studio 系統管理員更新的不同類型和特性。 您可以在下面找到有關如何及何時將其散發至整個組織、哪些設定選項可供使用，以及如何查看報告和疑難排解的資訊。 如需使用系統管理員更新之必要條件的詳細資訊，請參閱 [啟用系統管理員更新](../install/enabling-administrator-updates.md)。 系統管理員更新會假設電腦上已安裝 Visual Studio。 套用系統管理員更新不會起始全新安裝。

## <a name="understanding-visual-studio-administrator-updates"></a>瞭解 Visual Studio 系統管理員更新

發佈至 Microsoft Update 供 Microsoft Catalog 和 WSUS 取用的 Visual Studio 系統管理員更新套件，包含設定管理員必須能夠下載並散發 Visual Studio 更新至用戶端電腦的資訊。 它也包含 IT 系統管理員所需的資訊，以決定要在整個組織中散發哪些更新。 它也可以用來協助維護網路版面配置。 Visual Studio 系統管理員更新套件未包含足夠的資訊來進行產品的全新安裝，也不包含任何發佈至內容傳遞網路的實際產品二進位檔。 Visual Studio 系統管理員更新是累積的，就像定期 Visual Studio 更新一樣。 您可以假設有更高產品版本號碼和更新版本的任何 Visual Studio 更新都是舊版較低版本的超集合。

Visual Studio 系統管理員更新適用于受支援的 Visual Studio 服務版本。 如需特定時間範圍內仍支援哪些 Visual Studio 服務基準的詳細資訊，請參閱 [Visual Studio 產品生命週期和服務](/visualstudio/productinfo/vs-servicing-vs)。 所有支援的 Visual Studio 服務基準都會保持安全。  

## <a name="types-and-characteristics-of-administrator-updates"></a>系統管理員更新的類型和特性

有三種類型的系統管理員更新可 Visual Studio：

* **安全性更新** 適用于所有的 Visual Studio 版本 (例如企業版、專業版 ) 、專業版等），而且它們包含有限、高度目標且相容的服務等級變更。 安全性更新不會將用戶端前進至較新的次要版本;其設計目的是為了將安全性弱點的修正提供給已在特定次要版本層級的用戶端。 安全性更新將至少有一個安全性修正，但安全性修正程式可能不在安裝于用戶端電腦上的元件或工作負載中。 例如，我們可以修正 .NET 元件中的安全性弱點，我們會將更新標記為安全性更新，但在只安裝 c + + 元件的用戶端電腦上，並不會有任何有意義的效果。 安全性更新可能也包含其他可靠性修正或其他必要元件更新。 安全性更新會發佈至 [Microsoft Update 目錄](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) 和 [Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)，並將其分類為「安全性更新」。
* **功能更新** 可讓 IT 系統管理員將組織中的電腦推進至較新的次要版本 Visual Studio。 功能更新只適用于企業中常見的 Visual Studio 版本，例如 Enterprise、Professional 和 Build Tools Sku。 所有功能更新都會發佈至 Microsoft Update 類別目錄做為「功能套件」，並可選擇性地 [從 Microsoft Update 類別目錄手動匯入設定管理員](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)。 功能更新是累計的，而且會包含額外的品質和先前的安全性修正程式。 請參閱下面的設定 [選項一節](#understanding-configuration-options) ，以取得如何設定用戶端電腦以保持服務基準，以及防止將功能更新傳遞給特定用戶端的指示。
* **品質更新** 也只適用于企業中常見的 Visual Studio 版本，而且包含有限、高度目標且相容的服務層級變更。 品質更新不會將用戶端前進至較新的次要版本;其設計目的是要將效能和可靠性修正或其他必要元件更新提供給已在特定次要版本層級的用戶端。 品質更新會隨安全性更新累積，因此只有在安全性修正已獨立發行時，才會包含安全性修正。 品質更新會以「更新」的形式發佈到 Microsoft Update 目錄，也可以選擇性地手動匯 [入設定管理員](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)。

### <a name="decoding-the-titles-of-administrator-updates"></a>解碼系統管理員更新的標題

每個系統管理員更新的標題都會描述適用的版本範圍和更新的結果版本。例如，

::: moniker range="vs-2017"

* **Visual Studio 2017 版本 15.9.0 15.9.35 更新** 分類為「安全性更新」時，將會套用至用戶端上的 Visual Studio 任何2017版，這些版本是透過 15.9.35 15.9.0 的版本，並且會將這些用戶端版本更新為15.9.35。
* **15.0.0 版2017版的15.9.0 更新** 分類為「Feature Pack」，將適用于在15.0.0 版至15.9.0 的整個產品版本範圍之間，在用戶端上授權供企業使用的 Visual Studio 2017 版，並將這些用戶端版本更新為15.9.0。 Visual Studio 套用此功能套件基本上可讓用戶端接收安全性更新。 
* **Visual Studio 2017 版本的15.9.37 更新** 分類為單純的「更新」，將會套用至在用戶端上針對企業使用所授權的 Visual Studio 2017 版本（從15.9.0 到15.9.37 的版本之間），並將這些用戶端版本更新為15.9.37。

::: moniker-end

::: moniker range="vs-2019"

* **Visual Studio 2019 版本 16.7.0 16.7.12 更新** 分類為「安全性更新」時，將會套用至用戶端上的 Visual Studio 任何2019版，這些版本是透過 16.7.12 16.7.0 的版本，並且會將這些用戶端版本更新為16.7.12。  
* **Visual Studio 2019 版的16.9.0 更新** 分類為「Feature Pack」，將適用于在16.0.0 版至16.9.0 的整個產品版本範圍之間，于用戶端上以企業用途授權的 Visual Studio 2019 版本，並且會更新尚未設定為維持在舊版服務基準) 16.9.0 的用戶端 (版本。 
* **Visual Studio 2019 版本的16.8.7 更新** 分類為單純的「更新」，將會套用至在用戶端上針對企業使用所授權的 Visual Studio 2019 版本（從16.8.0 到16.8.7 的版本之間），並將這些用戶端版本更新為16.8.7。

::: moniker-end

::: moniker range=">=vs-2022"

::: moniker-end

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>使用設定管理員部署 Visual Studio 更新

### <a name="understanding-configuration-options"></a>瞭解設定選項

有幾個設定選項可用來自訂 Visual Studio 系統管理員更新，使其相容並符合您組織的部署喜好設定和需求。 最常見的設定選項如下所示。 如需所有支援之系統管理員更新行為的詳盡清單，請參閱 [使用命令列參數安裝 Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) ，並只需注意與「更新」動作對應的程式。

* **[系統管理員更新加入宣告](../install/enabling-administrator-updates.md#encoding-administrator-intent-on-the-client-machines)**：需要此登錄機碼才能讓用戶端電腦接收系統管理員更新。 它是全電腦的金鑰，這表示它適用于所有安裝在 box Visual Studio 實例。
* **Visual Studio 使用者退出**： Visual Studio 使用者可以使用個別的全電腦 **AdministratorUpdatesOptOut** 登錄機碼，以 *選擇* 不接收 Visual Studio 系統管理員更新。 此金鑰的目的是要讓 Visual Studio 的使用者有權控制自動套用至電腦的更新。 若要將用戶端電腦設定為封鎖系統管理員更新，請將 **AdministratorUpdatesOptOut**   REG_DWORD 機碼設定為 **1**。 缺少索引鍵或設定值為 **0**，表示 Visual Studio 使用者想要接收 Visual Studio 的系統管理員更新。
    請注意， ****   編碼使用者喜好設定的 AdministratorUpdatesOptOut 索引鍵會優先于 **AdministratorUpdatesEnabled**   金鑰，以將 IT 系統管理員意圖編碼。 如果 **AdministratorUpdatesOptOut**   設定為 **1**，則即使 **AdministratorUpdatesEnabled** 索引   鍵也設為 **1**，也會在用戶端上封鎖更新。此動作會假設 IT 系統管理員可以存取並監視哪些開發人員退出宣告，而雙方接著可以討論其需求更重要。IT 系統管理員隨時都可以在需要時變更任何金鑰。
* **更新產品位的位置**：大多數時間，用戶端電腦會透過 Microsoft CDN 從網際網路下載更新的產品位。 此案例要求用戶端電腦必須能夠存取網際網路。 不過，某些企業會將用戶端電腦限制為只安裝和更新內部網路設定位置的 bits。 若要確保系統管理員可以使用內部網路位置上的更新位來套用系統管理員更新，必須符合下列條件，才能成功部署系統管理員更新： 
  * 在某個時間點，用戶端電腦必須已從該網路設定位置執行啟動載入器。 在理想情況下，原始用戶端安裝會使用從網路設定的啟動載入器進行，但是也可以在相同的網路位置中使用更新的啟動載入器來安裝更新。 其中一個動作會在用戶端電腦上，以該特定版面配置位置的連接來內嵌。
  * 網路設定位置 (用戶端連線到) 必須更新，以包含系統管理員更新要部署 [的更新產品位](../install/update-a-network-installation-of-visual-studio.md) 。

::: moniker range=">=vs-2019"

* **維護基準** 的內容：如上所述，系統管理員功能更新會將 Visual Studio 安裝前移至產品的最新次要版本。 不過，有時候 Visual Studio 使用者必須維持在特定穩定且安全的服務基準層級，而且他們想要控制其機器移至較新的次要版本的時間。 若要將用戶端電腦設定為維持服務基準，並忽略傳送給它的不想要的系統管理員功能更新，您必須建立 **BaselineStickinessVersions2019** Reg_SZ 資料值，並將其設定為代表用戶端電腦應貼齊並保持開啟之慣用基準的字串。 此字串可以包含可允許的服務基準版本，例如 **16.7.0**。  
     如果 `BaselineStickinessVersions2019` 登錄值的格式不正確，則會禁止所有系統管理員功能更新安裝在電腦上。 請務必留意 [Visual Studio 功能更新所支援](/visualstudio/productinfo/vs-servicing-vs)的時間範圍。 此外，不論金鑰的存在與否或值 `BaselineStickinessVersions2019` 為何，雖然技術上可能會套用已達到存留期結束的系統管理員功能更新，但我們不建議您這麼做，因為它們會不受支援，因此可能不安全。

::: moniker-end

* **即使 Visual Studio 正在使用中，仍強制進行更新**：在安裝更新之前，必須先關閉 Visual Studio。 如果 Visual Studio 已開啟或正在使用中，更新安裝將會中止。 確保關閉 Visual Studio 的簡單方式，是將確認管理員設定為在機器重新開機後立即套用更新。 您也可以使用 `--force` 參數來強制關閉 Visual Studio。 強制關閉 Visual Studio 可能會導致工作遺失，因此請小心使用。 在預設系統內容中執行系統管理員更新將會忽略 `–-force` 旗標，因此您必須將系統管理員更新設定為在使用者內容中執行。

### <a name="methods-for-configuring-an-administrator-update"></a>設定系統管理員更新的方法

有三種主要的方法可以設定系統管理員更新：登錄機碼、用戶端電腦上的設定檔，或設定管理員部署套件本身的修改。   

* 登錄機 **碼**：系統管理員更新會尋找任何標準 Visual Studio 位置中的特定登錄機碼，如 [設定企業部署的預設值](../install/set-defaults-for-enterprise-deployments.md)中所述。 由登錄機碼控制的選項是 **AdministratorUpdatesOptOut** Reg_DWORD、 **AdministratorUpdatesOptOut**   Reg_DWORD 和 **BaselineStickinessVersions2019** Reg_SZ 等專案。 需要用戶端電腦上的系統管理員存取權，才能建立及設定登錄機碼的值。

* **設定檔**：某些設定可以保留在用戶端電腦上的選擇性設定檔中，此設定檔的優點是只將它設定為一次，並將它套用至所有未來的系統管理員更新。 設定檔方法的行為就像是登錄機碼，而且是電腦範圍，這表示它會套用至用戶端電腦上安裝的 Visual Studio 的所有安裝。 設定檔案的標準位置為 `C:\ProgramData\Microsoft\VisualStudio\updates.config` 。 但是，如果您想要使用另一個位置來儲存檔案，您可以建立名為 **UpdateConfigurationFile** 的 Reg_SZ 登錄機碼，並將此機碼的值設定為設定檔的路徑。 此登錄機碼可放置在任何 Visual Studio 登錄位置中，如 [設定企業部署的預設值](../install/set-defaults-for-enterprise-deployments.md)中所述。 如果您選擇新增自訂設定檔位置的登錄值，它會尋找該檔案;如果檔案不存在，則會擲回例外狀況，且更新會失敗。

     設定檔（採用 JSON 格式）支援選項， `installerUpdateArgs` 這是以逗號分隔的字串陣列，可指定可傳遞給 Visual Studio 安裝程式的更多參數。 如果檔案的內容包含不正確欄位或不支援的選項，則更新將會失敗。 如需詳細資訊，請參閱 [使用命令列參數來安裝 Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)。

   以下是範例設定檔案：

  ```json
  "installerUpdateArgs" : ["--quiet", "--noWeb"], 
  "checkPendingReboot" :  "true" 
  ```

* **在 sccm 中手動更新系統管理員更新套件**：您也可以手動修改 sccm 中個別系統管理員更新套件的命令列參數。

## <a name="verification-reports-and-troubleshooting-error-codes"></a>驗證、報告和疑難排解錯誤代碼

### <a name="determining-that-visual-studio-was-updated"></a>判斷 Visual Studio 已更新

您可以使用下列其中一種方法來驗證系統管理員更新是否已正確安裝：

* 在用戶端電腦上，啟動 Visual Studio， **選取**[說明]   >  ****，並確認版本號碼符合預期更新標題中的最後一個數位。
* 使用用戶端電腦上的 **vswhere** 工具，識別電腦上的各種 Visual Studio 版本。 如需詳細資訊，請參閱偵測 [和管理 Visual Studio 實例的工具](../install/tools-for-managing-visual-studio-instances.md)。
* 每個系統管理更新嘗試都會在用戶端電腦的目錄中產生數個記錄檔 `%temp%` ，以捕獲更新作業的進度。依日期排序資料夾，然後  `dd_updatedriver`  `dd_bootstrapper` 分別針對  `dd_client` 管理更新、啟動載入器  `dd_setup`   、Visual Studio 安裝程式和安裝程式引擎尋找開始、、和的檔案。確認這些記錄檔包含0，表示已成功套用更新。 請注意，這些記錄檔也可以用來確認正在使用設定檔案。 如需詳細資料，請參閱 [Visual Studio 記錄收集工具](https://www.microsoft.com/download/details.aspx?id=12493) 。

### <a name="error-codes-and-conditions"></a>錯誤碼和條件

>[!IMPORTANT]
> 請記住，在安裝更新之前，必須先關閉 Visual Studio。 如果 Visual Studio 已開啟或正在使用中，則會取消更新安裝。

系統管理更新可能會傳回下列傳回碼：  

| 錯誤碼 | 定義                                                                                                                                                                                                  |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0          | 已成功安裝系統管理更新。                                                                                                                                                       |
| 1001       | Visual Studio 安裝程式或相關的安裝程式正在執行。 不會套用更新。                                                                                                                   |
| 1002       | Visual Studio 安裝程式已暫停。 不會套用更新。                                                                                                                                               |
| 1003       | Visual Studio 正在執行。 不會套用更新。 您可以使用旗標來將這種情況無效 `--force` 。                                                                                              |
| 1004       | 未偵測到網際網路。更新無法連絡保存更新檔案的網際網路位置。 不會套用更新。                                                                          |
| 1005       |  **AdministratorUpdatesEnabled** 登錄   值設定為 **0** ，或完全未設定。 不會套用更新。                                                                                            |
| 1006       |  **AdministratorUpdatesOptOut** 登錄   值設定為 **1**。 不會套用更新。 金鑰適用于系統管理員不應更新的用戶端電腦。                     |
| 1007       | 未安裝 Visual Studio 安裝程式。                                                                                                                                                               |
| 1008       | **BaselineStickinessVersions2019** 登錄值不是可讀取的格式。 登錄值必須包含 **所有** 或有效版本，其組建編號會明確設定為0，例如，X. 0。 |
| 3010       | 系統需要重新開機。更新可能已套用或可能尚未套用。 請重新開機電腦，然後再次嘗試更新。                                                                                |
| 其他      | 嘗試套用更新時發生錯誤。不會套用更新。                                                                                                                                   |

如需用戶端錯誤碼的詳盡清單，請參閱 [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)。

## <a name="feedback-and-support"></a>意見反應與支援

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

您可以使用下列方法來提供有關 Visual Studio 系統管理員更新的意見反應，或回報影響更新的問題：

* 請參閱 [疑難排解 Visual Studio 安裝和升級問題](../install/troubleshooting-installation-issues.md) 的指引。
* 在 [Visual Studio 設定 Q&論壇](/answers/topics/vs-setup.html)中詢問有關社區的問題。
* 移至 [ [Visual Studio 支援] 頁面](https://visualstudio.microsoft.com/vs/support/)，並檢查問題是否列在常見問題中。  您也可以選取 [交談說明] 的 [ [支援連結](https://visualstudio.microsoft.com/vs/support/#talktous) ] 按鈕。
* [提供功能意見](https://aka.ms/vs/wsus/feedback) 反應，或向 Visual Studio 團隊回報有關套用系統管理員更新之體驗的問題。
* 洽詢您組織的 Microsoft 技術客戶經理。

## <a name="see-also"></a>另請參閱

* [啟用系統管理員更新](../install/enabling-administrator-updates.md)
* [Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)
* [Visual Studio 產品生命週期和服務](/visualstudio/productinfo/vs-servicing-vs)
* [Visual Studio 2019 版本資訊](/visualstudio/releases/2019/release-notes)
* [Visual Studio 2017 版本資訊](/visualstudio/releasenotes/vs2017-relnotes)
* [安裝 Visual Studio](../install/install-visual-studio.md)
* [使用命令列參數安裝 Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)
* [用於偵測及管理 Visual Studio 執行個體的工具](../install/tools-for-managing-visual-studio-instances.md)
* [建立 Visual Studio 的網路安裝](../install/create-a-network-installation-of-visual-studio.md)
* [如何在回應檔中定義設定](../install/automated-installation-with-response-file.md)
* [控制網路型 Visual Studio 部署的更新](../install/controlling-updates-to-visual-studio-deployments.md)
* [Microsoft Update 目錄常見問題](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager (SCCM) 檔](/mem/configmgr)
* [從 Microsoft Catalog 將更新匯入設定管理員](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS) 檔](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
