---
title: 如何： 連接到資料庫中的資料 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases, connecting to
- data sources, databases
- data [Visual Studio], connecting to databases
- data sources, creating
- database connections
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e75de3c81270449da6fe6bb504b476b912f51583
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273802"
---
# <a name="how-to-connect-to-data-in-a-database"></a>如何：連接至資料庫中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Visual Studio 將應用程式連接至資料庫。 在建立資料連線之後，Visual Studio 會產生由應用程式用來與資料庫資料進行互動的資料模型。 在資料模型物件會出現在[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)。 您接著可以建立資料繫結控制項項目從**資料來源視窗**至設計介面。 如需詳細資訊，請參閱 <<c0> [ 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
 本主題提供有關連接至資料庫以及建立下列資料模型類型的指示：  
  
-   資料集  
  
-   實體資料模型 (EDM)  
  
> [!NOTE]
>  您也可以使用 Visual Studio，從資料庫建立 LINQ to SQL 類別。 不過，LINQ to SQL 類別並不會顯示在**Zdroje dat**  視窗中，並因此無法直接拖曳至設計工具建立資料繫結控制項。 如需從資料庫建立 LINQ to SQL 類別的詳細資訊，請參閱[如何： 建立的 LINQ to SQL 類別對應至資料表和檢視 （O/R 設計工具）](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
##  <a name="dataset"></a> 連接至資料庫和建立資料集  
 當您根據資料庫建立資料集時，Visual Studio 會建立一組表示可程式資料檢視的類別。 主要的類別稱為*類型資料集*。 具類型資料集包含表示資料庫資料表的資料表物件。 如需有關具類型資料集的詳細資訊，請參閱 < [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)。  
  
 在建立資料集之後，只要將資料集物件從 [資料來源] 視窗拖曳至 WPF 或 Windows Form 設計工具，就可以建立資料繫結 WPF 或 Windows Form 控制項。  
  
#### <a name="to-connect-your-application-to-a-database-and-create-a-dataset"></a>若要將應用程式連接至資料庫和建立資料集  
  
1.  在 Visual Studio 中開啟現有專案，或建立新的專案。  
  
2.  在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。  
  
     **資料來源組態精靈**隨即開啟。  
  
3.  在 [**選擇資料來源類型**頁面上，選取**資料庫**，然後按一下**下一步]**。  
  
4.  在 [**選擇資料庫模型**頁面上，選取**資料集**，然後按一下**下一步]**。  
  
5.  在 [**選擇資料連接**頁面上，從可用連線清單中選取資料連接，然後按一下**下一步]**。  
  
     如果您想要的資料連接無法使用，請依照中的步驟建立新的連接[建立新的資料庫連接](#CreatingDataConnection)。  
  
6.  在上**儲存連接字串儲存到應用程式設定檔**頁面上，選擇性地清除**儲存連線設定為 [是]，** 核取方塊，如果您想要直接在編譯中儲存的連接字串應用程式。 根據預設，此連接會儲存在應用程式組態檔中。 如需詳細資訊，請參閱 <<c0> [ 如何： 儲存並編輯連接字串](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md)。  
  
7.  在 **選擇您的資料庫物件**頁面上，選取您將使用您的應用程式中的資料庫物件。 您也可以選擇取代預設**資料集名稱**。  
  
8.  按一下 [ **完成**]。 您剛才建立的資料集現已推出**Zdroje dat**視窗。  
  
    > [!NOTE]
    >  如果**資料來源**視窗未開啟，請按一下**顯示資料來源**上**資料**以開啟視窗 功能表。  
  
9. 您現在可以拖曳項目從**資料來源**WPF 設計工具中，Windows Form 設計工具中，視窗或[Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282)建立資料繫結控制項。 如需詳細資訊，請參閱 <<c0> [ 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
##  <a name="edm"></a> 連接至資料庫和建立實體資料模型  
 當您根據資料庫建立實體資料模型時，Visual Studio 會建立一組表示可程式資料檢視的類別。 如需有關實體資料模型及 ADO.NET Entity Framework 的詳細資訊，請參閱 < [Entity Framework 概觀](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)。  
  
 在建立實體資料模型之後，您可以從 [資料來源] 視窗將實體物件拖曳至 WPF 設計工具中，以建立資料繫結 WPF 控制項。  
  
#### <a name="to-connect-your-application-to-a-database-and-create-an-entity-data-model"></a>若要將應用程式連接至資料庫和建立實體資料模型  
  
1.  在 Visual Studio 中開啟現有專案，或建立新的專案。  
  
2.  請依照下列中的步驟**Entity Data Model 精靈**連接到資料庫，並指定模型的內容。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立新.edmx 檔案](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2)。  
  
3.  完成後**Entity Data Model 精靈**、 在實體資料模型設計工具中，會開啟 建立實體資料模型和資料物件現在均**Zdroje dat**視窗。  
  
    > [!NOTE]
    >  如果**資料來源**視窗未開啟，請按一下**顯示資料來源**上**資料**以開啟視窗 功能表。  
  
4.  如果 WPF 設計工具已開啟，您現在可以拖曳項目從**Zdroje dat**視窗建立控制項繫結至實體資料模型設計工具。 如需詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)。  
  
     如果開啟 Windows Form 設計工具，您無法將拖曳的項目**Zdroje dat**至設計工具。 若要建立繫結至實體資料模型的控制項，您必須建置專案，根據實體資料模型加入新的物件資料來源，然後將這些物件拖曳至設計工具。  
  
##  <a name="CreatingDataConnection"></a> 正在建立新的資料庫連接  
 當您使用**資料來源組態精靈**或**Entity Data Model 精靈**，您必須指定您想要使用資料庫的連接。 如果您尚未有可用的資料庫連接，請執行下列步驟建立連接。  
  
 這些指示假設您已經開始**資料來源組態精靈**或**Entity Data Model 精靈**中所述[連接至資料庫和建立資料集](#dataset)並[連接至資料庫和建立 Entity Data Model](#edm)。  
  
#### <a name="to-create-a-new-database-connection"></a>若要建立新的資料庫連接  
  
1.  上**選擇資料連接**頁面**資料來源組態精靈**或**Entity Data Model 精靈**，按一下 **新連線**.  
  
     發生下列其中一項動作：  
  
    -   如果您已經在 Visual Studio 中建立資料連線**加入連接**對話方塊隨即開啟。  
  
    -   如果這是您在 Visual Studio 中建立的第一個資料連線**選擇資料來源**對話方塊會顯示。 選取您想要連接到，然後按一下的資料庫的類型**確定**顯示**加入連接** 對話方塊。  
  
2.  在 **加入連接**對話方塊方塊中，輸入所要求的資訊。 **加入連接**對話方塊是不同的資料提供者的每個型別。  
  
    > [!NOTE]
    >  如果所選**資料來源**中**加入連接** 對話方塊不是您想要連接至，請按一下資料來源**變更**以開啟**變更資料來源**對話方塊然後選擇不同的資料來源。  
  
3.  在 [**加入連接**] 對話方塊中，按一下**確定**。  
  
     您返回**選擇資料連接**頁面**資料來源組態精靈**或**Entity Data Model 精靈**。  
  
4.  在 [**選擇資料連接**頁面上，確定已選取新的資料連接，然後按一下**下一步]**。  
  
5.  完成中剩餘的步驟**資料來源組態精靈**或**Entity Data Model 精靈**。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 儲存敏感資料 (如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4)。  
  
## <a name="see-also"></a>另請參閱  
 [加入新的資料來源](../data-tools/add-new-data-sources.md)   
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [連接至資料來源](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e)