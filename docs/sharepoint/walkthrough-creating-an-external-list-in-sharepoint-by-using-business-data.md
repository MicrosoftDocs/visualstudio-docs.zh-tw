---
title: 逐步解說：使用商務資料在 SharePoint 中建立外部清單 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45f0a896db97d489d58036ea226962550b512665
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600294"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>逐步解說：使用商務資料在 SharePoint 中建立外部清單

商務資料連接 (BDC) 服務可讓 SharePoint，以顯示來自後端伺服器應用程式、 Web 服務和資料庫的商務資料。

本逐步解說會示範如何建立傳回範例資料庫中的連絡人相關資訊的 BDC 服務模型。 您接著會使用此模型，在 SharePoint 中建立外部清單。

這個逐步解說將說明下列工作：

- 建立專案。
- 您可以將實體加入模型。
- 新增搜尋方法。
- 加入特定搜尋工具方法。
- 測試專案。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成此逐步解說：

- 支援的 Windows 和 SharePoint 版本。

- AdventureWorks 範例資料庫的存取。 如需如何安裝 AdventureWorks 資料庫的詳細資訊，請參閱[SQL Server 範例資料庫](http://go.microsoft.com/fwlink/?LinkID=117483)。

## <a name="create-a-project-that-contains-a-bdc-model"></a>建立包含 BDC 模型的專案

1. 在 Visual Studio 中的功能表列上選擇 **檔案** > **新增** > **專案**。

     [ **新增專案** ] 對話方塊隨即開啟。

2. 之下**Visual C#** 或**Visual Basic**，展開**SharePoint**  節點，然後選擇**2010年**項目。

3. 在**範本** 窗格中，選擇**SharePoint 2010 專案**，將專案命名為**為 AdventureWorksTest**，然後選擇**確定**按鈕.

     **SharePoint 自訂精靈**隨即出現。 在此精靈中，您可以指定您要用來偵錯專案和方案的信任層級設定的站台。

4. 選擇**部署為伺服陣列方案**選項按鈕，即可設定信任層級。

5. 選擇**完成** 按鈕，接受預設的本機 SharePoint 網站。

6. 在 [**方案總管] 中**，選擇 SharePoint 專案節點。

7. 在功能表列中，選擇 [專案] > [加入新項目]。

     [新增項目] 對話方塊隨即開啟。

8. 在**範本**窗格中，選擇**Business Data Connectivity 模型 （僅限陣列方案）**，將專案命名為**為 AdventureWorksContacts**，然後選擇 [ **新增**] 按鈕。

## <a name="add-data-access-classes-to-the-project"></a>加入專案中的資料存取類別

1. 在功能表列上選擇 **工具** > **連接至資料庫**。

     [新增連線] 對話方塊隨即開啟。

2. 新增連線至 SQL Server AdventureWorks 範例資料庫。

     如需詳細資訊，請參閱 <<c0> [ 加入/修改連接 (Microsoft SQL Server)](https://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3)。

3. 在 [ **方案總管**] 中選擇專案節點。

4. 在功能表列中，選擇 [專案] > [加入新項目]。

5. 在 **已安裝的範本**窗格中，選擇**資料**節點。

6. 在 **範本**窗格中，選擇**LINQ to SQL 類別**。

7. 在 [**名稱**方塊中，指定**AdventureWorks**，然後選擇**新增**] 按鈕。

     .dbml 檔案隨即加入至專案，而且物件關聯式設計工具 (O/R 設計工具) 便會開啟。

8. 在功能表列上選擇 **檢視** > **伺服器總管**。

9. 在 **伺服器總管**、 展開代表 AdventureWorks 範例資料庫的節點，然後再展開**資料表**節點。

10. 新增**Contact (Person)** 資料表拖曳至 O/R 設計工具。

     實體類別隨即建立並出現在設計介面上。 這個實體類別的屬性會對應至 Contact (Person) 資料表中的資料行。

## <a name="remove-the-default-entity-from-the-bdc-model"></a>預設實體移除 BDC 模型

**Business Data Connectivity 模型**專案加入名 Entity1 為模型的預設實體。 移除此實體。 稍後，您會加入新的實體。 開頭為空的模型，可減少完成本逐步解說所需的步驟數目。

1. 在 **方案總管**，展開**BdcModel1**節點，然後再開啟*BdcModel1.bdcm*檔案。

2. 在 BDC 設計工具中，開啟 Business Data Connectivity 模型檔案。

3. 在設計師中，開啟捷徑功能表**Entity1**，然後選擇**刪除**。

4. 中**方案總管**，開啟捷徑功能表*Entity1.vb* （在 Visual Basic) 或*Entity1.cs* （在 C# 中)，然後選擇**刪除**.

5. 開啟捷徑功能表*Entity1Service.vb* （在 Visual Basic) 或*Entity1Service.cs* （在 C# 中)，然後選擇**刪除**。

## <a name="add-an-entity-to-the-model"></a>將實體新增至模型

將實體新增至模型。 您可以從 Visual Studio 中新增實體**工具箱**在 BDC 設計工具上。

1. 在功能表列上，選擇 [檢視] > [工具箱]。

2. 在上**BusinessDataConnectivity**索引標籤**工具箱**，加入**實體**在 BDC 設計工具上。

     新的實體會出現在設計工具。 Visual Studio 會加入檔案，稱為*EntityService.vb* （在 Visual Basic) 或*EntityService.cs* （在 C# 中) 至專案。

3. 在功能表列上選擇 **檢視** > **屬性** > **視窗**。

4. 在 **屬性**視窗中，將**名稱**屬性值**連絡人**。

5. 在設計工具中，開啟實體的捷徑功能表，選擇 **新增**，然後選擇**識別項**。

     新的識別碼會出現在實體中。

6. 在 [**屬性**] 視窗中，變更的識別項的名稱**ContactID**。

7. 在 **型別名稱**清單中，選擇**System.Int32**。

## <a name="add-a-specific-finder-method"></a>新增 Specific Finder 方法

若要啟用的 BDC 服務，以顯示特定的連絡人，您必須新增特定搜尋工具方法。 BDC 服務呼叫特定搜尋工具方法，當使用者選擇清單中的項目，並選擇**檢視項目**功能區上的按鈕。

加入連絡人實體中的特定搜尋工具方法，使用**BDC 方法詳細資料**視窗。 若要傳回特定實體，請在方法中加入程式碼。

1. 在 BDC 設計工具中，選擇**連絡人**實體。

2. 在功能表列上選擇 **檢視** > **其他 Windows** > **BDC 方法詳細資料**。

     [BDC 方法詳細資料] 視窗隨即開啟。

3. 在 **將方法加入**清單中，選擇**建立特定搜尋方法**。

     Visual Studio 會將下列項目加入至模型。 這些項目會出現在**BDC 方法詳細資料**視窗。

    - 名為 ReadItem 方法。

    - 方法的輸入的參數。

    - 方法的傳回參數。

    - 每個參數的型別描述項。

    - 方法執行個體方法。

4. 在 [ **BDC 方法詳細資料**] 視窗中，開啟所顯示的清單**連絡人**類型描述元，然後選擇**編輯**。

     **BDC 總管**隨即開啟，並提供模型的階層式檢視。

5. 中**屬性**] 視窗中，開啟清單旁**TypeName**屬性中，選擇**目前專案**索引標籤，然後選擇 [**連絡人**屬性。

6. 在**BDC 總管**，開啟捷徑功能表**連絡人**，然後選擇**加入類型描述元**。

     新的型別描述項，稱為**TypeDescriptor1**會出現在**BDC 總管**。

7. 在 **屬性**視窗中，將**名稱**屬性值**ContactID**。

8. 開啟清單旁**TypeName**屬性，然後選擇**Int32**。

9. 開啟清單旁**識別碼**屬性，然後選擇**ContactID**。

10. 重複步驟 6 以下列欄位的每個建立的型別描述元。

    |名稱|類型名稱|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |Phone|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. 在 BDC 設計工具上**連絡人**實體上，開啟**ReadItem**方法。

     連絡人服務程式碼檔會在 「 程式碼編輯器 」 中開啟。

12. 在 `ContactService`類別中，取代`ReadItem`為下列程式碼的方法。 這個程式碼會執行下列工作：

    - 從 AdventureWorks 資料庫的 Contact 資料表中擷取一筆記錄。

    - 傳回 BDC 服務連絡人實體。

    > [!NOTE]
    > 值取代`ServerName`欄位與您伺服器的名稱。

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>新增搜尋方法

若要啟用 BDC 服務，以顯示連絡人清單中，您必須新增搜尋方法。 將搜尋工具方法新增至連絡人實體，使用**BDC 方法詳細資料**視窗。 若要返回 BDC 服務中實體的集合，請在方法中加入程式碼。

1. 在 BDC 設計工具中，選擇**連絡人**實體。

2. 在 [ **BDC 方法詳細資料**] 視窗中，摺疊**ReadItem**節點。

3. 在 **將方法加入**清單底下**ReadList**方法中，選擇**建立搜尋方法**。

     Visual Studio 會新增方法，是傳回參數和型別描述項。

4. 在 BDC 設計工具上**連絡人**實體上，開啟**ReadList**方法。

     Contact 服務的程式碼檔案隨即在 [程式碼編輯器] 中開啟。

5. 在 `ContactService`類別中，取代`ReadList`為下列程式碼的方法。 這個程式碼會執行下列工作：

   - 從 AdventureWorks 資料庫的 [連絡人] 資料表中擷取資料。

   - 傳回 BDC 服務連絡人實體的清單。

     > [!NOTE]
     > 值取代`ServerName`欄位與您伺服器的名稱。

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>測試專案

當您執行專案時，SharePoint 網站隨即開啟，Visual Studio 會將您的模型加入至 Business Data Connectivity 服務。 參照連絡人實體的 SharePoint 中建立外部清單。 AdventureWorks 資料庫中的連絡人資料出現在清單中。

> [!NOTE]
> 您可能必須修改您在 SharePoint 中的安全性設定，您可以偵錯您的解決方案之前。 如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

1. 選擇 **F5** 鍵。

     SharePoint 網站隨即開啟。

2. 在上**站台動作**功能表上，選擇**更多選項**命令。

3. 上**建立**頁面上，選擇**外部清單** 範本，然後選擇**建立** 按鈕。

4. 命名自訂清單**連絡人**。

5. 選擇 [瀏覽] 按鈕旁**外部內容類型**欄位。

6. 在 **外部內容的型別選擇器**對話方塊方塊中，選擇**AdventureWorksContacts.BdcModel1.Contact**項目，然後再選擇 **建立** 按鈕。

     SharePoint 會建立一個外部清單，其中包含 AdventureWorks 範例資料庫中的連絡人。

7. 若要測試特定搜尋工具方法，請選擇清單中的連絡人。

8. 在功能區中，選擇**項目**索引標籤，然後選擇**檢視項目**命令。

     您選擇之連絡人的詳細資料隨即出現在表單上。

## <a name="next-steps"></a>後續步驟

您可以深入了解如何設計模型在 SharePoint 中的 BDC 服務從下列主題：

- [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)。
- [如何：新增更新者方法](../sharepoint/how-to-add-an-updater-method.md)。
- [如何：新增刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)。

## <a name="see-also"></a>另請參閱

[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)
[建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)
[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)
 [將商務資料整合到 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
