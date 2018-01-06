---
title: "逐步解說： 使用商務資料在 SharePoint 中建立外部清單 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
ms.assetid: 046cf234-705a-4a6f-91f8-c5c569ae0dd0
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8ecc80a3c26b97b9754f998bd0903471d00cd1d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data"></a>逐步解說：使用商務資料在 SharePoint 中建立外部清單
  商務資料連線 (BDC) 服務可讓 SharePoint，以顯示來自後端伺服器應用程式、 Web 服務和資料庫的商務資料。  
  
 本逐步解說會示範如何建立傳回範例資料庫中的連絡人相關資訊，BDC 服務的模型。 您接著會使用此模型，在 SharePoint 中建立外部清單。  
  
 這個逐步解說將說明下列工作：  
  
-   建立專案。  
  
-   將實體加入至模型。  
  
-   加入搜尋方法。  
  
-   加入特定搜尋工具方法。  
  
-   測試專案。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Windows 版本和 SharePoint。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]、[!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)] 或 [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)]。  
  
-   AdventureWorks 範例資料庫的存取。 如需如何安裝 AdventureWorks 資料庫的詳細資訊，請參閱[SQL Server 範例資料庫](http://go.microsoft.com/fwlink/?LinkID=117483)。  
  
## <a name="creating-a-project-that-contains-a-bdc-model"></a>建立包含 BDC 模型的專案  
  
#### <a name="to-create-a-project-that-contains-a-bdc-model"></a>若要建立包含 BDC 模型的專案  
  
1.  在 Visual Studio 中的功能表列上選擇 **檔案**，**新增**，**專案**。  
  
     [ **新增專案** ] 對話方塊隨即開啟。  
  
2.  之下**Visual C#**或**Visual Basic**，依序展開**SharePoint** ] 節點，然後選擇 [ **2010年**項目。  
  
3.  在**範本**] 窗格中，選擇**SharePoint 2010 專案**，將專案命名**為 AdventureWorksTest**，然後選擇 [ **[確定]**按鈕.  
  
     **SharePoint 自訂精靈**隨即出現。 在此精靈中，您可以指定您要用以偵錯專案和方案的信任層級設定的站台。  
  
4.  選擇**部署為伺服陣列方案**選項按鈕，即可設定信任層級。  
  
5.  選擇**完成** 按鈕，接受預設的本機 SharePoint 網站。  
  
6.  在**方案總管 中**，選擇 SharePoint 專案節點。  
  
7.  在功能表列上選擇 **專案**，**加入新項目**。  
  
     [新增項目] 對話方塊隨即開啟。  
  
8.  在**範本** 窗格中，選擇**商務資料連接模型 （僅限陣列方案）**，將專案命名**命名為 AdventureWorksContacts**，然後選擇  **新增** 按鈕。  
  
## <a name="adding-data-access-classes-to-the-project"></a>加入至專案的資料存取類別  
  
#### <a name="to-add-data-access-classes-to-the-project"></a>將資料存取類別加入至專案  
  
1.  在功能表列上選擇 **工具**，**連接至資料庫**。  
  
     **加入連接**對話方塊隨即開啟。  
  
2.  加入 SQL Server AdventureWorks 範例資料庫的連接。  
  
     如需詳細資訊，請參閱[新增/修改連接 (Microsoft SQL Server)](http://msdn.microsoft.com/en-us/fa400910-26c3-4df7-b9d1-115e688b4ea3)。  
  
3.  在 [ **方案總管**] 中選擇專案節點。  
  
4.  在功能表列上選擇 **專案**，**加入新項目**。  
  
5.  在**已安裝的範本** 窗格中，選擇**資料**節點。  
  
6.  在**範本** 窗格中，選擇**LINQ to SQL 類別**。  
  
7.  在**名稱**方塊中，指定**AdventureWorks**，然後選擇 [**新增**] 按鈕。  
  
     .dbml 檔案隨即加入至專案，而且物件關聯式設計工具 (O/R 設計工具) 便會開啟。  
  
8.  在功能表列上選擇 **檢視**，**伺服器總管**。  
  
9. 在**伺服器總管**、 展開代表 AdventureWorks 範例資料庫的節點，然後再展開**資料表**節點。  
  
10. 新增**Contact (Person)**資料表拖曳至 O/R 設計工具。  
  
     實體類別隨即建立並出現在設計介面上。 這個實體類別的屬性會對應至 Contact (Person) 資料表中的資料行。  
  
## <a name="removing-the-default-entity-from-the-bdc-model"></a>預設實體移除 BDC 模型  
 **商務資料連接模型**專案加入名為模型的 Entity1 的預設實體。 移除此實體。 稍後，您會加入新的實體。 開頭為空的模型，減少所需完成此逐步解說的步驟數目。  
  
#### <a name="to-remove-the-default-entity-from-the-model"></a>若要從模型移除預設的實體  
  
1.  在**方案總管 中**，依序展開**BdcModel1**節點，然後再開啟 bdcmodel1.bdcm 檔案。  
  
2.  商務資料連接模型檔案會在 BDC 設計工具中開啟。  
  
3.  在設計師中，開啟捷徑功能表**Entity1**，然後選擇 **刪除**。  
  
4.  在**方案總管 中**，開啟 Entity1.vb （在 Visual Basic) 或 Entity1.cs （在 C#) 的捷徑功能表，然後選擇**刪除**。  
  
5.  開啟 Entity1Service.vb （在 Visual Basic) 或 Entity1Service.cs （在 C#) 的捷徑功能表，然後選擇**刪除**。  
  
## <a name="adding-an-entity-to-the-model"></a>將實體加入至模型  
 將實體加入至模型。 您可以從 Visual Studio 加入實體**工具箱**在 BDC 設計工具上。  
  
#### <a name="to-add-an-entity-to-the-model"></a>若要將實體加入至模型  
  
1.  在功能表列上，依序選擇 [檢視] 和 [工具箱]。  
  
2.  在**BusinessDataConnectivity**  索引標籤**工具箱**，新增**實體**在 BDC 設計工具上。  
  
     新的實體會出現在設計工具。 Visual Studio 會加入至專案中是名為的 EntityService.vb （在 Visual Basic) 或 EntityService.cs （在 C# 中) 的檔案。  
  
3.  在功能表列上選擇 **檢視**，**屬性**，**視窗**。  
  
4.  在**屬性**視窗中，將**名稱**屬性值設定為**連絡人**。  
  
5.  在設計工具中，開啟實體的捷徑功能表，選擇 **新增**，然後選擇 **識別碼**。  
  
     新的識別碼會出現在實體上。  
  
6.  在**屬性**視窗中，變更的識別項名稱**ContactID**。  
  
7.  在**型別名稱**清單中，選擇**System.Int32**。  
  
## <a name="adding-a-specific-finder-method"></a>新增 Specific Finder 方法  
 若要啟用顯示特定連絡人，BDC 服務，您必須加入特定搜尋工具方法。 使用者在清單中選擇的項目，然後選擇時，BDC 服務會呼叫特定搜尋工具方法**檢視項目**功能區上的按鈕。  
  
 使用將特定搜尋工具方法新增至連絡人實體**BDC 方法詳細資料**視窗。 若要傳回特定的實體，將程式碼加入至方法。  
  
#### <a name="to-add-a-specific-finder-method"></a>若要加入特定搜尋工具方法  
  
1.  在 BDC 設計工具中，選擇 **連絡人**實體。  
  
2.  在功能表列上選擇 **檢視**，**其他視窗**， **BDC 方法詳細資料**。  
  
     BDC 方法詳細資料視窗隨即開啟。  
  
3.  在**將方法加入**清單中，選擇**建立特定搜尋方法**。  
  
     Visual Studio 會將下列項目加入至模型。 這些項目會出現在**BDC 方法詳細資料**視窗。  
  
    -   名為 ReadItem 的方法。  
  
    -   方法的輸入的參數。  
  
    -   方法的傳回參數。  
  
    -   針對每個參數類型描述元。  
  
    -   方法執行個體方法。  
  
4.  在**BDC 方法詳細資料**視窗中，開啟所顯示清單**連絡人**類型描述元，然後選擇**編輯**。  
  
     **BDC 總管**會開啟並提供模型的階層式檢視。  
  
5.  在**屬性**視窗中，開啟清單旁**TypeName**屬性，選擇**目前專案**索引標籤，然後選擇 **連絡人**屬性。  
  
6.  在**BDC 總管**，開啟捷徑功能表**連絡人**，然後選擇 **加入類型描述元**。  
  
     名為的新類型描述元**TypeDescriptor1**會出現在**BDC 總管**。  
  
7.  在**屬性**視窗中，將**名稱**屬性值設定為**ContactID**。  
  
8.  接下來，開啟清單**TypeName**屬性，然後選擇  **Int32**。  
  
9. 接下來，開啟清單**識別碼**屬性，然後選擇  **ContactID**。  
  
10. 重複步驟 6 來建立每個下列欄位的類型描述元。  
  
    |名稱|類型名稱|  
    |----------|---------------|  
    |FirstName|System.String|  
    |LastName|System.String|  
    |電話|System.String|  
    |emailAddress|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. 在 BDC 設計工具上**連絡人**實體上，開啟**ReadItem**方法。  
  
     請連絡服務程式碼檔隨即開啟程式碼編輯器中。  
  
12. 在`ContactService`類別中，取代`ReadItem`方法取代下列程式碼。 這個程式碼會執行下列工作：  
  
    -   從 Contact 資料表的 AdventureWorks 資料庫中擷取記錄。  
  
    -   Contact 實體傳回，BDC 服務。  
  
    > [!NOTE]  
    >  取代的值`ServerName`欄位與您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="adding-a-finder-method"></a>加入搜尋方法  
 若要啟用 BDC 服務，以顯示連絡人清單中，您必須加入搜尋方法。 使用將搜尋工具方法新增至連絡人實體**BDC 方法詳細資料**視窗。 若要返回 BDC 服務實體的集合，將程式碼加入至方法。  
  
#### <a name="to-add-a-finder-method"></a>若要加入搜尋方法  
  
1.  在 BDC 設計工具中，選擇 **連絡人**實體。  
  
2.  在**BDC 方法詳細資料** 視窗中，摺疊**ReadItem**節點。  
  
3.  在**將方法加入**清單下**ReadList**方法中，選擇**建立搜尋方法**。  
  
     Visual Studio 加入方法，傳回的參數和型別描述項。  
  
4.  在 BDC 設計工具上**連絡人**實體上，開啟**ReadList**方法。  
  
     Contact 服務的程式碼檔案隨即在 [程式碼編輯器] 中開啟。  
  
5.  在`ContactService`類別中，取代`ReadList`方法取代下列程式碼。 這個程式碼會執行下列工作：  
  
    -   從 AdventureWorks 資料庫的 [連絡人] 資料表擷取資料。  
  
    -   傳回 BDC 服務連絡人實體的清單。  
  
    > [!NOTE]  
    >  取代的值`ServerName`欄位與您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="testing-the-project"></a>測試專案  
 當您執行專案時，SharePoint 網站隨即開啟，Visual Studio 將商務資料連接服務加入您的模型。 參照連絡人實體的 SharePoint 中建立外部清單。 連絡人 AdventureWorks 資料庫中的資料會出現在清單中。  
  
> [!NOTE]  
>  您可能必須修改您在 SharePoint 中的安全性設定，您可以在偵錯您的方案之前。  如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
#### <a name="to-test-the-project"></a>測試專案  
  
1.  選擇 **F5** 鍵。  
  
     開啟 SharePoint 網站。  
  
2.  在**網站動作**功能表上，選擇**更多選項**命令。  
  
3.  在**建立**頁面上，選擇**外部清單**範本，然後選擇 [**建立**] 按鈕。  
  
4.  命名自訂清單**連絡人**。  
  
5.  選擇 [瀏覽] 按鈕旁邊**外部內容類型**欄位。  
  
6.  在**外部內容類型選擇器**對話方塊方塊中，選擇**AdventureWorksContacts.BdcModel1.Contact**項目，然後再選擇**建立** 按鈕。  
  
     SharePoint 會建立一個外部清單，其中包含 AdventureWorks 範例資料庫中的連絡人。  
  
7.  若要測試特定搜尋工具方法，請選擇清單中的連絡人。  
  
8.  在功能區中，選擇 **項目**索引標籤，然後選擇 **檢視項目**命令。  
  
     您選擇之連絡人的詳細資料隨即出現在表單上。  
  
## <a name="next-steps"></a>後續步驟  
 您可以深入了解如何設計模型的 SharePoint BDC 服務從下列主題：  
  
-   [如何： 加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)。  
  
-   [如何： 加入 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)。  
  
-   [如何： 加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)。  
  
## <a name="see-also"></a>請參閱  
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  