---
title: 為 Azure 雲端服務和虛擬機器設定診斷 |Microsoft Docs
description: 了解如何設定偵錯 Azure 雲端服務和虛擬機器 (Vm) 在 Visual Studio 中的診斷。
author: mikejo5000
manager: douge
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 4448825c5d443887833a405aab14d2243a0e5216
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002087"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>針對 Azure 雲端服務與虛擬機器設定診斷
當您需要疑難排解 Azure 雲端服務或虛擬機器時，您可以使用 Visual Studio 更輕鬆地設定 Azure 診斷。 診斷會擷取系統資料和記錄資料的虛擬機器和執行雲端服務的虛擬機器執行個體上。 診斷資料傳送到您選擇的儲存體帳戶。 如需診斷的詳細資訊記錄在 Azure 中，請參閱[針對 Azure App Service 中的 Web 應用程式啟用診斷記錄](/azure/app-service/web-sites-enable-diagnostic-log)。

在本文中，我們示範您如何使用 Visual Studio 來開啟和設定 Azure 診斷，在部署前後。 了解如何設定 Azure 虛擬機器上的診斷、 如何選取要收集的診斷資訊類型及如何收集之後檢視資訊。

您可以使用下列選項之一來設定 Azure 診斷：

* 變更診斷設定**診斷組態**Visual Studio 中的對話方塊。 這些設定會儲存在稱為 diagnostics.wadcfgx （在 Azure SDK 2.4 和更早版本，檔案稱為 diagnostics.wadcfg） 的檔案。 您也可以直接修改組態檔。 如果您手動更新檔案，這個組態變更生效下次部署雲端服務至 Azure，或在模擬器中執行服務。
* 使用雲端總管] 或 [伺服器總管 」 Visual Studio 中，若要變更雲端服務或執行的虛擬機器的診斷設定。

## <a name="azure-sdk-26-diagnostics-changes"></a>Azure SDK 2.6 診斷變更
Azure SDK 2.6 和更新版本的專案，Visual Studio 中適用於下列變更：

* 本機模擬器現在支援診斷。 這表示您可以用來收集診斷資料，並確保您的應用程式在開發及測試 Visual Studio 中時，會建立正確的追蹤。 連接字串`UseDevelopmentStorage=true`開啟診斷資料集合，當您執行您的雲端服務專案在 Visual Studio 中使用 Azure 儲存體模擬器。 開發儲存體儲存體帳戶中，會收集所有的診斷資料。
* 診斷儲存體帳戶連接字串`Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString`會儲存在服務組態 (.cscfg) 檔。 在 Azure SDK 2.5，diagnostics.wadcfgx 檔案中指定診斷儲存體帳戶。

連接字串的運作方式不同以一些主要的方式在 Azure SDK 2.6 和更新版本與 Azure SDK 2.4 及更早版本：

* 在 Azure SDK 2.4 和更早版本，連接字串來與執行階段診斷外掛程式取得用於傳輸診斷記錄的儲存體帳戶資訊。
* 在 Azure SDK 2.6 和更新版本，Visual Studio 會使用診斷連接字串，若要設定 Azure 診斷擴充功能，在發佈期間的適當的儲存體帳戶資訊。 您可以使用的連接字串來定義不同的儲存體帳戶的 Visual Studio 在發佈期間使用的不同服務組態。 不過，因為 Azure SDK 2.5 之後無法使用診斷外掛程式，.cscfg 檔案本身無法設定診斷延伸模組。 您必須設定延伸模組分開使用 Visual Studio 或 PowerShell 等工具。
* 為了簡化使用 PowerShell 設定診斷延伸模組的程序，從 Visual Studio 的封裝輸出會包含每個角色的診斷擴充功能公用組態 XML。 Visual Studio 會使用診斷連接字串，填入公用設定中的儲存體帳戶資訊。 公用設定檔會建立擴充功能資料夾中。 公用設定檔使用的命名模式 PaaSDiagnostics。&lt;角色名稱\>.Pubconfig.xml。 任何以 PowerShell 為基礎的部署可以使用此模式，來將每個組態對應至角色。
* [Azure 入口網站](http://go.microsoft.com/fwlink/p/?LinkID=525040).cscfg 檔案中使用的連接字串，來存取診斷資料。 資料會出現在**監視** 索引標籤。連接字串，才能設定服務以在入口網站中顯示詳細監視資料。

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>移轉至 Azure SDK 2.6 及更新版本的專案
當您移轉從 Azure SDK 2.5 Azure SDK 2.6 或更新版本，如果您有.wadcfgx 檔案中指定診斷儲存體帳戶時，儲存體帳戶會保持在該檔案中。 若要利用不同的儲存體組態使用不同的儲存體帳戶的彈性，手動將連接字串加入您的專案。 如果您要移轉的專案，從 Azure SDK 2.4 或先前以 Azure SDK 2.6，則會保留診斷連接字串。 不過請注意在上一節中所述的 Azure SDK 2.6 中連接字串的處理方式的變更。

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Visual Studio 如何決定診斷儲存體帳戶
* 如果在.cscfg 檔案中指定診斷連接字串，則 Visual Studio 會使用它來設定診斷延伸模組，在發行期間，以及在封裝期間產生公用組態 XML 檔案時。
* 如果未在.cscfg 檔案中指定診斷連接字串，Visual Studio 退而使用在.wadcfgx 檔案來設定診斷延伸模組進行發佈，以及產生公用組態 XML 中指定的儲存體帳戶在封裝期間的檔案。
* .Cscfg 檔案中的診斷連接字串的優先順序高於.wadcfgx 檔案中的儲存體帳戶。 如果診斷連接字串是在.cscfg 檔案中，指定 Visual Studio 會使用該連接字串並忽略.wadcfgx 中的儲存體帳戶。

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>「 更新開發儲存體連接字串...」 核取方塊的作用為何？
**更新開發儲存體連接字串以供診斷和快取，使用 Microsoft Azure 儲存體帳戶認證時發佈至 Microsoft Azure**核取方塊是便利的方式來更新任何開發儲存體帳戶連接字串與您在發佈期間指定的 Azure 儲存體帳戶。

例如，如果您選取此核取方塊和診斷連接字串指定`UseDevelopmentStorage=true`，當您發行專案至 Azure，Visual Studio 會自動更新診斷連接字串中指定的儲存體帳戶[發行精靈]。 不過，如果實際的儲存體帳戶指定為診斷連接字串，該帳戶是改為使用。

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>在 Azure SDK 2.4 及更舊版本中的診斷功能差異。Azure SDK 2.5 及更新版本
如果您要升級您的專案，從 Azure SDK 2.4 和稍早為 Azure SDK 2.5 或更新版本，請記住下列診斷功能差異：

* **組態 Api 已淘汰**。 適用於 Azure SDK 2.4 和更早版本，以程式設計方式設定診斷，但在 Azure SDK 2.5 及更新版本已被取代。 如果您的診斷組態目前定義程式碼中，您必須重新設定診斷的移轉專案中從頭繼續使用這些設定。 Azure SDK 2.4 的診斷組態檔是 diagnostics.wadcfg。 Azure SDK 2.5 及更新版本時，診斷組態檔是 diagnostics.wadcfgx。
* **雲端服務應用程式的診斷可設定只能在角色層級**。 在 Azure SDK 2.5 和更新版本，無法在執行個體層級設定雲端服務應用程式的診斷。
* **每次您部署您的應用程式時，都會更新診斷組態**。 如果您從 Visual Studio 伺服器總管 變更診斷組態，然後重新部署您的應用程式，這會導致同位問題。
* **在 Azure SDK 2.5 和更新版本，在 診斷組態檔，而不是在程式碼設定損毀傾印**。 如果您有程式碼中設定的損毀傾印，您必須手動將組態從程式碼組態檔。 損毀傾印不是在移轉期間移轉至 Azure SDK 2.6。

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>在部署之前開啟雲端服務專案中的診斷
在 Visual Studio 中，您可以收集診斷資料，當您在部署之前模擬器中執行服務時，在 Azure 中執行的角色。 Visual Studio 中對診斷設定的所有變更都會都儲存在 diagnostics.wadcfgx 組態檔中。 這些設定會指定當您部署您的雲端服務時，其中儲存診斷資料的儲存體帳戶。

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>若要開啟 Visual Studio 中部署之前的診斷

1. 在角色的捷徑功能表，選取**屬性**。 在角色的**屬性**對話方塊中，選取**組態** 索引標籤。
2. 在 **診斷**區段中，請確定**啟用診斷**選取核取方塊。
   
    ![存取啟用診斷選項](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. 若要指定診斷資料的儲存體帳戶，請選取省略符號 （...） 按鈕。
   
    ![指定要使用的儲存體帳戶](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. 在 **建立儲存體連接字串**對話方塊方塊中，指定您想要使用 Azure 儲存體模擬器，Azure 訂用帳戶中，連接或手動輸入的認證。
   
    ![儲存體帳戶對話方塊](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)
   
   * 如果您選取**Microsoft Azure 儲存體模擬器**，連接字串設定為`UseDevelopmentStorage=true`。
   * 如果您選取**訂用帳戶**，您可以選取您要使用的 Azure 訂用帳戶，並輸入帳戶名稱。 若要管理您的 Azure 訂用帳戶，請選取**Manage Accounts**。
   * 如果您選取**手動輸入的認證**，輸入名稱和您想要使用的 Azure 帳戶金鑰。
5. 若要檢視**診斷組態**對話方塊中，選取**設定**。 除了**一般**並**記錄檔目錄**，每個索引標籤各代表您可以收集的診斷資料來源。 預設值**一般**索引標籤提供下列診斷資料收集選項：**僅限錯誤**，**所有資訊**，和**自訂計劃**. 預設值**僅限錯誤**選項會使用最少的儲存體，因為它不會傳輸警告或追蹤訊息。 **的所有資訊**選項會傳輸大部分的資訊、 使用最多的儲存體，以及因此，是最昂貴的選項。

   > [!NOTE]
   > 針對 「 磁碟配額中 MB 」 支援的大小下限為 4 GB。 不過，如果您要收集記憶體傾印，增加這個較高的值，例如 10 GB。
   >
  
    ![啟用 Azure 診斷和組態](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. 此範例中，選取**自訂計劃**選項，因此您可以自訂收集的資料。
7. 在 [ **mb 的磁碟配額**] 方塊中，您可以設定要在診斷資料的儲存體帳戶中配置多少空間。 您可以變更或接受預設值。
8. 在您想要收集的診斷資料的每個索引標籤上，選取**啟用傳輸\<記錄檔類型\>** 核取方塊。 例如，如果您想要收集的應用程式記錄檔中，**應用程式記錄檔**索引標籤上，選取**啟用傳輸應用程式記錄檔**核取方塊。 此外，指定所需的每個診斷資料類型的其他資訊。 每個索引標籤的設定資訊，請參閱節**設定診斷資料來源**本文稍後。 
9. 您已啟用您想要的所有診斷資料收集之後，請選取**確定**。
10. 像往常一樣在 Visual Studio 中執行您的 Azure 雲端服務專案。 當您使用您的應用程式時，您已啟用的記錄資訊會儲存到您指定的 Azure 儲存體帳戶。

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>開啟 Azure 虛擬機器上的診斷
在 Visual Studio 中，您可以收集 Azure 虛擬機器的診斷資料。

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>若要開啟 Azure 虛擬機器上的診斷

1. 在伺服器總管 中，選取 Azure 節點，然後連接至您 Azure 訂用帳戶中，如果您尚未連接。
2. 依序展開**虛擬機器**節點。 您可以建立新的虛擬機器，或選取現有的節點。
3. 在您想要的虛擬機器的捷徑功能表，選取**設定**。 虛擬機器的 [設定] 對話方塊隨即出現。
   
    ![設定 Azure 虛擬機器](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. 如果尚未安裝，請新增 Microsoft Monitoring Agent 診斷延伸模組。 與此延伸模組，您可以收集 Azure 虛擬機器的診斷資料。 底下**已安裝擴充功能**，請在**選取 可用的擴充功能**下拉式清單方塊中，選取**Microsoft Monitoring Agent 診斷**。
   
    ![安裝 Azure 虛擬機器擴充功能](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)
   
    > [!NOTE]
   > 其他診斷延伸模組可供您的虛擬機器。 如需詳細資訊，請參閱 <<c0> [ 虛擬機器擴充功能和 Windows 的功能](https://docs.microsoft.com/azure/virtual-machines/windows/extensions-features)。
   > 
   > 
5. 若要新增延伸模組及檢視其**診斷組態**對話方塊中，選取**新增**。
6. 若要指定儲存體帳戶，請選取**設定**，然後選取**確定**。
   
    每個索引標籤 (除了**一般**並**記錄檔目錄**) 代表您可以收集的診斷資料來源。
   
    ![啟用 Azure 診斷和組態](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
   
    [預設] 索引標籤中，**一般**，提供您下列的診斷資料收集選項：**僅限錯誤**，**所有資訊**，和**自訂計劃**. [預設] 選項中，**僅限錯誤**，佔用最少的儲存體，因為它不會傳輸警告或追蹤訊息。 **的所有資訊**選項會傳輸大部分的資訊和，因此它是對儲存體而言最昂貴的選項。
7. 此範例中，選取**自訂計劃**選項，使您可以自訂資料收集。
8. **Mb 的磁碟配額** 方塊中指定您要配置儲存體帳戶中的診斷資料的空間。 如果您想要您可以變更預設值。
9. 在您想要收集的診斷資料的每個索引標籤上，選取其**啟用傳輸\<記錄檔類型\>** 核取方塊。
   
    例如，如果您想要收集應用程式記錄檔，選取**啟用 přenos protokolů Aplikace**  核取方塊**應用程式記錄檔** 索引標籤。此外，指定所需的每個診斷資料類型的其他資訊。 每個索引標籤的設定資訊，請參閱節**設定診斷資料來源**本文稍後。
10. 您已啟用所有您想要的診斷資料收集之後，請選取**確定**。
11. 儲存更新的專案。
    
    中的訊息**Microsoft Azure 活動記錄**視窗表示已更新虛擬機器。

## <a name="set-up-diagnostics-data-sources"></a>設定診斷資料來源
啟用診斷資料收集之後，您可以選擇您想要收集，完全是何種資料來源和所收集的資訊。 下節說明中的索引標籤**診斷組態** 對話方塊中，以及每個組態選項的意義。

### <a name="application-logs"></a>應用程式記錄檔
應用程式記錄具有 web 應用程式所產生的診斷資訊。 如果您想要擷取應用程式記錄檔，請選取**啟用傳輸應用程式記錄檔**核取方塊。 若要增加或減少應用程式將記錄傳輸至儲存體帳戶之間的間隔，變更**傳輸期間 （分鐘）** 值。 您也可以變更藉由設定記錄中擷取的資訊量**記錄層級**值。 例如，選取**Verbose**以取得詳細資訊，或選取**重大**只擷取嚴重錯誤。 如果您有特定的診斷提供者發出應用程式記錄檔，您可以藉由新增提供者的 GUID，在擷取記錄檔**提供者 GUID**  方塊中。

  ![應用程式記錄檔](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

如需有關應用程式記錄檔的詳細資訊，請參閱[針對 Azure App Service 中的 Web 應用程式啟用診斷記錄](/azure/app-service/web-sites-enable-diagnostic-log)。

### <a name="windows-event-logs"></a>Windows 事件記錄檔
若要擷取 Windows 事件記錄檔，請選取**啟用傳輸 Windows 事件記錄檔**核取方塊。 若要增加或減少的事件記錄檔傳輸至儲存體帳戶之間的間隔，變更**傳輸期間 （分鐘）** 值。 選取您想要追蹤的事件類型的核取方塊。

![事件記錄檔](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

如果您使用 Azure SDK 2.6 或更新版本，而且您想要指定自訂資料來源，請輸入它**\<資料來源名稱\>** 文字方塊中，然後選取**新增**。 資料來源會新增至 diagnostics.cfcfg 檔案。

如果您正在使用 Azure SDK 2.5 且想要指定自訂資料來源時，您可以將它加入`WindowsEventLog`區段在 diagnostics.wadcfgx 檔案，例如在下列範例中：

```
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```
### <a name="performance-counters"></a>效能計數器
效能計數器資訊可協助您找出系統瓶頸並微調系統和應用程式的效能。 如需詳細資訊，請參閱 <<c0> [ 在 Azure 應用程式中的建立及使用效能計數器](https://msdn.microsoft.com/library/azure/hh411542.aspx)。 若要擷取效能計數器，請選取**啟用效能計數器的傳輸**核取方塊。 若要增加或減少的事件記錄檔傳輸至儲存體帳戶之間的間隔，變更**傳輸期間 （分鐘）** 值。 選取您想要追蹤的效能計數器的核取方塊。

![效能計數器](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

若要追蹤未列出的效能計數器，請使用建議的語法輸入效能計數器。 然後選取**新增**。 虛擬機器上的作業系統會決定您可以追蹤的效能計數器。如需有關語法的詳細資訊，請參閱 <<c0> [ 指定計數器路徑](https://msdn.microsoft.com/library/windows/desktop/aa373193.aspx)。

### <a name="infrastructure-logs"></a>基礎結構記錄檔
基礎結構記錄具有 Azure 診斷基礎結構、 RemoteAccess 模組和 RemoteForwarder 模組的相關資訊。 若要收集基礎結構記錄檔的相關資訊，請選取**啟用傳輸基礎結構記錄檔**核取方塊。 若要增加或減少的間隔的基礎結構記錄檔傳輸至儲存體帳戶，請變更**傳輸期間 （分鐘）** 值。

![診斷基礎結構記錄檔](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

如需詳細資訊，請參閱 <<c0> [ 藉由使用 Azure 診斷收集記錄資料](https://msdn.microsoft.com/library/azure/gg433048.aspx)。

### <a name="log-directories"></a>記錄檔目錄
記錄檔目錄具有從 Internet Information Services (IIS) 要求、 失敗的要求，或您選擇之資料夾的記錄檔目錄中收集的資料。 若要擷取記錄檔目錄，請選取**啟用的記錄檔目錄的傳輸**核取方塊。 若要增加或減少將記錄傳輸至儲存體帳戶之間的間隔，變更**傳輸期間 （分鐘）** 值。

選取您想要收集，例如記錄檔的核取方塊**IIS 記錄檔**並**失敗要求**記錄檔。 提供預設儲存體容器名稱，但您可以變更名稱。

您可以擷取任何資料夾中的記錄檔。 指定路徑**絕對目錄中的記錄檔**區段，然後再選取**新增目錄**。 記錄會擷取在指定的容器。

![記錄檔目錄](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>ETW 記錄檔
如果您使用[的 Windows 事件追蹤](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx)(ETW)，而且想要擷取 ETW 記錄檔中，選取**啟用傳輸 ETW 記錄檔**核取方塊。 若要增加或減少將記錄傳輸至儲存體帳戶之間的間隔，變更**傳輸期間 （分鐘）** 值。

從事件來源和您指定的事件資訊清單擷取事件。 若要指定事件來源，在**事件來源**區段中，輸入名稱，然後選取**新增事件來源**。 同樣地，您可以在其中指定中的事件資訊清單**事件資訊清單**區段，然後再選取**新增事件資訊清單**。

![ETW 記錄檔](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

ETW 架構支援在 ASP.NET 中的類別透過[System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110))命名空間。 Microsoft.WindowsAzure.Diagnostics 命名空間，會繼承並擴充標準[System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110))類別，可讓您使用[System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110))作為記錄在 Azure 環境中的架構。 如需詳細資訊，請參閱 <<c0> [ 參加 Microsoft Azure 中控制記錄和追蹤](https://msdn.microsoft.com/magazine/ff714589.aspx)並[在 Azure 雲端服務和虛擬機器中啟用診斷](/azure/cloud-services/cloud-services-dotnet-diagnostics)。

### <a name="crash-dumps"></a>損毀傾印
若要擷取角色執行個體的當機的相關資訊，請選取**啟用傳輸損毀傾印**核取方塊。 （由於 ASP.NET 處理大多數例外狀況，這是通常只對背景工作角色有用）。若要增加或減少專用於損毀傾印的儲存空間的百分比，變更**目錄配額 （%）** 值。 您可以變更損毀傾印會儲存位置，而選取您想要擷取的儲存體容器**完整**或是**迷你**傾印。

目前正在追蹤的處理程序會列在下一步 的螢幕擷取畫面。 選取您想要擷取的處理程序的核取方塊。 若要新增另一個處理序清單，請輸入處理序名稱，然後按**新增處理序**。

![損毀傾印](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

如需詳細資訊，請參閱 <<c0> [ 參加 Microsoft Azure 中控制記錄和追蹤](https://msdn.microsoft.com/magazine/ff714589.aspx)並[Microsoft Azure 診斷第 4 部分： 自訂記錄元件和 Azure 診斷 1.3 變更](http://justazure.com/microsoft-azure-diagnostics-part-4-custom-logging-components-azure-diagnostics-1-3-changes/)。

## <a name="view-the-diagnostics-data"></a>檢視診斷資料
收集的雲端服務或虛擬機器的診斷資料之後，您可以檢視它。

### <a name="to-view-cloud-service-diagnostics-data"></a>若要檢視雲端服務診斷資料
1. 如往常般，將雲端服務部署，然後執行它。
2. 您可以在您的儲存體帳戶中之報表中的 Visual Studio 會產生，或在資料表中檢視診斷資料。 若要檢視的資料在報表中，開啟 [雲端總管] 或 [伺服器總管] 中，開啟您想要，然後選取之角色節點的捷徑功能表**檢視診斷資料**。
   
    ![檢視診斷資料](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)
   
    報告，以顯示可用的資料會出現。
   
    ![Visual Studio 中的 Microsoft Azure 診斷報告](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)
   
    如果未顯示最新的資料，您可能必須等到傳輸週期過後。
   
    若要立即更新資料，請選取**重新整理**連結。 若要自動更新資料，請選取 在間隔**自動重新整理**下拉式清單方塊。 若要匯出錯誤資料，請選取**匯出至 CSV**按鈕，以建立您可以在 Excel 工作表中開啟的逗號分隔值檔案。
   
    在 Cloud Explorer 或伺服器總管 中，開啟與部署相關聯的儲存體帳戶。
3. 在 資料表檢視器中開啟診斷資料表，然後檢閱您所收集的資料。 如需 IIS 記錄檔和自訂記錄檔，您可以開啟 blob 容器。 下表列出的資料表或 blob 容器包含不同的記錄檔資料。 除了該記錄檔資料，包含資料表項目**EventTickCount**， **DeploymentId**，**角色**，以及**RoleInstance**可協助您識別哪些虛擬機器與角色產生了資料和時間。 
   
   | 診斷資料 | 描述 | 位置 |
   | --- | --- | --- |
   | 應用程式記錄檔 |您的程式碼會藉由呼叫的方法產生的記錄檔**System.Diagnostics.Trace**類別。 |WADLogsTable |
   | 事件記錄檔 |從 Windows 事件記錄檔，在虛擬機器上的資料。 Windows 會將資訊儲存在這些記錄檔，但應用程式和服務也會使用記錄來報告錯誤或記錄資訊。 |WADWindowsEventLogsTable |
   | 效能計數器 |您可以使用虛擬機器的任何效能計數器上收集資料。 作業系統會提供效能計數器，其包括記憶體使用狀況和處理器時間等多種統計資料。 |WADPerformanceCountersTable |
   | 基礎結構記錄檔 |從診斷基礎結構本身產生的記錄檔。 |WADDiagnosticInfrastructureLogsTable |
   | IIS 記錄檔 |記錄 web 要求的記錄檔。 如果您的雲端服務取得大量的流量，這些記錄可能冗長。 它是個不錯的主意，來收集並儲存這項資料，只有當您在需要時。 |您可以找到失敗要求記錄下 wad-iis-failedreqlogs，該部署、 角色和執行個體的路徑下的 blob 容器中。 您可以找到下 wad-iis 記錄檔的完整記錄檔。 建立於 WADDirectories 資料表中做為每個檔案的項目。 |
   | 損毀傾印 |提供您的雲端服務處理程序 （通常是背景工作角色） 的二進位映像。 |wad 殲擊-傾印的 blob 容器 |
   | 自訂記錄檔 |您預先定義的資料的記錄檔。 |您可以指定在程式碼中的自訂記錄檔的位置在儲存體帳戶。 例如，您可以指定自訂 blob 容器。 |
4. 如果任何類型的資料遭到截斷，您可以嘗試增加該資料緩衝區型別，或縮短傳輸的資料從虛擬機器至儲存體帳戶之間的間隔。
5. （選擇性）清除資料，從儲存體帳戶，有時候以減少整體儲存成本。
6. 當您進行完整部署時，在 Azure 中，更新 diagnostics.cscfg 檔案 (Azure SDK 2.5.wadcfgx)，而且您的雲端服務挑選診斷組態所做的任何變更。 如果您改為更新現有的部署，.cscfg 檔案不會在 Azure 中更新。 您仍然可以依照下一節的步驟，變更診斷設定。 如需有關執行完整部署，並更新現有部署的詳細資訊，請參閱 <<c0> [ 發佈 Azure 應用程式精靈](vs-azure-tools-publish-azure-application-wizard.md)。

### <a name="to-view-virtual-machine-diagnostics-data"></a>若要檢視虛擬機器診斷資料
1. 在 虛擬機器的捷徑功能表，選取 **檢視診斷資料**。
   
    ![在 Azure 虛擬機器中檢視診斷資料](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)
   
    **診斷摘要** 對話方塊隨即出現。
   
    ![Azure 虛擬機器診斷摘要](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)  
   
    如果未顯示最新的資料，您可能必須等到傳輸週期過後。
   
    若要立即更新資料，請選取**重新整理**連結。 若要自動更新資料，請選取 在間隔**自動重新整理**下拉式清單方塊。 若要匯出錯誤資料，請選取**匯出至 CSV**按鈕，以建立您可以在 Excel 工作表中開啟的逗號分隔值檔案。

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>在部署後設定雲端服務診斷
如果您要調查的問題與已在執行中的雲端服務，您可能想要收集資料，您未指定您原本在部署角色之前。 在此情況下，您可以開始收集這類資料變更 [伺服器總管] 中的設定。 您可以將單一執行個體，或是在角色中，根據您是開啟的所有執行個體的診斷設定**診斷組態**對話方塊中，從執行個體或角色的捷徑功能表。 如果您設定角色節點，任何您所做的變更會套用至所有執行個體。 如果您設定執行個體節點，所做的任何變更會套用至該執行個體只。

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>若要執行的雲端服務的診斷設定
1. 在 伺服器總管 中，展開**雲端服務** 節點，然後展開節點以找出角色或執行個體 （或兩者） 的清單，您想要調查。
   
    ![設定診斷](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. 在執行個體節點或角色節點的捷徑功能表，選取**更新診斷設定**，然後選取您想要收集的診斷設定。
   
    組態設定的相關資訊，請參閱節**設定診斷資料來源**這篇文章中。 如需有關如何檢視診斷資料的資訊，請參閱下節**檢視診斷資料**這篇文章中。
   
    如果您變更在伺服器總管 中的資料收集時，所做的變更都有效，除非您完全重新部署您的雲端服務。 如果您使用預設發佈設定，所做的變更不會覆寫。 預設發佈設定是可更新現有的部署，而不執行完整部署。 若要確保在部署時會清除設定，請前往**進階設定**索引標籤的 發行精靈，然後清除**部署更新**核取方塊。 當您重新部署清除該核取方塊時，設定將還原為.wadcfgx （或.wadcfg） 檔案中為透過**屬性**角色的編輯器。 如果您更新您的部署，Azure 會保留先前的設定。

## <a name="troubleshoot-azure-cloud-service-issues"></a>針對 Azure 雲端服務問題進行疑難排解
如果您遇到雲端服務專案的相關問題，例如陷入 「 忙碌 」 狀態中，角色重複回收，或擲回內部伺服器錯誤，有工具和技術，可用來診斷並修正問題。 如需特定範例的常見問題和解決方案，以及概念和工具，您可以用來診斷和修正這些錯誤的概觀，請參閱[Azure PaaS 計算診斷資料](http://blogs.msdn.com/b/kwill/archive/2013/08/09/windows-azure-paas-compute-diagnostics-data.aspx)。

## <a name="q--a"></a>問與答
**何謂緩衝區大小，而且大小應該它嗎？**

在每個虛擬機器執行個體中，配額會限制多少診斷資料可以儲存在本機檔案系統。 此外，您可以指定每種類型的診斷資料所提供的緩衝區大小。 這個緩衝區大小就像是該資料類型的個別配額。 若要判斷整體配額和剩餘的記憶體數量，請參閱對話方塊底部的診斷資料類型。 如果您指定較大的緩衝區或更多類型的資料，您會愈趨近整體配額。 您可以藉由修改 diagnostics.wadcfg 或.wadcfgx 組態檔變更整體配額。 診斷資料會儲存在相同的檔案系統，為您的應用程式資料。 如果您的應用程式使用大量磁碟空間，您不應該增加整體診斷配額。

**何謂傳輸週期和多久？**

傳輸週期是時間的資料擷取之間經過量。 每個傳輸週期之後，資料會從本機檔案系統上移的虛擬機器儲存體帳戶中的資料表。 如果收集的資料量在傳輸週期結束前超過配額，則會捨棄較舊的資料。 如果您會遺失資料，因為資料超過緩衝區大小或整體配額，您可能想要縮短傳輸週期。

**哪個時區時間戳記是指在？**

時間戳記位於裝載雲端服務的資料中心的當地時區。 會使用下列三個時間戳記資料行中的記錄資料表：

* **PreciseTimeStamp**： 事件的 ETW 時間戳記。 也就是從用戶端記錄事件的時間。
* **時間戳記**： 的值**PreciseTimeStamp**無條件捨去到上傳頻率界限。 例如，如果您上傳頻率為 5 分鐘，而事件時間為 00:17:12，時間戳記是 00:15:00。
* **時間戳記**： 在 Azure 資料表中建立實體的時間戳記。

**收集診斷資訊時如何管理成本？**

預設設定 (**記錄層級**設為**錯誤**，和**傳輸週期**設定為**1 分鐘**) 設計用來將成本降至最低。 當您收集更多診斷資料，或縮短傳輸週期，就會增加運算成本。 請勿收集超過，也別忘了當您不再需要時停用資料收集的資料。 您可以一律它再次啟用，即使在執行階段，如本文稍早所述。

**如何從 IIS 收集失敗要求記錄檔？**

根據預設，IIS 不會收集失敗要求記錄檔。 您可以將 IIS 設定，以藉由編輯您的 web 角色的 web.config 檔案收集失敗要求記錄檔。

**我無法從 OnStart 之類的 RoleEntryPoint 方法取得追蹤資訊。有什麼問題？**

方法**RoleEntryPoint** WAIISHost.exe，未在 IIS 中的內容中呼叫。 啟用追蹤通常並不適用的 web.config 中設定資訊。 若要解決此問題，請將.config 檔案新增至您的 web 角色專案，並將檔案命名以符合輸出組件，其中包含**RoleEntryPoint**程式碼。 在預設 web 角色專案中，.config 檔案的名稱應該是 WAIISHost.exe.config。將下列幾行新增至此檔案：

```
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

在 **屬性**視窗中，將**複製到輸出目錄**屬性設**永遠複製**。

## <a name="next-steps"></a>後續步驟
若要深入了解 Azure 中診斷記錄，請參閱[在 Azure 雲端服務和虛擬機器中啟用診斷](/azure/cloud-services/cloud-services-dotnet-diagnostics.md)並[針對 Azure App Service 中的 Web 應用程式啟用診斷記錄](/azure/app-service/web-sites-enable-diagnostic-log)。

