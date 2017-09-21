---
title: "使用 Visual Studio 中的資料集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.DataSet"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "快取 [Visual Studio], 資料集"
  - "區分大小寫, 資料集"
  - "子資料錄"
  - "條件約束 [Visual Basic], 資料集"
  - "資料集中的目前資料錄"
  - "資料配接器, 填入資料集"
  - "資料快取, 資料集"
  - "資料關聯性"
  - "資料庫 [Visual Basic], 更新"
  - "DataRelation 物件, 資料集"
  - "DataSet 類別"
  - "DataSet 類別, 關於資料集"
  - "資料集 [Visual Basic]"
  - "資料集 [Visual Basic], 擴充的屬性"
  - "資料集 [Visual Basic], 填滿"
  - "資料集 [Visual Basic], msprop"
  - "資料集 [Visual Basic], namespace"
  - "資料集 [Visual Basic], 填入"
  - "資料集 [Visual Basic], 關聯性"
  - "擴充的屬性, 在具類型資料集中"
  - "外部索引鍵, 資料集"
  - "主從式資料表, 資料集"
  - "msprop"
  - "資料集中的父資料錄"
  - "關聯資料表"
  - "關聯資料表, 資料集"
  - "關聯性, 資料集"
  - "結構描述 [Visual Basic], 資料集"
  - "具類型資料集"
  - "具類型資料集, 與不具類型資料集比較"
  - "唯一的條件約束 (資料集)"
  - "不具類型的資料集"
  - "不具類型的資料集, 與具類型資料集比較"
  - "更新資料集, 關於資料集更新"
  - "XML [Visual Basic], 資料集"
  - "XML 結構描述, 關於 XML 結構描述與資料集"
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 49
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 Visual Studio 中的資料集
資料集是指包含資料表的物件，您可以暫時將資料儲存在裡面，以供應用程式使用。  如果應用程式需要處理資料，您可以將資料載入到資料集中，這樣可為應用程式提供所要使用之資料的本機 In\-Memory 快取。  即使應用程式中斷與資料庫的連接，您還是可以處理資料集中的資料。  資料集會維護與其資料變更相關的資訊，以便在應用程式重新連接時能夠追蹤更新，並將更新傳回資料庫。  
  
 下列主題提供有關使用 Visual Studio 中資料集的詳細資訊：  
  
|主題|描述|  
|--------|--------|  
|[建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)|解釋建立資料集的設計階段工具。|  
|[如何：建立具類型資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)|說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的設計工具，建立具型別的資料集。|  
|[如何：擴充資料集的功能](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|提供為資料集建立部分類別的步驟，讓您在設計工具產生的程式碼之外加入更多的程式碼。|  
|[如何：在 DataSet 設計工具中開啟資料集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)|解釋如何從 \[**方案總管**\] 和 \[**資料來源**\] 視窗開啟資料集。|  
|[如何：編輯資料集](../Topic/How%20to:%20Edit%20a%20Dataset.md)|解釋如何使用 \[**DataSet 設計工具**\] 編輯資料集當中的物件。|  
|[逐步解說：以 DataSet 設計工具建立資料集](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)|提供在沒有 \[**資料來源組態精靈**\] 協助之下，建立具型別資料集的逐步指示。|  
|[設計 DataTable](../data-tools/designing-datatables.md)|提供主題的連結，這些主題將說明如何以設計階段工具建立和編輯資料的資料表。|  
|[資料集中的關聯性](../data-tools/relationships-in-datasets.md)|提供主題的連結，這些主題將說明如何以設計階段工具建立和編輯資料關聯。|  
|[TableAdapter](../Topic/TableAdapters.md)|提供主題的連結，這些主題將說明如何以設計階段工具建立和編輯 TableAdapter。|  
|[使用多層式架構應用程式中的資料集](../data-tools/work-with-datasets-in-n-tier-applications.md)|說明 N\-Tier 應用程式為何，以及哪些功能可用於處理 N\-Tier 應用程式中的資料集。|  
  
 <xref:System.Data.DataSet> 的結構和關聯式資料庫類似；它會公開資料表、資料列、條件約束和關聯性的階層式物件模型。  
  
 資料集可以是具型別或不具型別   \(如需詳細資訊，請參閱底下標題為＜具型別與不具型別的資料集＞一節\)。具型別資料集是從 .xsd 檔案衍生其結構描述 \(資料表和資料行結構\)，因此比較容易據以撰寫程式。  您可在應用程式中使用具型別或不具型別資料集。  但 Visual Studio 對具型別資料集有較多的工具支援，而且使用具型別資料集撰寫程式更為容易，並且較不會出現錯誤。  
  
 您可以建立具型別之資料集，其方式是執行[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)，或是透過 \[**專案**\] 功能表上的 \[**加入新項目**\] 命令來加入 \[**資料集**\] 項目。  如需詳細資訊，請參閱 [如何：建立具類型資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
 您可以建立不具型別之資料集，其方式是從 \[**工具箱**\] 將 \[**資料集**\] 項目拖曳到 [Windows Forms Designer](http://msdn.microsoft.com/zh-tw/3c3d61f8-f36c-4d41-b9c3-398376fabb15)或[Component Designer](../Topic/Component%20Designer.md)上。  
  
 在建立資料集之後，請在 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)中加以編輯。  
  
 您可以使用下列 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 命名空間部分，建立及處理具型別和不具型別的資料集。  
  
 ![系統資料 Dataset 命名空間](../data-tools/media/vbdatasetnamspace.png "vbDataSetNamspace")  
資料集位在 System.Data 命名空間中  
  
 資料集物件，是透過標準的程式設計建構 \(例如屬性和集合\) 公開的。  例如：  
  
-   <xref:System.Data.DataSet> 類別包含資料表的 <xref:System.Data.DataTableCollection> 集合，以及 <xref:System.Data.DataRelation> 物件的 <xref:System.Data.DataRelationCollection> 集合。  
  
-   <xref:System.Data.DataTable> 類別包含資料列的 <xref:System.Data.DataRowCollection> 集合、資料行的 <xref:System.Data.DataColumnCollection> 集合，以及資料關聯的 <xref:System.Data.DataTable.ChildRelations%2A> 和 <xref:System.Data.DataTable.ParentRelations%2A> 集合。  
  
-   <xref:System.Data.DataRow> 類別包含 <xref:System.Data.DataRow.RowState%2A> 屬性，其值是用來指出第一次從資料庫載入資料表之後，資料列是否已變更和如何變更。  <xref:System.Data.DataRow.RowState%2A> 屬性的可能值包括 <xref:System.Data.DataRowState>、<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState> 和 <xref:System.Data.DataRowState>。  
  
## 將資料填入資料集  
 資料集預設不含任何實際資料；  將資料填入資料集，是指將資料載入組成資料集所的個別 <xref:System.Data.DataTable> 物件。  您可以執行 TableAdapter 查詢或資料配接器 \(例如，<xref:System.Data.SqlClient.SqlDataAdapter>\) 命令，來填入資料表。  當您將資料填入資料集時，會引發各種事件、檢查條件約束等等。  如需將資料載入資料集的詳細資訊，請參閱[將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)。  
  
 當您從[資料來源視窗](../Topic/Data%20Sources%20Window.md)將項目拖曳到 Windows 應用程式的表單上時，用來填入資料集的程式碼會自動加入到表單載入事件處理常式中。  如需詳細資訊，請完成下列逐步解說：[逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)。  
  
 將 TableAdapter 填入資料集的範例：  
  
 [!CODE [VbRaddataDatasets#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#1)]  
  
 您可利用下列幾種方式來填入資料集：  
  
-   如果您使用設計階段工具 \(例如資料精靈\) 建立資料集，請呼叫 TableAdapter 的 `Fill` 方法   \(建立 TableAdapter 時，隨附有預設的 `Fill` 方法，但您可以選擇變更此名稱，所以實際的方法名稱可能會不同\)。 如需詳細資訊，請參閱 [如何：以資料填入資料集](../data-tools/how-to-fill-a-dataset-with-data.md)的＜使用 TableAdapter 填入資料集＞章節。  
  
-   呼叫 <xref:System.Data.Common.DataAdapter> 的 `Fill` 方法。  如需詳細資訊，請參閱[從 DataAdapter 填入 DataSet](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md)。  
  
-   手動填入資料集當中的資料表，方式是建立 <xref:System.Data.DataRow> 物件，並將其加入至資料表的 <xref:System.Data.DataRowCollection> 集合   \(您只能在執行階段這麼做，不可以在設計階段設定 <xref:System.Data.DataRowCollection> 集合\)。 如需詳細資訊，請參閱 [將資料加入至 DataTable](../Topic/Adding%20Data%20to%20a%20DataTable.md)。  
  
-   將 XML 文件或資料流讀入資料集。  如需詳細資訊，請參閱 <xref:System.Data.DataSet.ReadXml%2A> 方法。  如需範例，請參閱 [逐步解說：將 XML 資料讀入資料集](../data-tools/read-xml-data-into-a-dataset.md)。  
  
-   合併 \(複製\) 某個資料集與其他資料集的內容。  如果您的應用程式從不同來源 \(例如不同 XML Web Service\) 取得資料集，這種案例會很有用，但需要將這些資料集合併至單一資料集。  如需詳細資訊，請參閱 [合併 DataSet 內容](../Topic/Merging%20DataSet%20Contents.md)。  
  
-   合併 \(複製\) 某個 <xref:System.Data.DataTable> 與其他資料表的內容。  
  
## 將資料集中的資料存回資料庫  
 在變更資料集當中的資料錄時，必須將變更寫回資料庫。  若要將變更從資料集寫入資料庫，您必須呼叫 TableAdapter 或 <xref:System.Data.Common.DataAdapter> \(在資料集與其對應資料庫之間通訊\) 的 `Update` 方法。  
  
 當您使用 Visual Studio 中的資料設計工具時，請呼叫 TableAdapter 的 Update 方法，並傳入您想要儲存的資料表，將資料送回資料庫。  例如：  
  
 [!CODE [VbRaddataDatasets#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#2)]  
  
 為了要能夠對更新程序有更佳的控制能力，請呼叫其中一個 TableAdapter DBDirect 方法，讓您針對每一個資料列傳入個別值。  如需詳細資訊，請參閱[如何：使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)和 [逐步解說：使用 TableAdapter DBDirect 方法儲存資料](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)。  
  
 用來管理個別資料錄的 <xref:System.Data.DataRow> 類別包含 <xref:System.Data.DataRow.RowState%2A> 屬性，其值是用來指出第一次從資料庫載入資料表之後，資料列是否已變更以及如何變更。  可能值包括 <xref:System.Data.DataRowState>、<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState> 和 <xref:System.Data.DataRowState>。  TableAdapter 和 <xref:System.Data.Common.DataAdapter> 的 `Update` 方法會檢查 <xref:System.Data.DataRow.RowState%2A> 屬性的值，以判斷哪些資料錄需要寫入資料庫，以及應叫用哪個特定資料庫命令 \(`InsertCommand`、`UpdateCommand` 和 `DeleteCommand`\)。  
  
 如需更新資料的詳細資訊，請參閱[儲存資料](../data-tools/saving-data.md)。  
  
## 巡覽資料集中的資料錄  
 由於資料集是完全中斷連接的資料容器，因此資料集 \(不同於 ADO 資料錄集\) 並不支援目前資料錄的概念。  但是，資料集當中的所有資料錄隨時都可以使用。  
  
 由於沒有目前資料錄，因此並沒有特定的屬性可指向目前資料錄，也沒有方法或屬性來從一個資料錄移動至另一個 \(請參閱底下的注意事項\)。  您可將資料集當中的個別資料表當做物件存取；每個資料表都會顯露資料列的集合。  您可以將這個集合視為任一個集合來處理，並透過集合的索引或使用程式設計語言中特定集合的陳述式來存取資料列。  
  
 例如，您可以使用下列程式碼，取得 `Customers` 資料表的第四列：  
  
 [!CODE [VbRaddataDatasets#3](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#3)]  
  
> [!NOTE]
>  如果您要將表單上的控制項繫結至資料集，可以使用 <xref:System.Windows.Forms.BindingNavigator> 元件，簡化對個別資料錄的存取。  如需詳細資訊，請參閱 [如何：巡覽 Windows Form 中的資料](../Topic/How%20to:%20Navigate%20Data%20in%20Windows%20Forms.md)。  
  
## LINQ to Dataset  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] 可讓您對 <xref:System.Data.DataSet> 物件中的資料進行[LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)。  如需詳細資訊，請參閱 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)。  
  
## 資料集和 XML  
 資料集是可以用 XML 表示的關聯式資料檢視。  資料集和 XML 之間的關聯性讓您可利用資料集的下列功能：  
  
-   資料集的結構，包括資料表、資料行、關聯性和條件約束，都可以在 XML 結構描述中定義。  資料集可使用 <xref:System.Data.DataSet.ReadXmlSchema%2A> 和 <xref:System.Data.DataSet.WriteXmlSchema%2A> 方法讀取和寫入儲存結構化資訊的結構描述。  如果沒有可用的結構描述，資料集可從關聯式結構化的 XML 文件中的資料推論結構描述 \(透過其 <xref:System.Data.DataSet.InferXmlSchema%2A> 方法\)。  如需 XML 結構描述的詳細資訊，請參閱[建置 XML 結構描述](../Topic/Building%20XML%20Schemas.md)。  
  
-   您可以產生資料集類別，其中加入定義其資料結構的結構描述資訊。  這稱資料集為「*具型別*」\(Typed\) 資料集。  如需建立具型別資料集的詳細資訊，請參閱 [如何：建立具類型資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
-   您可以使用資料集的 <xref:System.Data.DataSet.ReadXml%2A> 方法來將 XML 文件或資料流讀入資料集，也可以使用資料集的 <xref:System.Data.DataSet.WriteXml%2A> 方法來將資料集寫出為 XML。  因為 XML 是不同應用程式之間資料的標準交換格式，這表示您可載入其他應用程式傳送的 XML 格式資料集。  同樣地，資料集也可將其資料寫出為 XML 資料流或文件，以便與其他應用程式共用，或只是將其以標準格式儲存。  
  
-   您可以建立資料集或資料表內容的 XML 檢視 \(<xref:System.Xml.XmlDataDocument> 物件\)，然後使用關聯式方法 \(透過資料集\) 或 XML 方法來檢視並管理資料。  這兩種檢視都會在變更時自動同步 \(Synchronize\)。  
  
## 具型別與不具型別的資料集  
 具型別資料集是先從基底 <xref:System.Data.DataSet> 類別衍生的資料集，然後會使用 \[**DataSet 設計工具**\] 中的資訊 \(儲存在 .xsd 檔中\)，以產生新的強型別資料集類別。  接著會產生來自於結構描述的資訊 \(資料表、資料行等等\) 並將其編譯至這個新的資料集類別，成為一組最高級的物件和屬性。  因為具型別資料集繼承自基底 <xref:System.Data.DataSet> 類別，所以具型別類別會採用 <xref:System.Data.DataSet> 類別的所有功能，而且可以與使用 <xref:System.Data.DataSet> 類別執行個體做為參數的方法一起使用。  
  
 相反地，不具型別的資料集並沒有對應的內建結構描述。  就像具型別資料集一樣，不具型別的資料集也包含資料表、資料行等等，但這些都只顯露為集合   \(不過，在不具型別的資料集當中手動建立資料表和其他資料項目之後，您可以使用資料集的 <xref:System.Data.DataSet.WriteXmlSchema%2A> 方法，將資料集的結構以結構描述匯出\)。  
  
### 對照具型別與不具型別資料集的資料存取  
 具型別資料集的類別擁有物件模型，其中的屬性採用資料表和資料行的實際名稱。  例如，如果您使用具型別資料集，您可使用下列程式碼來參考資料行：  
  
 [!CODE [VbRaddataDatasets#4](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#4)]  
  
 相反地，如果您使用不具型別的資料集，對等的程式碼則如下：  
  
 [!CODE [VbRaddataDatasets#5](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#5)]  
  
 具型別存取不但比較容易讀取，而且 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \[**程式碼編輯器**\] 中的 IntelliSense 也完全支援它。  除了較容易使用之外，具型別資料集的語法還提供編譯時間的具型別檢查 \(Type Checking\)，對於指派值給資料集成員的方面能夠大幅減少出現錯誤的可能性。  如果您變更 <xref:System.Data.DataSet> 中資料行的名稱，然後編譯應用程式，就會收到建置錯誤。  按兩下 \[**工作清單**\] 上的建置錯誤，即可直接到參考舊資料行名稱的程式碼行。  存取型別資料集當中的資料表和資料行在執行階段時也稍快些，這是因為存取是在編譯時間決定，而非透過執行階段時的集合來決定。  
  
 雖然型別資料集有許多優點，不過在多種情況下，不具型別的資料集還是相當有用的。  最明顯的案例就是當資料集沒有可用的結構描述。  例如，如果您的應用程式與傳回資料集的元件互動，但您事前並不知道其結構為何，這很可能就會發生上述情況。  同樣地，有時您會使用結構為靜態 \(Static\) 且無法預期的資料，在這種情況下，使用型別資料集就沒有用，因為您可能需要在資料結構一變更時就要重新產生型別資料類別。  
  
 更常見的情況是，您可能要動態建立不用結構描述的資料集。  在這種情況下，只要資料可以關聯式方法表示，資料集只不過是可儲存資訊的方便結構而已。  同時，您也可利用資料集的功能，例如將資料序列化以傳遞至其他處理序或寫出 XML 檔案的能力。  
  
## 資料集大小寫區分性  
 資料集內的資料表和資料行名稱依預設是不區分大小寫的。也就是說，資料集當中名為「Customers」的資料表也代表「customers」。 這符合許多資料庫的命名規範，包括 SQL Server 的預設行為，其中資料項目的名稱無法只由大小寫來分別。  
  
> [!NOTE]
>  與資料集不同的是，XML 文件必須區分大小寫，因此在結構描述中定義的資料項目名稱也必須區分大小寫。  例如，結構描述通訊協定 \(Protocol\) 允許結構描述定義名為 "Customers" 的資料表和另一個名為 "customers" 的不同資料表。 使用內含只由大小寫區分項目的結構描述，產生資料集類別時，這可能造成名稱衝突。  
  
 不過，大小寫區分性可以是資料集當中解譯資料的要素之一。  例如，如果您要篩選資料集資料表當中的資料，則搜尋準則會因是否比較大小寫而可能傳回不同的結果。  您可以控制篩選、搜尋及排序的區分大小寫，方式是設定資料集的 <xref:System.Data.DataSet.CaseSensitive%2A> 屬性。  資料集當中所有資料表都會依預設繼承這個屬性的值   \(分別設定每個資料表的 <xref:System.Data.DataTable.CaseSensitive%2A> 屬性，就可以覆寫資料表的這個屬性\)。  
  
## 關聯資料表和 DataRelation 物件  
 如果您在資料集當中有多個資料表，資料表中的資訊可能相關聯。  資料集原本並不會了解這類關聯性；因此，為了要能夠處理關聯資料表中的資料，您可以建立 <xref:System.Data.DataRelation> 物件，讓這些物件描述資料集之資料表之間的關聯。  如需詳細資訊，請參閱 [如何：存取關聯 DataTable 中的資料錄](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md)。  <xref:System.Data.DataRelation> 物件可用來以程式設計方式擷取父資料錄的相關子資料錄，以及子資料錄中的父資料錄。  如需詳細資訊，請參閱 [資料集中的關聯性](../data-tools/relationships-in-datasets.md)。  如果資料庫包含兩個以上資料表的關聯性，則設計工具會自動為您建立 <xref:System.Data.DataRelation> 物件。  
  
 例如，假設在 Northwind 資料庫中包含客戶和訂單資料。  `Customers` 資料表可能包含的資料錄如下：  
  
```  
CustomerID   CompanyName               City  
ALFKI        Alfreds Futterkiste       Berlin  
ANTON        Antonio Moreno Taquerias  Mexico D.F.  
AROUT        Around the Horn           London  
```  
  
 資料集也可能包含另一個具有訂單資訊的資料表。  `Orders` 資料表包含客戶 ID，做為外部索引鍵資料行。  僅選取 `Orders` 資料表中的某些資料行，看起來會像這樣：  
  
```  
OrderId    CustomerID    OrderDate  
10692      ALFKI         10/03/1997  
10702      ALFKI         10/13/1997  
10365      ANTON         11/27/1996  
10507      ANTON         4/15/1997  
```  
  
 由於每位客戶可能有多個訂單，因此客戶和訂單之間為一對多關聯性 \(One\-To\-Many Relationship\)。  例如，在上述資料表中，客戶 ALFKI 有兩個訂單。  
  
 您可使用 <xref:System.Data.DataRelation> 物件，從子或父資料表取得關聯資料錄。  例如，在您使用說明客戶 ANTON 的資料錄時，可取得說明這位客戶所下訂單的資料錄集合。  如需詳細資訊，請參閱 <xref:System.Data.DataRow.GetChildRows%2A>。  同樣地，使用描述 OrderId 10507 的資料錄時，可以向上巡覽關聯物件，取得其父代 ANTON 的資料錄。  如需詳細資訊，請參閱 <xref:System.Data.DataRow.GetParentRow%2A>。  
  
## 條件約束  
 就像多數資料庫，資料集也支援條件約束以確保資料的完整性。  條件約束是在資料表中插入、更新或刪除資料列時所套用的規則 \(Rule\)。  您可定義兩種條件約束：  
  
-   *唯一的*條件約束 \(Unique Constraint\)，會檢查資料行當中的新值在資料表中是否為唯一的。  
  
-   *外部索引鍵* \(Foreign\-Key\) 的條件約束，當更新或刪除主要資料表中的資料錄時，會定義更新關聯子資料錄更新方式的規則。  例如，外部索引鍵條件約束可驗證父資料錄是否存在之後，才允許建立任何子資料錄。  
  
 在資料集中，條件約束與個別資料表 \(外部索引鍵的條件約束\) 或資料行 \(唯一的條件約束，保證資料行值是唯一的\) 相關聯。  條件約束是實作為型別 <xref:System.Data.UniqueConstraint> 或 <xref:System.Data.ForeignKeyConstraint> 的物件。  然後將它們加入至 <xref:System.Data.DataTable> 的 <xref:System.Data.DataTable.Constraints%2A> 集合。  此外，將 <xref:System.Data.DataColumn> 的 <xref:System.Data.DataColumn.Unique%2A> 屬性設為 `true`，即可指定唯一的條件約束。  
  
 資料集本身支援布林 <xref:System.Data.DataSet.EnforceConstraints%2A> 屬性，指定是否強制使用條件約束。  根據預設，這個屬性是設定為 `true`。  不過在某些情況下，暫時關閉條件約束卻十分有效。  這通常是在變更資料錄的方式會暫時導致無效狀態時使用。  當完成變更 \(並因此回到有效狀態\) 之後，您可重新啟用條件約束。  
  
 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，您可以在定義資料集時隱含建立條件約束。  藉由將主索引鍵加入至資料集，您可為主索引鍵資料行隱含建立唯一的條件約束。  您可以將其他資料行的 <xref:System.Data.DataColumn.Unique%2A> 屬性設定為 `true`，為其指定唯一的條件約束。  
  
 您可以在資料集當中建立 <xref:System.Data.DataRelation> 物件，建立外部索引鍵條件約束。  除了讓您以程式設計方式取得關聯資料錄的資訊之外，<xref:System.Data.DataRelation> 物件還可讓您定義外部索引鍵條件約束的規則。  
  
## 資料集擴充屬性  
 在從 .xsd 檔產生資料集的過程當中遇到了命名衝突時，擴充屬性可提供名稱對應。  當 .xsd 檔中的識別項與資料集產生器所建立的計算之名稱不同時，會在 `msprop` 命名空間的資料集中加入擴充屬性。  下表將顯示可以產生的可能擴充屬性：  
  
|物件|擴充屬性|  
|--------|----------|  
|<xref:System.Data.DataSet>|msprop:Generator\_UserDSName|  
||msprop:Generator\_DataSetName|  
|<xref:System.Data.DataTable>|msprop:Generator\_UserTableName|  
||msprop:Generator\_TablePropName|  
||msprop:Generator\_TableVarName|  
||msprop:Generator\_TableClassName|  
||msprop:Generator\_RowClassName|  
||msprop:Generator\_RowEvHandlerName|  
||msprop:Generator\_RowEvArgName|  
|<xref:System.Data.DataColumn>|msprop:Generator\_UserColumnName|  
||msprop:Generator\_ColumnPropNameInTable|  
||msprop:Generator\_ColumnVarNameInTable|  
||msprop:Generator\_ColumnPropNameInRow|  
  
## 請參閱  
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)