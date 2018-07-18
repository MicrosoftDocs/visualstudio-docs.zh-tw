---
title: 建立設定類別 |Microsoft 文件
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
ms.openlocfilehash: 22a625466dd8a94ba1dbe67ef6f05bec68954d2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107494"
---
# <a name="creating-a-settings-category"></a>建立設定類別
在此逐步解說中您建立 Visual Studio 設定類別目錄，並使用它來儲存值，並從設定檔案還原值。 設定類別是一群相關的屬性顯示為 「 自訂設定點。 」也就是為核取方塊在**匯入和匯出設定**精靈。 (您可以在它找到**工具**功能表。)儲存或還原為類別目錄時，設定和個別的設定不會顯示在精靈中。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
 您建立設定類別從<xref:Microsoft.VisualStudio.Shell.DialogPage>類別。  
  
 若要開始本逐步解說，您必須先完成的第一個區段[建立選項頁面](../extensibility/creating-an-options-page.md)。 產生的選項屬性方格可讓您檢查及變更的類別中的屬性。 儲存屬性類別目錄中的設定檔之後，您可以檢查檔案以查看儲存屬性值的方式。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-settings-category"></a>建立設定類別  
 在本節中，您可以使用自訂設定點來儲存和還原設定類別目錄的值。  
  
#### <a name="to-create-a-settings-category"></a>若要建立設定類別  
  
1.  完成[建立選項頁面](../extensibility/creating-an-options-page.md)。  
  
2.  開啟 VSPackage.resx 檔案並加入下列三個字串資源：  
  
    |名稱|值|  
    |----------|-----------|  
    |106|我的類別目錄|  
    |107|我的設定|  
    |108|OptionInteger 和 OptionFloat|  
  
     這會建立資源，該名稱 「 我的類別目錄 」 的類別、 物件 「 我的設定 」 和類別目錄描述 「 OptionInteger 和 OptionFloat"。  
  
    > [!NOTE]
    >  這三個欄位中，只有類別名稱不在匯入和匯出設定精靈。  
  
3.  在 MyToolsOptionsPackage.cs，加入`float`屬性名為`OptionFloat`至`OptionPageGrid`類別，如下列範例所示。  
  
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
    >  `OptionPageGrid`現在名為 「 我的類別目錄 」 類別目錄包含兩個屬性，`OptionInteger`和`OptionFloat`。  
  
4.  新增<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>至`MyToolsOptionsPackage`類別和類別名稱 「 我的類別目錄 」 提供給它，讓它 ObjectName [我的設定]，再 isToolsOptionPage 設為 true。 CategoryResourceID、 objectNameResourceID 和 DescriptionResourceID 設識別碼稍早建立的對應字串資源。  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  建置此專案並開始偵錯。 在實驗執行個體您應該會看到**我的格線頁**現在具有整數和浮點數的值。  
  
## <a name="examining-the-settings-file"></a>檢查設定檔  
 在本節中，您將屬性類別目錄值匯出的設定檔。 檢查檔案，並再將值匯回屬性類別目錄。  
  
1.  按 f5 鍵偵錯模式啟動專案。 這樣會啟動實驗執行個體。  
  
2.  開啟**工具 / 選項**對話方塊。  
  
3.  在樹狀檢視中的左窗格中，依序展開**我類別**，然後按一下 **我的格線頁**。  
  
4.  值變更**OptionFloat**至 3.1416 和**OptionInteger**到 12。 按一下 [確定 **Deploying Office Solutions**]。  
  
5.  在**工具**功能表上，按一下 **匯入和匯出設定**。  
  
     **匯入和匯出設定**精靈 隨即出現。  
  
6.  請確定**匯出選取的環境設定**已選取，然後按一下**下一步**。  
  
     **選擇要匯出的設定**頁面隨即出現。  
  
7.  按一下**我的設定**。  
  
     **描述**變為**OptionInteger 和 OptionFloat**。  
  
8.  請確定**我的設定**是唯一的類別目錄，已選取，然後按一下**下一步**。  
  
     **程式設定檔名稱**頁面隨即出現。  
  
9. 新的設定檔命名`MySettings.vssettings`並將它儲存在適當的目錄中。 按一下 [ **完成**]。  
  
     **匯出完成**頁面會報告已順利匯出您的設定。  
  
10. 在**檔案**功能表上，指向**開啟**，然後按一下 **檔案**。 找出`MySettings.vssettings`並開啟它。  
  
     您可以找到您匯出的檔案 （您的 Guid 會不同） 的下列區段中的屬性類別目錄。  
  
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
  
     請注意完整類別名稱正確的前面加上底線後接物件名稱的類別名稱。 OptionFloat 和 OptionInteger 會出現在類別中，以及其匯出的值。  
  
11. 關閉 設定檔，而不變更它。  
  
12. 上**工具**功能表上，按一下**選項**，依序展開**我類別**，按一下**我的格線頁**然後再將值變更**OptionFloat**為 1.0 和**OptionInteger**設為 1。 按一下 [確定 **Deploying Office Solutions**]。  
  
13. 上**工具**功能表上，按一下 **匯入和匯出設定**，選取**匯入選取的環境設定**，然後按一下 **下一步**。  
  
     **儲存目前設定**頁面隨即出現。  
  
14. 選取**否，只需匯入新的設定**，然後按一下 **下一步**。  
  
     **選擇的設定集合匯入**頁面隨即出現。  
  
15. 選取`MySettings.vssettings`檔案**我的設定**樹狀結構檢視中的節點。 如果檔案不會出現在樹狀檢視中，按一下**瀏覽**找到它。 按 [ **下一步**]。  
  
     **選擇要匯入的設定** 對話方塊隨即出現。  
  
16. 請確定**我的設定**已選取，然後按一下**完成**。 當**匯入完成**頁面出現時，按一下**關閉**。  
  
17. 上**工具**功能表上，按一下**選項**，依序展開**我類別**，按一下**我的格線頁**，並確認有屬性類別目錄值已還原。