---
title: 瀏覽和使用伺服器總管中管理儲存體資源 |Microsoft Docs
description: 瀏覽和使用伺服器總管中管理儲存體資源
author: ghogen
manager: douge
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 00229cd88ddcab4d2d59ae40202620c374415e4b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002070"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>使用伺服器總管來瀏覽及管理儲存體資源

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>總覽

如果您已安裝 Azure Tools for Microsoft Visual Studio，您可以檢視 blob、 佇列和資料表資料從您的儲存體帳戶的 Azure。 Azure**儲存體**伺服器總管 中的節點會顯示您的本機儲存體模擬器帳戶和其他 Azure 儲存體帳戶中的資料。

若要檢視 在 Visual Studio 中，伺服器總管 中，功能表列上，選取**檢視** > **伺服器總管**。 **儲存體**節點會顯示存在於每個 Azure 訂用帳戶或您已連線到的憑證下的儲存體帳戶。 如果您的儲存體帳戶未出現，您可以新增它的指示[本文稍後的](#add-storage-accounts-by-using-server-explorer)。

從 Azure SDK 2.7 開始，您也可以使用雲端總管 來檢視和管理您的 Azure 資源。 如需詳細資訊，請參閱 <<c0> [ 使用雲端總管管理 Azure 資源](vs-azure-tools-resources-managing-with-cloud-explorer.md)。

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>檢視及管理 Visual Studio 中的儲存體資源

伺服器總管 會自動顯示您的儲存體模擬器帳戶中的 blob、 佇列和資料表的清單。 儲存體模擬器帳戶會列在 [伺服器總管] 下方**儲存體**節點，做為**開發**節點。

若要查看儲存體模擬器帳戶的資源，請展開**開發**節點。 當您展開時，如果尚未啟動儲存體模擬器**開發** 節點，它會自動啟動。 此程序可能需要幾秒鐘的時間。 您可以繼續在儲存體模擬器啟動時，Visual Studio 的其他區域中運作。

若要檢視儲存體帳戶中的資源，請展開 [儲存體帳戶的節點，在伺服器總管] 中，您看到**Blob**，**佇列**，並**資料表**節點。

## <a name="work-with-blob-resources"></a>使用 blob 資源

**Blob**節點會顯示一份所選的儲存體帳戶的容器。 Blob 容器包含 blob 檔案，並將這些 blob 組織成資料夾和子資料夾。 如需詳細資訊，請參閱 <<c0> [ 如何使用.NET 的 Blob 儲存體](/azure/storage/blobs/storage-dotnet-how-to-use-blobs)。

### <a name="to-create-a-blob-container"></a>若要建立 blob 容器

1. 開啟捷徑功能表**Blob**節點，，然後選取**建立 Blob 容器**。
1. 在 **建立 Blob 容器**對話方塊方塊中，輸入新容器的名稱。  
1. 選取 Enter 鍵盤上，您可以按一下或點選 儲存的 blob 容器的 名稱 欄位之外。

   > [!NOTE]
   > Blob 容器名稱必須以數字 (0-9) 或小寫字母 (a 到 z) 開頭。

### <a name="to-delete-a-blob-container"></a>若要刪除的 blob 容器

開啟您想要移除此項目，然後選取 blob 容器的捷徑功能表**刪除**。

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>若要顯示的項目清單中的 blob 容器

在清單中，開啟 blob 容器名稱的捷徑功能表，然後選取**開啟**。

當您檢視 blob 容器的內容時，它就會出現在稱為 blob 容器檢視的索引標籤上。

![Blob 容器檢視](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

您可以使用 blob 容器檢視右上角的按鈕來執行 blob 上的下列作業：

* 輸入篩選值，並加以套用。
* 重新整理容器中 blob 清單。
* 上傳的檔案。
* 刪除 blob。 （從 blob 容器中刪除檔案並不會刪除基礎的檔案。 它只會移除它的 blob 容器。）
* 開啟 blob。
* 將 blob 儲存到本機電腦。

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>若要建立 blob 容器中的資料夾或子資料夾

1. 在 [雲端總管] 中選擇 blob 容器。 在 容器 視窗中，選取**上傳 Blob**  按鈕。

1. 在 [**上傳新的檔案**對話方塊方塊中，選取**瀏覽**按鈕來指定您想要上傳的檔案，然後輸入資料夾名稱中的**資料夾 （選擇性）** ] 方塊中。

   ![將檔案上傳至 blob 資料夾](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   您可以依照相同的步驟來新增容器資料夾的子資料夾。 如果您未指定資料夾名稱，檔案會上傳至 blob 容器的最上層。 檔案會出現在容器中指定的資料夾。

   ![新增至 blob 容器的資料夾](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. 按兩下資料夾或選取 Enter 以查看資料夾的內容。 當您使用容器的資料夾時，您可以移回至容器的根目錄藉**開啟上層目錄**（箭頭） 按鈕。

### <a name="to-delete-a-container-folder"></a>若要刪除容器資料夾

刪除資料夾中的所有檔案。

因為 blob 容器中的資料夾是虛擬資料夾，您無法建立空的資料夾。 您也無法刪除資料夾並刪除其檔案內容，但必須改為刪除資料夾並刪除該資料夾本身的整個內容。

### <a name="to-filter-blobs-in-a-container"></a>若要篩選在容器中的 blob

您可以篩選會顯示藉由指定共同首碼的 blob。

例如，如果您輸入的前置詞**hello**篩選 文字方塊中，然後選取**Execute** (**！**) 按鈕，以"hello"開頭的 blob 會出現。

![篩選文字方塊](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

[篩選] 文字方塊中會區分大小寫，且不支援使用萬用字元篩選。 Blob 可以只利用前置詞篩選。 如果您要使用分隔符號在虛擬階層中組織 blob，前置詞可以包含分隔符號。 例如，篩選前置詞"HelloFabric /"會傳回所有以該字串開頭的 blob。

### <a name="to-download-blob-data"></a>若要下載 blob 資料

在 [雲端總管] 中，使用下列方法之一：

* 開啟一或多個 blob 的捷徑功能表，然後選取**開啟**。
* 選擇 blob 名稱，然後選取**開啟** 按鈕。
* 按兩下 blob 名稱。

Blob 下載進度會顯示在**Azure 活動記錄檔**視窗。

Blob 會在該檔案類型的預設編輯器中開啟。 如果作業系統辨識出的檔案類型，則會在本機安裝的應用程式中開啟檔案。 否則，系統會提示選擇適用於 blob 的檔案類型的應用程式。 下載 blob 時，會建立本機檔案會標示為唯讀。

Blob 資料會在本機快取，並針對在 Azure Blob 儲存體 blob 的上次修改時間檢查。 如果自上次下載 blob 已更新，系統會再次下載。 否則，從本機磁碟載入 blob。

根據預設，blob 會下載至暫存目錄。 若要下載 blob 到特定的目錄中，開啟所選的 blob 名稱的捷徑功能表，然後選取**另存新檔**。 當您以這種方式儲存 blob 時，blob 檔案尚未開啟，並將本機檔案會利用讀/寫屬性建立。

### <a name="to-upload-blobs"></a>若要上傳 blob

若要上傳 blob，請選取**上傳 Blob**按鈕當容器開啟以檢視 blob 容器中加以檢視時。

您可以選擇要上傳的一或多個檔案，您可以上傳任何類型的檔案。 **Azure 活動記錄檔**視窗會顯示上傳的進度。 如需如何使用 blob 資料的詳細資訊，請參閱[如何在.NET 中使用 Azure Blob 儲存體](http://go.microsoft.com/fwlink/p/?LinkId=267911)。

### <a name="to-view-logs-transferred-to-blobs"></a>若要檢視記錄傳送輸到 blob

如果您使用 Azure 診斷記錄資料從 Azure 應用程式，而且您已將記錄傳輸至儲存體帳戶，您會看到 Azure 為這些記錄檔建立的容器。 在 [伺服器總管] 中檢視這些記錄檔是輕鬆地找出您的應用程式的問題，尤其是如果它已部署至 Azure。

如需有關 Azure 診斷的詳細資訊，請參閱 <<c0> [ 收集記錄資料使用 Azure 診斷](https://msdn.microsoft.com/library/azure/gg433048.aspx)。

### <a name="to-get-the-url-for-a-blob"></a>若要取得 blob 的 URL

開啟 blob 的捷徑功能表，然後選取**複製 URL**。

### <a name="to-edit-a-blob"></a>若要編輯 blob

選取 blob，然後選取**開啟 Blob**  按鈕。

檔案會下載到暫存位置，並在本機電腦上開啟。 在變更之後，再次上傳 blob。

## <a name="work-with-queue-resources"></a>使用佇列資源

儲存體服務佇列裝載在 Azure 儲存體帳戶。 您可以使用它們來讓您的雲端服務角色進行通訊的訊息傳遞機制彼此及與其他服務。 透過雲端服務，並透過 web 服務是外部用戶端，您可以透過程式設計方式存取佇列。 您也可以在 Visual Studio 中使用伺服器總管 來直接存取佇列。

當您開發使用佇列的雲端服務時，您可能想要使用 Visual Studio 來建立佇列，並且使用它們以互動方式開發及測試您的程式碼時。

在 [伺服器總管] 中，您可以檢視儲存體帳戶中的佇列、 建立和刪除佇列、 開啟佇列以檢視其訊息，以及將訊息加入佇列。 當您開啟佇列進行檢視時，您可以檢視個別訊息，，而且您也可以使用左上角的按鈕在佇列上執行下列動作：

* 重新整理佇列的檢視。
* 將訊息加入佇列。
* 清除佇列的最上層的訊息。
* 清除整個佇列。

下圖顯示含有兩個訊息的佇列：

![檢視佇列](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

如需有關儲存體服務佇列，請參閱[開始使用.NET 的 Azure 佇列儲存體使用](http://go.microsoft.com/fwlink/?LinkID=264702)。 如需 web 服務的儲存體服務佇列，請參閱[佇列服務概念](http://go.microsoft.com/fwlink/?LinkId=264788)。 如需如何使用 Visual Studio，將訊息傳送至儲存體服務佇列的資訊，請參閱[傳送訊息至儲存體服務佇列](https://docs.microsoft.com/azure/visual-studio/vs-storage-cloud-services-getting-started-queues)。

> [!NOTE]
> 儲存體服務佇列是與 Azure 服務匯流排佇列不同。 如需有關服務匯流排佇列的詳細資訊，請參閱 <<c0> [ 服務匯流排佇列、 主題和訂用帳戶](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions)。

## <a name="work-with-table-resources"></a>使用資料表資源

Azure 資料表儲存體可儲存大量的結構化資料。 服務會接受已驗證的呼叫從 Azure 雲端內外的 NoSQL 資料存放區。 Azure 資料表很適合用來儲存結構化、 非關聯式資料。

### <a name="to-create-a-table"></a>若要建立資料表

1. 在 [雲端總管] 中，選取**資料表**節點，然後選取儲存體帳戶，以及**Create Table**。
1. 在  **Create Table**對話方塊方塊中，輸入資料表的名稱。

### <a name="to-view-table-data"></a>若要檢視資料表的資料

1. 在 [雲端總管] 中，開啟**Azure**節點，然後再開啟**儲存體**節點。
1. 開啟儲存體帳戶節點也有興趣，然後再開啟**資料表**看到一份資料表儲存體帳戶的節點。
1. 開啟資料表的捷徑功能表，然後選取**檢視表**。

    ![方案總管 中的 Azure 資料表](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

資料表被依 （資料列中顯示） 的實體和屬性 （資料行中顯示）。 例如下, 圖顯示資料表設計工具中所列的實體。

### <a name="to-edit-table-data"></a>若要編輯資料表資料

在 資料表設計工具中，開啟實體 （單一資料列） 或屬性 （單一儲存格），快顯功能表，然後選取**編輯**。

    ![Add or edit a table entity](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

單一資料表中的實體不一定要有相同的一組屬性 （資料行）。 請記住下列的限制檢視和編輯資料表資料：

* 您無法檢視或編輯二進位資料 (`type byte[]`)，但您可以將其儲存在資料表中。
* 您無法編輯**PartitionKey**或是**RowKey**值，因為在 Azure 中的資料表儲存體不支援這項操作。
* 您無法建立屬性，稱為**時間戳記**。 Azure 儲存體服務會使用該名稱的屬性。
* 如果您輸入**DateTime**值，您必須遵循適合您的電腦的地區和語言設定的格式 (例如，MM/DD/YYYY hh: mm: [AM |PM] 適用於美國英文)。

### <a name="to-add-entities"></a>若要加入實體

1. 在 [資料表設計工具中，選取**新增實體**] 按鈕。

    ![新增實體 按鈕](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. 在 **新增實體**對話方塊方塊中，輸入的值**PartitionKey**並**RowKey**屬性。

    ![新增實體對話方塊](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    請小心輸入這些值。 除非您刪除此實體並且再次將其加入，關閉對話方塊之後，您無法變更它們。

### <a name="to-filter-entities"></a>若要篩選實體

您可以自訂出現在資料表中，如果您使用查詢產生器的實體集。

1. 若要開啟 [查詢產生器]，請開啟任一表格進行檢視。
1. 選取 **查詢產生器**資料表檢視工具列上的按鈕。

    **查詢產生器** 對話方塊隨即出現。 下圖會顯示正在建立的查詢，查詢產生器中。

    ![查詢產生器](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. 當您完成建立查詢，關閉對話方塊。 產生的文字格式的查詢會出現在文字方塊中，做為 WCF Data Services 篩選條件。
1. 若要執行查詢，請選取綠色的三角形圖示。

您也可以篩選出現在資料表設計工具 」 如果您輸入 WCF Data Services 篩選字串，直接在篩選文字方塊中的實體資料。 這種類型的字串類似於 SQL WHERE 子句，但會傳送至伺服器的 HTTP 要求。 如需有關如何建構篩選字串的資訊，請參閱[Constructing 資料表設計工具的篩選字串](https://docs.microsoft.com/azure/vs-azure-tools-table-designer-construct-filter-strings)。

下圖顯示有效的篩選字串的範例：

![篩選字串](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>重新整理儲存體資料

當伺服器總管 連接至或從儲存體帳戶中取得資料時，此作業最多可能需要一分鐘的時間才能完成。 如果無法連線伺服器總管 中，此作業可能會逾時。擷取資料時，您可以繼續在 Visual Studio 的其他部分中運作。 若要取消此作業，如果費時太久，請選取**停止重新整理**伺服器總管 工具列上的按鈕。

### <a name="to-refresh-blob-container-data"></a>若要重新整理 blob 容器資料

* 選取 [ **Blob**下方的節點**儲存體**，然後選取**重新整理**伺服器總管] 工具列上的按鈕。
* 若要重新整理顯示的 blob 清單，請選取**Execute**  按鈕。

### <a name="to-refresh-table-data"></a>若要重新整理資料表資料

* 選取 [**資料表**下方的節點**儲存體**，然後選取**重新整理**伺服器總管] 工具列上的按鈕。
* 若要重新整理資料表設計工具中顯示的實體清單，請選取**Execute**資料表設計工具中的按鈕。

### <a name="to-refresh-queue-data"></a>若要重新整理佇列資料

選取 [**佇列**下方的節點**儲存體**，然後選取**重新整理**伺服器總管] 工具列上的按鈕。

### <a name="to-refresh-all-items-in-a-storage-account"></a>若要重新整理儲存體帳戶中的所有項目

選擇帳戶名稱，然後選取**重新整理**伺服器總管 工具列上的按鈕。

## <a name="add-storage-accounts-by-using-server-explorer"></a>使用 [伺服器總管] 新增儲存體帳戶

有兩種方式可使用 [伺服器總管] 新增儲存體帳戶。 您可以在您 Azure 訂用帳戶中的儲存體帳戶，或您可以附加現有的儲存體帳戶。

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>若要使用伺服器總管 中建立儲存體帳戶

1. 在 [伺服器總管] 中，開啟捷徑功能表**儲存體**節點，，然後選取**建立儲存體帳戶**。

1. 在 **建立儲存體帳戶**對話方塊方塊中，選取或輸入下列資訊：

   * 您要將儲存體帳戶新增 Azure 訂用帳戶。
   * 您想要用於新的儲存體帳戶名稱。
   * 區域或同質群組 （例如美國西部或東亞）。
   * 您想要使用儲存體帳戶，例如複寫的類型本地備援。

   ![建立 Azure 儲存體帳戶](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. 選取 [建立]。

新的儲存體帳戶會出現在**儲存體**方案總管 中的清單。

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>若要使用伺服器總管附加現有的儲存體帳戶

1. 在 [伺服器總管] 中，開啟捷徑功能表的 azure**儲存體**節點，，然後選取**附加外部儲存體**。

    ![新增現有的儲存體帳戶](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. 在 **建立儲存體帳戶**對話方塊方塊中，選取或輸入下列資訊：

   * 您想要附加的現有儲存體帳戶名稱。
   * 選取的儲存體帳戶金鑰。 當您選取的儲存體帳戶時，這個值通常會提供給您。 如果您想要 Visual Studio 記住儲存體帳戶金鑰，請選取**記住帳戶金鑰**核取方塊。
   * 要用於連接至儲存體帳戶，例如 HTTP、 HTTPS 或自訂端點的通訊協定。 如需有關自訂端點的詳細資訊，請參閱 <<c0> [ 如何設定連接字串](https://msdn.microsoft.com/library/azure/ee758697.aspx)。

### <a name="to-view-the-secondary-endpoints"></a>若要檢視其次要端點

如果您使用 建立儲存體帳戶**讀取權限異地備援**複寫選項，您可以檢視其次要端點開啟帳戶名稱的捷徑功能表，然後選取**屬性**.

![儲存體次要端點](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>若要從伺服器總管移除儲存體帳戶

在 [伺服器總管] 中，開啟帳戶名稱的捷徑功能表，然後按**刪除**。 

如果您刪除儲存體帳戶，也會移除任何已儲存的金鑰資訊，該帳戶。

如果您從 [伺服器總管] 刪除儲存體帳戶，它不會影響您的儲存體帳戶或任何它所包含的資料。 它只會從伺服器總管 移除參考。 若要永久刪除儲存體帳戶，請使用[Azure 入口網站](https://portal.azure.com/)。

## <a name="next-steps"></a>後續步驟

若要深入了解如何使用 Azure 儲存體服務，請參閱[存取 Azure 儲存體服務](https://msdn.microsoft.com/library/azure/ee405490.aspx)。
