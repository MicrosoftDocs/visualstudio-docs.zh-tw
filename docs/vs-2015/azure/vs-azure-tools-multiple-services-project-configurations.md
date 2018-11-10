---
title: 設定 Azure 專案使用多個服務組態 |Microsoft Docs
description: 了解如何透過變更 ServiceDefinition.csdef、 ServiceConfiguration.Local.cscfg 和 ServiceConfiguration.Cloud.cscfg 檔案來設定 Azure 雲端服務專案。
author: ghogen
manager: douge
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: f309c2a960d011601a9fdd41e29d767c667de838
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002003"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>在 Visual Studio 中設定您的 Azure 專案以使用多個服務設定

在 Visual Studio 中的 Azure 雲端服務專案包含三個組態檔： `ServiceDefinition.csdef`， `ServiceConfiguration.Local.cscfg`，和`ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef` 部署至 Azure 來描述需求的雲端服務和其角色，以及提供適用於所有執行個體的設定。 可以在執行階段使用 Azure 服務裝載執行階段 API 來讀取設定。 雲端服務已停止時，才可以在 Azure 上更新此檔案。
- `ServiceConfiguration.Local.cscfg` 和`ServiceConfiguration.Cloud.cscfg`提供值的定義中的設定檔案，並指定要針對每個角色執行的執行個體數目。 "Local"檔案包含用於本機偵錯; 的值「 雲端 」 檔案部署到 Azure 作為`ServiceConfiguration.cscfg`，並提供伺服器環境的設定。 在 Azure 中執行您的雲端服務時，可以更新此檔案。

管理和使用適用於角色的屬性頁的 Visual Studio 中修改組態設定 (以滑鼠右鍵按一下角色，然後選取**屬性**，或按兩下角色)。 變更受限於中選擇的任何組態**服務組態**下拉式清單。 Web 和背景工作角色的屬性很類似，除了在下列各節所述。

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

如需服務定義檔和服務組態檔的基礎結構描述資訊，請參閱[.csdef XML 結構描述](/azure/cloud-services/schema-csdef-file.md)並[.cscfg XML 結構描述](/azure/cloud-services/schema-cscfg-file.md)文章。 如需服務組態的詳細資訊，請參閱[如何設定雲端服務](/azure/cloud-services/cloud-services-how-to-configure-portal)。


## <a name="configuration-page"></a>組態頁面

### <a name="service-configuration"></a>服務組態

選取`ServiceConfiguration.*.cscfg`檔案的變更會影響。 根據預設，有本機和雲端的變體，而且您可以使用**管理...** 命令來複製、 重新命名和移除組態檔。 這些檔案會新增至您的雲端服務專案，並會出現在**方案總管 中**。 不過，重新命名或移除組態可以完成只能從這個控制項。

### <a name="instances"></a>執行個體

設定**執行個體**計數屬性，服務應該執行此角色的執行個體數目。

設定**VM 大小**屬性設**超小型**，**小型**，**中型**，**大型**，或  **超大型**。  如需詳細資訊，請參閱 <<c0> [ 雲端服務的大小](/azure/cloud-services/cloud-services-sizes-specs)。

### <a name="startup-action-web-role-only"></a>啟動動作 （僅限 Web 角色）

設定這個屬性來指定 Visual Studio 在您開始偵錯時，應該啟動網頁瀏覽器的 HTTP 端點或 HTTPS 端點，或兩者。

**HTTPS 端點**選項才會提供您已為您的角色定義 HTTPS 端點。 您可以定義 HTTPS 端點**端點**屬性頁。

如果您已新增 HTTPS 端點，預設會啟用 HTTPS 端點選項，Visual Studio 會啟動此端點的瀏覽器，您開始偵錯時，除了在瀏覽器的 HTTP 端點，假設這兩種啟動選項會啟用。

### <a name="diagnostics"></a>診斷

根據預設，Web 角色啟用診斷。 Azure 雲端服務專案和儲存體帳戶會設定為使用本機儲存體模擬器。 當您準備好要部署至 Azure 時，您可以選取產生器 按鈕 (**...**) 改為使用 Azure 儲存體。 隨選或自動排程的間隔，您可以將診斷資料傳輸至儲存體帳戶。 如需有關 Azure 診斷的詳細資訊，請參閱 <<c0> [ 在 Azure 雲端服務和虛擬機器中啟用診斷](/azure/cloud-services/cloud-services-dotnet-diagnostics)。

## <a name="settings-page"></a>設定頁面

在 [**設定**] 頁面上，您可以將設定加入設定做為名稱 / 值組。 角色中執行的程式碼可以讀取您在使用所提供的類別的執行階段的組態設定的值[Azure Managed 程式庫](http://go.microsoft.com/fwlink?LinkID=171026)，具體來說， [GetConfigurationSettingValue](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.getconfigurationsettingvalue.aspx)方法。

### <a name="configuring-a-connection-string-for-a-storage-account"></a>設定儲存體帳戶的連接字串

連接字串是儲存體模擬器或 Azure 儲存體帳戶提供連接和驗證資訊的設定。 每當角色中的程式碼存取 Azure 儲存體 （blob、 佇列或資料表），它會需要連接字串。

> [!Note]
> Azure 儲存體帳戶的連接字串必須使用已定義的格式 (請參閱[設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string))。

您可以設定連接字串以使用本機儲存體，如有需要當您部署應用程式，然後設定 Azure 儲存體帳戶的雲端服務。 若未正確設定連接字串可能會導致您的角色無法啟動，或初始化、 忙碌和停止狀態間循環。

若要建立的連接字串，請選取**新增設定**並設定**型別**至 「 連接字串 」。

針對新的或現有的連接字串中，選取  **...*** 右側**值**欄位，以開啟**建立的儲存體連接字串**對話方塊：

1. 底下**使用連接**，選擇**您的訂用帳戶**選項以從訂用帳戶選取儲存體帳戶。 Visual Studio 接著會取得儲存體帳戶認證，自動從`.publishsettings`檔案。
1. 選取**手動輸入的認證**可讓您指定的帳戶名稱和金鑰直接使用從 Azure 入口網站的資訊。 若要複製帳戶金鑰：
    1. 瀏覽至儲存體帳戶，在 Azure 入口網站，然後選取**管理金鑰**。
    1. 若要複製帳戶金鑰，請瀏覽至儲存體帳戶，在 Azure 入口網站中，選取**設定 > 存取金鑰**，然後使用 [複製] 按鈕將主要存取金鑰複製到剪貼簿。
1. 選取其中一個連線選項。 **指定自訂端點**會要求您指定特定的 Url，如 blob、 資料表和佇列。 自訂端點可讓您使用[自訂網域](/azure/storage/blobs/storage-custom-domain-name.md)以及更精確地控制存取。 請參閱[設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string)。
1. 選取  **確定**，然後**檔案 > 儲存**利用新的連接字串更新組態。

同樣地，當您發行至 Azure 的應用程式時，選擇包含連接字串之 Azure 儲存體帳戶的服務組態。 發行您的應用程式之後，請確認應用程式運作如預期般對 Azure 儲存體服務。

如需如何更新服務組態的詳細資訊，請參閱下節[管理的儲存體帳戶連接字串](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts)。

## <a name="endpoints-page"></a>端點頁面

Web 角色通常會有單一的 HTTP 端點連接埠 80 上。 相反地，背景工作角色，可以有任意數目的 HTTP、 HTTPS 或 TCP 端點。 端點可以是輸入的端點，可供外部用戶端或可用於服務中執行其他角色的內部端點。

- 若要讓 HTTP 端點可供外部用戶端和網頁瀏覽器，將端點類型變更為輸入，並指定名稱和公用連接埠號碼。
- 若要讓 HTTPS 端點可供外部用戶端和網頁瀏覽器，將端點類型變更為**輸入**，並指定名稱、 公用連接埠號碼，以及管理憑證名稱。 您也必須定義憑證上**憑證**之前您可以指定管理憑證的屬性頁。 
- 若要讓雲端服務中的其他角色適用於內部存取端點，將端點類型變更為內部，並指定名稱和可能的私用連接埠，這個端點。

## <a name="local-storage-page"></a>本機儲存體頁面

您可以使用**本機儲存體**保留一或多個角色的本機儲存體資源的屬性頁。 本機儲存體資源是 Azure 的虛擬機器角色的執行個體執行所在的檔案系統中的保留的目錄。

## <a name="certificates-page"></a>憑證頁面

**憑證**屬性頁會將您的服務組態中的憑證的相關資訊。 請注意，您的憑證不會封裝與您的服務;您必須分別上傳憑證至 Azure 中透過[Azure 入口網站](http://portal.azure.com)。

新增的憑證，是在您的服務組態中將憑證的相關資訊。 憑證未隨附服務;您必須將您的憑證，透過 Azure 入口網站分別上傳。

若要將憑證與角色產生關聯，提供憑證的名稱。 您可以使用此名稱來參照憑證上設定 HTTPS 端點時**端點**頁面。 接下來，指定 憑證存放區是否**本機電腦**或是**目前使用者**和存放區的名稱。 最後，輸入憑證的指紋。 如果憑證是在目前使用者 \ 個人 (My) 存放區，您可以輸入從填入的清單中選取憑證的憑證的指紋。 如果它位於其他任何位置，請以手動方式輸入指紋值。

當您將憑證從憑證存放區時，所有中繼憑證會自動新增至您的組態設定。 此外，這些中繼憑證必須上傳至 Azure，以正確地設定服務的 SSL。

在雲端執行時，才，與您的服務相關聯的管理憑證會套用至您的服務。 當在本機開發環境中執行您的服務時，它會使用計算模擬器所管理的標準憑證。
