---
title: 編輯 TableAdapters |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.dbtablefunctionwizard
- vs.datasource.datacomponentquerywizard
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data component queries
- data [Visual Studio], TableAdapters
- TableAdapter Query Configuration Wizard
- data [Visual Studio], table adapter queries
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: faeac90c92675c897774cc3650575cd60f5be991
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288401"
---
# <a name="editing-tableadapters"></a>編輯 TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有時候您可能要變更此配接器的資料表結構描述。 若要這樣做，您可以修改配接器的主要`Fill`方法。 Tableadapter 會建立含有 main`Fill`定義相關聯的資料表的結構描述的方法。 主`Fill`方法為基礎的查詢或預存程序時輸入您原先設定 TableAdapter; 它是第一個 （最上層） 方法在資料表上[建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)。  
  
 ![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 任何您所做變更至 TableAdapter 的主要`Fill`方法會反映在相關聯的資料的資料表結構描述。 例如，從主要查詢移除資料行`Fill`方法也會移除資料行相關聯的資料表。 此外，移除資料行，從主要`Fill`方法移除資料行從任何其他查詢的 TableAdapter。  
  
 您可以使用**TableAdapter 查詢組態精靈**來建立和編輯其他查詢的 TableAdapter。 這些額外的查詢必須符合資料表的結構描述，除非它們會傳回純量值。  額外的查詢具有您指定的名稱 (例如`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`。)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>若要開始使用新的查詢的 TableAdapter 查詢組態精靈  
  
1.  開啟您的資料集，在**Dataset 設計工具**。  
  
2.  如果您要建立新的查詢，拖曳**查詢**物件**資料集**索引標籤**工具箱**拖曳至<xref:System.Data.DataTable>，或選取**加入查詢**TableAdapter 的快顯功能表中。 您也可以拖曳**查詢**物件上的空白區域**Dataset 設計工具**，這會建立有關聯的 TableAdapter <xref:System.Data.DataTable>。 這些查詢限制為傳回單一值 （純量），或執行 UPDATE、 INSERT、 或刪除對資料庫的命令。 如需詳細資訊，請參閱 <<c0> [ 如何： 加入至 TableAdapter 的全域查詢](../data-tools/how-to-add-global-queries-to-a-tableadapter.md)。  
  
3.  在 **選擇資料連接**頁面上，選取或建立查詢將使用的連接。  
  
    > [!NOTE]
    >  設計工具無法判斷適當的連接，若要使用，或沒有連線可供使用時，才會出現此頁面。  
  
4.  在 **選擇命令類型**頁面上，選取從資料庫擷取資料的下列方法：  
  
    -   **使用 SQL 陳述式**可讓您輸入 SQL 陳述式，從您的資料庫選取的資料。  
  
    -   **建立新的預存程序**— 選取此選項即可讓精靈建立新預存程序 （資料庫） 中指定的 SELECT 陳述式為基礎。  
  
    -   **使用現有的預存程序**— 選取此選項以執行查詢時，執行現有的預存程序。  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>若要在現有的查詢上啟動 TableAdapter 查詢組態精靈  
  
-   如果您要編輯現有的 TableAdapter 查詢，以滑鼠右鍵按一下查詢，並選擇**設定**從捷徑功能表。  
  
    > [!NOTE]
    >  以滑鼠右鍵按一下主查詢的 TableAdapter 會重新設定 TableAdapter 和<xref:System.Data.DataTable>結構描述，而其他查詢的 TableAdapter 上按一下滑鼠右鍵，則只會設定選取的查詢。 **TableAdapter 組態精靈**重新設定 TableAdapter 定義，而**TableAdapter 查詢組態精靈**重新設定選取的查詢。  
  
## <a name="running-the-wizard"></a>執行精靈  
 將查詢拖曳至**Dataset 設計工具**，或設定現有的查詢 （任何下列第一個查詢的查詢）。  
  
 TableAdapter 中的第一個查詢是 TableAdapter 的主要查詢。 編輯此主要查詢會開啟**TableAdapter 組態精靈**和編輯 TableAdapter 資料表的結構描述。 主要查詢下方所列的所有查詢的其他查詢作業，而且會設定為使用**TableAdapter 查詢組態精靈**。 如需有關執行精靈的詳細資訊，請參閱 <<c0> [ 如何： 啟動 TableAdapter 查詢組態精靈](http://msdn.microsoft.com/library/fc7b468e-3417-48a4-a8aa-cace8f99c24a)。  
  
## <a name="choose-your-data-connection"></a>選擇資料連線  
 從連接清單中選擇現有的連線，或按一下**新的連接**來建立您資料庫的連接。  
  
 完成時**連接屬性** 對話方塊中，**連線詳細資料**區域會顯示關於所選的提供者，以及連接字串的唯讀資訊。  
  
## <a name="save-the-connection-string-to-the-application-configuration-file"></a>將連接字串儲存到應用程式組態檔  
 選擇 **[是]，將連接儲存為為**來儲存應用程式組態檔中的連接字串。 輸入連接的名稱，或使用提供的預設名稱。  
  
 將連接字串儲存至應用程式組態檔，即可簡化資料庫連接變更時的應用程式維護流程。 如果資料庫連接變更，您可以編輯應用程式組態檔中的連接字串。 這樣一來，您就不需要編輯原始程式碼以及重新編譯您的應用程式。 如需編輯應用程式組態檔中的連接字串的詳細資訊，請參閱[如何： 儲存並編輯連接字串](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md)。  
  
> [!IMPORTANT]
>  資訊會以純文字形式儲存在應用程式組態檔中。 若要減少未授權存取敏感性資訊的機率，您可能會想要加密資料。 如需詳細資訊，請參閱 <<c0> [ 加密和解密資料](http://msdn.microsoft.com/en-us/22812ae8-e082-4eb1-a29b-21b6ee00c6b5)。  
  
## <a name="use-sql-statements"></a>使用 SQL 陳述式  
 本節說明如何完成**TableAdapter 查詢組態精靈**時選取**使用 SQL 陳述式**選項。  
  
## <a name="choose-a-query-type"></a>選擇查詢類型  
 此精靈會建立數種類型的查詢 (視您應用程式的需求而定)。 您可以選擇傳回數列資料 (資料表) 的 SELECT 查詢，還是傳回純量值 (單一值，如 `Count` 或 `Sum`) 的 SELECT 查詢。  
  
 在 **選擇查詢類型**頁面上，選取 從可用查詢清單建立查詢的類型。  
  
> [!NOTE]
>  建立 INSERT、UPDATE 或 DELETE 陳述式，並不會取代呼叫 TableAdapter 的 `Update` 方法時所使用的 TableAdapter 命令。 例如，選取 UPDATE 做為查詢類型，將會使用您稍後在精靈中指定的名稱來建立新的查詢。 呼叫 TableAdapter 的這個具名方法，即可執行此查詢。 呼叫 TableAdapter 的 `Update` 方法，將會執行設定原始 TableAdapter 時所建立的陳述式。  
  
## <a name="specify-a-sql-query-type-statement"></a>指定 SQL\<查詢類型 > 陳述式  
 在 **指定 SQL 陳述式**頁面上，輸入 SQL 陳述式在呼叫查詢時執行。  
  
> [!TIP]
>  精靈會提供存取權**查詢產生器**，一種視覺化工具來建立 SQL 查詢。 若要開啟它，請按一下**查詢產生器** 按鈕。  
  
## <a name="choose-methods-to-generate"></a>選擇要產生的方法  
 此頁面所提供的選項用於選取精靈針對查詢所產生的方法。  
  
 **填入 DataTable**  
 建立用於填入資料表的方法。 呼叫此方法將所傳回的資料填入資料表時，您可以將資料表名稱傳遞為參數。  
  
 （選擇性） 您可以在此變更中的預設名稱**方法名稱** 方塊中。 在程式碼中使用此查詢時，提供有意義的名稱十分有用。  
  
 **傳回 DataTable**  
 建立用於傳回已填入之資料表的方法。 在特定應用程式中，傳回已填入的資料表，會優先於使用資料填入現有資料表。  
  
 （選擇性） 您可以在此變更中的預設名稱**方法名稱** 方塊中。  
  
## <a name="choose-function-name"></a>選擇函式名稱  
 輸入函式的名稱。 建立 TableAdapter 查詢，會將方法加入至具有這裡所提供名稱的 TableAdapter。 呼叫此方法以執行查詢。 在程式碼中使用此查詢時，提供有意義的名稱十分有用。  
  
> [!NOTE]
>  建立新的預存程序時，系統會要求您提供兩個名稱。 第一個名稱是在資料庫中建立的預存程序名稱；第二個名稱是 TableAdapter 上執行所呼叫預存程序的方法名稱。  
  
## <a name="create-new-stored-procedures"></a>建立新的預存程序  
 本節說明如何完成**TableAdapter 查詢組態精靈**時選取**建立新的預存程序**選項。  
  
1.  在 **產生預存程序**頁面上，輸入 SQL 陳述式在呼叫預存程序時執行。  
  
    > [!NOTE]
    >  精靈會提供存取權**查詢產生器**，一種視覺化工具來建立 SQL 查詢。 若要開啟它，請按一下**查詢產生器** 按鈕。  
  
2.  在 **建立的預存程序**頁面上，執行下列動作：  
  
    1.  輸入新預存程序的名稱。  
  
    2.  指定是否在基礎資料庫中建立預存程序。  
  
        > [!NOTE]
        >  在資料庫中建立預存程序的能力是透過特定資料庫的安全性設定所決定。  
  
     **檢視精靈結果**頁面會顯示建立 TableAdapter 查詢的結果。 如果精靈發生問題，則此頁面會提供錯誤資訊。  
  
## <a name="use-existing-stored-procedures"></a>使用現有的預存程序  
 本節說明如何完成**TableAdapter 查詢組態精靈**時選取**使用現有的預存程序**選項。  
  
1.  在 選取現有的預存程序，從下拉式清單**選擇現有的預存程序**精靈頁面。  
  
     **參數**並**結果**所選的預存程序所顯示的參考。  
  
2.  按 [ **下一步**]。  
  
## <a name="choose-the-shape-of-data-returned-by-the-stored-procedure"></a>選擇預存程序所傳回資料的形式  
 所選取預存程序所傳回的資料類型可決定精靈建立 TableAdapter 方法的方式。  
  
 選取此查詢所傳回的資料類型。  
  
-   選取**表格式資料**便會開啟**選擇要產生的方法**頁面 （先前所述在此 [說明] 頁面上），可讓您指定的方法、 方法名稱和要建立的分頁支援的類型。  
  
-   選取**的單一值**建立具類型的方法會傳回單一值。 此選項會開啟**選擇函式名稱**頁面 （如這個說明網頁所述）。  
  
-   選取**沒有值**建立具類型的方法執行預存程序，並預期要傳回的資料。 此選項會開啟**選擇函式名稱**頁面 （如這個說明網頁所述）。  
  
## <a name="view-wizards-results"></a>檢視精靈結果  
 **檢視精靈結果**頁面會顯示建立 TableAdapter 查詢的結果。 如果精靈發生問題，則會在此頁面上顯示詳細資料。  
  
## <a name="see-also"></a>另請參閱  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [如何： 編輯 TableAdapter 查詢](../data-tools/how-to-edit-tableadapter-queries.md)   
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [在 Visual Studio 中的資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)