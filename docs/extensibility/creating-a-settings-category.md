---
title: Creating a Settings Category |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: afbb16d3f5bd9d9278ba6e787a6bba673cc28acb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910006"
---
# <a name="create-a-settings-category"></a>建立設定類別
在本逐步解說您可以建立 Visual Studio 設定類別目錄，並使用它來儲存值，並還原從設定檔的值。 設定類別是一組顯示為 「 自訂設定點; 」 的相關內容也就是為核取方塊**匯入和匯出設定**精靈。 (您可以上找到**工具**功能表。)設定會儲存或還原為類別，並個別設定不會顯示在精靈中。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
 您建立設定類別從<xref:Microsoft.VisualStudio.Shell.DialogPage>類別。  
  
 若要開始本逐步解說中，您必須先完成的第一個區段[建立選項頁面](../extensibility/creating-an-options-page.md)。 產生的選項屬性方格可讓您檢查及變更的類別中的屬性。 您將屬性分類儲存在設定檔之後，您會檢查檔案以查看屬性值的儲存方式。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="create-a-settings-category"></a>建立設定類別  
 在本節中，您可以使用自訂設定點儲存和還原設定類別的值。  
  
### <a name="to-create-a-settings-category"></a>若要建立設定類別  
  
1.  完成[建立選項頁面](../extensibility/creating-an-options-page.md)。  
  
2.  開啟*VSPackage.resx*檔案，並新增下列三個字串資源：  
  
    |名稱|值|  
    |----------|-----------|  
    |106|我的類別目錄|  
    |107|我的設定|  
    |108|OptionInteger 和 OptionFloat|  
  
     這會建立資源，該名稱"My Category"的類別、 物件"My Settings"和類別描述 「 OptionInteger 和 OptionFloat"。  
  
    > [!NOTE]
    >  三者之中，只有類別名稱未出現在**匯入和匯出設定**精靈。  
  
3.  在  *MyToolsOptionsPackage.cs*，新增`float`名為屬性`OptionFloat`到`OptionPageGrid`類別，如下列範例所示。  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  `OptionPageGrid`現在名為"My Category"類別目錄包含兩個屬性，`OptionInteger`和`OptionFloat`。  
  
4.  新增<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>至`MyToolsOptionsPackage`類別並為它提供類別名稱"My Category"，讓它 ObjectName"My Settings"，再 isToolsOptionPage 設為 true。 設定 categoryResourceID、 objectNameResourceID 和 DescriptionResourceID 對應識別碼稍早建立的字串資源。  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  建置此專案並開始偵錯。 在實驗執行個體您應該會看到**我的格線頁**現在有整數和浮點數的值。  
  
## <a name="examine-the-settings-file"></a>檢查設定檔  
 在本節中，您可以匯出屬性類別目錄值設定檔。 您檢查檔案，並再將值匯入回屬性類別目錄。  
  
1.  在 偵錯模式中啟動專案，藉由按下**F5**。 這會啟動實驗執行個體。  
  
2.  開啟**工具** > **選項**對話方塊。  
  
3.  在樹狀檢視中的左窗格中，依序展開**My Category** ，然後按一下**我的格線頁**。  
  
4.  值變更**OptionFloat** 3.1416 到並**OptionInteger**到 12。 按一下 [確定 **Deploying Office Solutions**]。  
  
5.  在 **工具**功能表上，按一下**匯入和匯出設定**。  
  
     **匯入和匯出設定** 精靈隨即出現。  
  
6.  請確定**匯出選取的環境設定**已選取，然後按一下**下一步**。  
  
     **選擇要匯出的設定**頁面隨即出現。  
  
7.  按一下 **我的設定**。  
  
     **描述**變更為**OptionInteger 和 OptionFloat**。  
  
8.  請確定**My Settings**是唯一的類別，已選取，然後按一下**下一步**。  
  
     **名稱設定檔案**頁面隨即出現。  
  
9. 新的設定檔命名*MySettings.vssettings*並將它儲存在適當的目錄。 按一下 [ **完成**]。  
  
     **匯出完成**頁面會報告已成功匯出您的設定。  
  
10. 在上**檔案**功能表上，指向**開放**，然後按一下**檔案**。 找出*MySettings.vssettings*並將它開啟。  
  
     您可以找到您匯出的檔案 （您 Guid 將會不同） 的下一節中的屬性分類。  
  
    ```  
    <Category name="My Category_My Settings"   
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"   
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"   
          RegisteredName="My Category_My Settings">  
          PackageName="MyToolsOptionsPackage">  
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>   
       <PropertyValue name="OptionInteger">12</PropertyValue>   
    </Category>  
    ```  
  
     請注意完整類別名稱正確的分類名稱，後面接著物件名稱前面加上底線。 OptionFloat 和 OptionInteger 會出現在類別中，以及其匯出的值。  
  
11. 關閉 設定檔，而不變更它。  
  
12. 在上**工具**] 功能表中，按一下**選項**，展開**My Category**，按一下 [**我的格線頁**然後再將值變更**OptionFloat**為 1.0 和**OptionInteger**為 1。 按一下 [確定 **Deploying Office Solutions**]。  
  
13. 在上**工具** 功能表中，按一下**匯入和匯出設定**，選取**匯入選取的環境設定**，然後按一下**下一步**。  
  
     **儲存目前的設定**頁面隨即出現。  
  
14. 選取 [**否，只需匯入新的設定**，然後按一下**下一步]**。  
  
     **選擇的設定集合來匯入**頁面隨即出現。  
  
15. 選取  *MySettings.vssettings*中的檔案**我的設定**樹狀檢視的節點。 如果檔案不會出現在 [樹狀] 檢視中，按一下**瀏覽**並找到它。 按 [ **下一步**]。  
  
     **選擇要匯入設定** 對話方塊隨即出現。  
  
16. 請確定**My Settings**已選取，然後按一下**完成**。 當**匯入完整** 頁面出現時，按一下**關閉**。  
  
17. 上**工具**功能表上，按一下**選項**，展開**My Category**，按一下 **我的格線頁**並確認屬性類別目錄值具有已還原。