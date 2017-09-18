---
title: "建立設定分類 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "設定檔設定，建立類別目錄"
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 39
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 39
---
# 建立設定分類
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在本逐步解說您建立 Visual Studio 設定類別目錄，並使用它來儲存值，並從設定檔還原值。 設定類別是一群相關的屬性顯示為 「 自訂設定點 」。也就是為核取方塊，在 **匯入和匯出設定** 精靈。 \(您可以找到 **工具** 功能表。\) 設定會儲存或還原為類別，並個別設定不會顯示在精靈中。 如需詳細資訊，請參閱[在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 從建立設定分類 <xref:Microsoft.VisualStudio.Shell.DialogPage> 類別。  
  
 若要開始本逐步解說，您必須先完成的第一個區段 [建立選項\] 頁面](../Topic/Creating%20an%20Options%20Page.md)。 產生的選項屬性方格可讓您檢查及變更的類別中的屬性。 設定檔中儲存屬性類別目錄之後，您會檢查檔案以查看儲存屬性值的方式。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 建立設定分類  
 本節中，您可以使用自訂設定點來儲存和還原類別設定的值。  
  
#### 若要建立設定類別  
  
1.  完成 [建立選項\] 頁面](../Topic/Creating%20an%20Options%20Page.md)。  
  
2.  開啟 VSPackage.resx 檔案並新增下列三個字串資源︰  
  
    |名稱|值|  
    |--------|-------|  
    |106|我的類別|  
    |107|我的設定|  
    |108|OptionInteger 和 OptionFloat|  
  
     這會建立資源，該名稱為 「 My Category 」 的類別、 物件 「 我的設定 」 和類別描述 「 OptionInteger 和 OptionFloat 」。  
  
    > [!NOTE]
    >  三者之中，只有類別名稱不在 \[匯入和匯出設定精靈\]。  
  
3.  在 MyToolsOptionsPackage.cs，加入 `float` 屬性名為 `OptionFloat` 到 `OptionPageGrid` 類別，如下列範例所示。  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  `OptionPageGrid` 現在名為 「 My Category 」 類別目錄包含兩個屬性， `OptionInteger` 和 `OptionFloat`。  
  
4.  新增 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 至 `MyToolsOptionsPackage` 類別和類別名稱 「 My Category 」 給它，讓它 ObjectName 「 我的設定\]，再 isToolsOptionPage 設為 true。 CategoryResourceID、 objectNameResourceID 和 DescriptionResourceID 設對應識別碼稍早建立的字串資源。  
  
    ```c#  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  建置此專案並開始偵錯。 實驗執行個體中您應該會看到 **我的格線頁** 現在具有整數和浮點值。  
  
## 檢查設定檔  
 本節中，您可以匯出屬性類別目錄值來設定檔案。 檢查檔案，並再匯入回屬性類別目錄的值。  
  
1.  按 F5 偵錯模式中啟動專案。 這會啟動實驗執行個體。  
  
2.  開啟 **工具 \/ 選項** \] 對話方塊。  
  
3.  在樹狀檢視中的左窗格中，依序展開 **My Category** 然後按一下 \[ **我的格線頁**。  
  
4.  值變更 **OptionFloat** 至 3.1416 和 **OptionInteger** 到 12。 按一下 \[確定\]。  
  
5.  按一下 \[**工具**\] 功能表上的 \[**匯入和匯出設定**\]。  
  
     **匯入和匯出設定** 精靈\] 隨即出現。  
  
6.  請確定 **匯出選取的環境設定** 已選取，然後按一下 \[ **下一步**。  
  
     **選擇要匯出的設定** \] 頁面隨即出現。  
  
7.  按一下 \[ **我的設定**。  
  
     **描述** 變成 **OptionInteger 和 OptionFloat**。  
  
8.  請確定 **我的設定** 是唯一的類別，已選取，然後按一下 \[ **下一步**。  
  
     **程式設定檔名稱** \] 頁面隨即出現。  
  
9. 新的設定檔命名 `MySettings.vssettings` 並將它儲存在適當的目錄中。 按一下 \[**完成**\]。  
  
     **匯出完成** 頁面會報告已順利匯出您的設定。  
  
10. 在 **檔案** 功能表上，指向 **開啟**, ，然後按一下 \[ **檔案**。 找出 `MySettings.vssettings` 並開啟它。  
  
     您可以找到您匯出的檔案 （您的 Guid 會有所不同） 的下一節中的屬性類別目錄。  
  
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
  
     請注意完整類別名稱的前面加上底線後接物件名稱的類別名稱加入正確的。 OptionFloat 和 OptionInteger 會出現在類別中，以及其匯出值。  
  
11. 關閉 \[設定檔，而不變更它。  
  
12. 上 **工具** \] 功能表上，按一下 \[ **選項**, ，展開 **My Category**, ，按一下 \[ **我的格線頁** ，然後變更的值 **OptionFloat** 為 1.0 和 **OptionInteger** 為 1。 按一下 \[確定\]。  
  
13. 在 **工具** \] 功能表上，按一下 \[ **匯入和匯出設定**, ，請選取 **匯入選取的環境設定**, ，然後按一下 \[ **下一步**。  
  
     **儲存目前設定** \] 頁面隨即出現。  
  
14. 選取 **否，只需匯入新設定** 然後按一下 \[ **下一步**。  
  
     **選擇的設定集合匯入** \] 頁面隨即出現。  
  
15. 選取 `MySettings.vssettings` 檔案中 **我的設定** 樹狀結構檢視中的節點。 如果檔案不在樹狀檢視中，按一下 \[ **瀏覽** 找到它。 按 \[**下一步**\]。  
  
     **選擇要匯入的設定** \] 對話方塊隨即出現。  
  
16. 請確定 **我的設定** 已選取，然後按一下 \[ **完成**。 當 **匯入完成** 頁面出現時，按一下 **關閉**。  
  
17. 在 **工具** \] 功能表上，按一下 \[ **選項**, ，展開 **My Category**, ，按一下 **我的格線頁** 並確認已還原屬性類別目錄值。