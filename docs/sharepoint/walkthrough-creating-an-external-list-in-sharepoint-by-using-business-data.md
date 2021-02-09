---
title: 使用商務資料在 SharePoint 中建立外部清單
description: 建立 BDC 服務的模型，以傳回商務資料庫中連絡人的相關資訊，然後使用此模型在 SharePoint 中建立外部清單。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dbf996a2d44f94e4571a332fa7a86d861d820d45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847709"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>逐步解說：使用商務資料在 SharePoint 中建立外部清單

 (BDC) 服務的商務資料連線能力，可讓 SharePoint 顯示來自後端伺服器應用程式、Web 服務和資料庫的商務資料。

本逐步解說將示範如何建立 BDC 服務的模型，以傳回範例資料庫中連絡人的相關資訊。 然後，您將使用此模型在 SharePoint 中建立外部清單。

本逐步解說將說明下列工作：

- 建立專案。
- 將實體加入至模型。
- 加入 finder 方法。
- 加入特定的搜尋工具方法。
- 測試專案。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成這個逐步解說：

- 支援的 Windows 和 SharePoint 版本。

- AdventureWorks 範例資料庫的存取權。 如需有關如何安裝 AdventureWorks 資料庫的詳細資訊，請參閱 [SQL Server 範例資料庫](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)。

## <a name="create-a-project-that-contains-a-bdc-model"></a>建立包含 BDC 模型的專案

1. 在 Visual Studio 的功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

     此時會開啟 [新增專案] 對話方塊。

2. 在 [ **Visual c #** ] 或 [ **Visual Basic**] 下，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 專案。

3. 在 [ **範本** ] 窗格中，選擇 [ **SharePoint 2010 專案**]，將專案命名為 **AdventureWorksTest**，然後選擇 [ **確定]** 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。 在此嚮導中，您可以指定要用來對專案進行錯用的網站，並設定解決方案的信任層級。

4. 選擇 [ **部署為伺服器陣列方案** ] 選項按鈕，以設定信任層級。

5. 選擇 [ **完成]** 按鈕以接受預設的本機 SharePoint 網站。

6. 在 **方案總管** 中，選擇 [SharePoint 專案] 節點。

7. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

     [ **加入新專案** ] 對話方塊隨即開啟。

8. 在 [ **範本** ] 窗格中，選擇 [ **商務資料連線模型 (伺服器陣列方案])**、將專案命名為 **Adventureworkscontacts.bdcmodel1.contact**，然後選擇 [ **加入** ] 按鈕。

## <a name="add-data-access-classes-to-the-project"></a>將資料存取類別加入至專案

1. 在功能表列上，選擇 [**工具**  >  **連接到資料庫]**。

     [新增連線] 對話方塊隨即開啟。

2. 將連接新增至 SQL Server AdventureWorks 範例資料庫。

     如需詳細資訊，請參閱 [新增/修改連接 (Microsoft SQL Server) ](/previous-versions/dxb6fxah(v=vs.140))。

3. 在 [ **方案總管**] 中選擇專案節點。

4. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

5. 在 [ **已安裝的範本** ] 窗格中，選擇 [ **資料** ] 節點。

6. 在 [ **範本** ] 窗格中，選擇 [ **LINQ to SQL 類別**]。

7. 在 [ **名稱** ] 方塊中指定 **AdventureWorks**，然後選擇 [ **加入** ] 按鈕。

     .dbml 檔案隨即加入至專案，而且物件關聯式設計工具 (O/R 設計工具) 便會開啟。

8. 在功能表列上，選擇 [ **View**  >  **伺服器總管**]。

9. 在 **伺服器總管** 中，展開代表 AdventureWorks 範例資料庫的節點，然後展開 [ **資料表]** 節點。

10. 將 **Contact (Person)** 資料表加入至 O/R 設計工具。

     實體類別隨即建立並出現在設計介面上。 Entity 類別的屬性會對應至 Contact (Person) 資料表中的資料行。

## <a name="remove-the-default-entity-from-the-bdc-model"></a>從 BDC 模型移除預設實體

**商務資料連線模型** 專案會將名為 Entity1 的預設實體加入至模型。 移除此實體。 稍後，您將會加入新的實體。 從空白模型開始，可減少完成逐步解說所需的步驟數目。

1. 在 **方案總管** 中，展開 [ **BdcModel1** ] 節點，然後開啟 *BdcModel1 .bdcm* 檔案。

2. 商務資料連線模型檔會在 BDC 設計工具中開啟。

3. 在設計工具中，開啟 **Entity1** 的快捷方式功能表，然後選擇 [ **刪除**]。

4. 在 **方案總管** 中，開啟 [Entity1.cs] 中的 [Visual Basic (*Entity1* ] 的快捷方式功能表，) 或 [c # 中的 (] ) ，然後選擇 [**刪除**]。

5. 在 Visual Basic) 中開啟 *Entity1Service* 的快捷方式功能表 (，或在 c # ) 中開啟 [ *Entity1Service.cs* (]，然後選擇 [ **刪除**]。

## <a name="add-an-entity-to-the-model"></a>將實體新增至模型

將實體新增至模型。 您可以從 Visual Studio 工具箱將實體加入至 BDC 設計 **工具** 。

1. 在功能表列上，選擇 [ **View**  >  **工具箱**]。

2. 在 [工具箱] 的 [ **BusinessDataConnectivity** ] 索引標籤上，將 **實體** 加入至 BDC 設計 **工具**。

     新的實體會出現在設計工具上。 Visual Studio 會將名為 *EntityService* (的檔案新增至 Visual Basic) 或 c # (中的 *EntityService.cs* ) 至專案。

3. 在功能表列上，選擇 [**視圖**  >  **屬性**  >  **視窗]**。

4. 在 [ **屬性** ] 視窗中，將 [ **名稱** ] 屬性值設定為 [ **連絡人**]。

5. 在設計工具中，開啟實體的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **識別碼**]。

     新的識別碼會出現在實體上。

6. 在 [ **屬性** ] 視窗中，將識別碼的名稱變更為 **ContactID**。

7. 在 [ **類型名稱** ] 清單中，選擇 [ **system.object**]。

## <a name="add-a-specific-finder-method"></a>新增特定搜尋工具方法

若要讓 BDC 服務顯示特定的連絡人，您必須加入特定的搜尋工具方法。 當使用者挑選清單中的專案，然後選擇功能區上的 [ **視圖專案** ] 按鈕時，BDC 服務會呼叫特定的搜尋工具方法。

使用 [ **BDC 方法詳細資料** ] 視窗，將特定的 Finder 方法新增至 Contact 實體。 若要傳回特定實體，請將程式碼加入至方法。

1. 在 BDC 設計工具上，選擇 [ **Contact** ] 實體。

2. 在功能表列上，選擇 [**查看**  >  **其他 Windows**  >  **BDC 方法詳細資料**]。

     [BDC 方法詳細資料] 視窗隨即開啟。

3. 在 [ **加入方法** ] 清單中，選擇 [ **建立特定的搜尋工具方法**]。

     Visual Studio 將下列元素加入至模型。 這些專案會出現在 [ **BDC 方法詳細資料** ] 視窗中。

    - 名為 ReadItem 的方法。

    - 方法的輸入參數。

    - 方法的傳回參數。

    - 每個參數的類型描述元。

    - 方法的方法實例。

4. 在 [ **BDC 方法詳細資料** ] 視窗中，開啟針對 [ **Contact** ] 類型描述元顯示的清單，然後選擇 [ **編輯**]。

     [ **BDC Explorer** ] 隨即開啟，並提供模型的階層式查看。

5. 在 [ **屬性** ] 視窗中，開啟 [ **TypeName** ] 屬性旁邊的清單，選擇 [ **目前的專案** ] 索引標籤，然後選擇 [ **Contact** ] 屬性。

6. 在 [ **BDC Explorer**] 中，開啟 [ **Contact**] 的快捷方式功能表，然後選擇 [ **加入類型描述** 元]。

     名為 **TypeDescriptor1** 的新類型描述元會出現在 **BDC Explorer** 中。

7. 在 [ **屬性** ] 視窗中，將 [ **名稱** ] 屬性值設定為 **ContactID**。

8. 開啟 [ **TypeName** ] 屬性旁的清單，然後選擇 [ **Int32**]。

9. 開啟 [ **識別碼** ] 屬性旁的清單，然後選擇 [ **ContactID**]。

10. 重複步驟6，為下列每個欄位建立類型描述元。

    |名稱|類型名稱|
    |----------|---------------|
    |名字|System.String|
    |姓氏|System.String|
    |電話|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. 在 BDC 設計工具的 [ **Contact** ] 實體上，開啟 **ReadItem** 方法。

     連絡人服務程式代碼檔案會在程式碼編輯器中開啟。

12. 在 `ContactService` 類別中， `ReadItem` 以下列程式碼取代方法。 此程式碼會執行下列工作：

    - 從 AdventureWorks 資料庫的 Contact 資料表中抓取記錄。

    - 將 Contact 實體傳回給 BDC 服務。

    > [!NOTE]
    > 將欄位的值取代為 `ServerName` 您伺服器的名稱。

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>新增 finder 方法

若要讓 BDC 服務將連絡人顯示在清單中，您必須加入搜尋工具方法。 使用 [ **BDC 方法詳細資料** ] 視窗，將 Finder 方法新增至 Contact 實體。 若要將實體的集合傳回給 BDC 服務，請將程式碼加入至方法。

1. 在 BDC 設計工具中，選擇 [ **Contact** ] 實體。

2. 在 [ **BDC 方法詳細資料** ] 視窗中，折迭 [ **ReadItem** ] 節點。

3. 在 [ **加入方法** ] 清單中的 [ **ReadList** ] 方法下，選擇 [ **建立 Finder 方法**]。

     Visual Studio 加入方法、傳回參數和類型描述元。

4. 在 BDC 設計工具的 [ **Contact** ] 實體上，開啟 **ReadList** 方法。

     Contact 服務的程式碼檔案隨即在 [程式碼編輯器] 中開啟。

5. 在 `ContactService` 類別中， `ReadList` 以下列程式碼取代方法。 此程式碼會執行下列工作：

   - 從 AdventureWorks 資料庫的 Contacts 資料表中取出資料。

   - 傳回 BDC 服務的連絡人實體清單。

     > [!NOTE]
     > 將欄位的值取代為 `ServerName` 您伺服器的名稱。

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>測試專案

當您執行專案時，會開啟 SharePoint 網站，並 Visual Studio 將您的模型加入至商務資料連線服務。 在 SharePoint 中建立參考 Contact 實體的外部清單。 AdventureWorks 資料庫中連絡人的資料會出現在清單中。

> [!NOTE]
> 您可能必須先修改 SharePoint 中的安全性設定，才能將方案進行偵錯工具。 如需詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

1. 選擇 **F5** 鍵。

     SharePoint 網站隨即開啟。

2. 在 [ **網站動作** ] 功能表上，選擇 [ **更多選項** ] 命令。

3. 在 [ **建立** ] 頁面上，選擇 [ **外部清單** ] 範本，然後選擇 [ **建立** ] 按鈕。

4. 將自訂清單命名為「 **連絡人**」。

5. 選擇 [ **外部內容類型** ] 欄位旁的 [流覽] 按鈕。

6. 在 [ **外部內容類型選擇器** ] 對話方塊中，選擇 [adventureworkscontacts.bdcmodel1.contact]、[ **BdcModel1** ] 專案，然後選擇 [ **建立** ] 按鈕。

     SharePoint 會建立一個外部清單，其中包含 AdventureWorks 範例資料庫中的連絡人。

7. 若要測試特定搜尋工具方法，請選擇清單中的連絡人。

8. 在功能區上，選擇 [ **專案** ] 索引標籤，然後選擇 [ **View Item** ] 命令。

     您選擇之連絡人的詳細資料隨即出現在表單上。

## <a name="next-steps"></a>下一步

您可以從下列主題深入瞭解如何在 SharePoint 中設計 BDC 服務的模型：

- [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)。
- [如何：加入更新程式方法](../sharepoint/how-to-add-an-updater-method.md)。
- [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)。

## <a name="see-also"></a>另請參閱

[設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md) 
[建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md) 
[BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md) 
將[商務資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)