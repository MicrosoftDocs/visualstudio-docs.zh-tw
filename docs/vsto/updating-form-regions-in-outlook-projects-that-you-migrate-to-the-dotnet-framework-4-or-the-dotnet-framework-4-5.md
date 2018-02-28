---
title: "更新您要移轉至.NET Framework 4 或.NET Framework 4.5 之 Outlook 專案中的表單區域 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 5c2f3e3951ac46a2459545b51fafa45ecc6b86f9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="updating-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 之 Outlook 專案中的表單區域
  如果 Outlook VSTO 增益集專案的目標 Framework 與表單區域的變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您就必須在執行階段中，針對產生的表單區域程式碼以及可執行個體化特定表單區域類別的任何程式碼，進行一些變更。  
  
## <a name="updating-the-generated-form-region-code"></a>更新產生的表單區域程式碼  
 如果專案的目標 Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您必須變更產生的表單區域程式碼。 您要針對 Visual Studio 中設計的表單區域所做的變更，與針對從 Outlook 匯入的表單區域所做的變更並不相同。 如需這些表單區域類型之間差異的詳細資訊，請參閱 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)。  
  
#### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>若要更新您在 Visual Studio 中所設計之表單區域產生的程式碼  
  
1.  在程式碼編輯器中，開啟表單區域程式碼後置檔案。 此檔案的名稱為 *YourFormRegion*.Designer.cs 或 *YourFormRegion*.Designer.vb。 若要查看 Visual Basic 專案中的這個檔案，請按一下 [方案總管]  中的 [顯示所有檔案] 按鈕。  
  
2.  修改表單區域類別的宣告，使其衍生自<xref:Microsoft.Office.Tools.Outlook.FormRegionBase>而不是 Microsoft.Office.Tools.Outlook.FormRegionControl。  
  
3.  修改表單區域類別的建構函式，如下列程式碼範例所示。  
  
     下列程式碼範例顯示在目標為 .NET Framework 3.5 的專案中，表單區域類別的建構函式。  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
     下列程式碼範例顯示在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]的專案中，表單區域類別的建構函式。  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
4.  修改 `InitializeManifest` 方法的簽章，如下所示。 請勿修改方法中的程式碼；此程式碼表示您在設計工具中套用的表單區域設定。 在 Visual C# 專案中，您必須展開名為 `Form Region Designer generated code` 的區域，以查看此方法。  
  
     下列程式碼範例顯示在目標為 .NET Framework 3.5 的專案中， `InitializeManifest` 方法的簽章。  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
     下列程式碼範例顯示在目標為 `InitializeManifest` 的專案中， [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]方法的簽章。  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,   
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,   
        Microsoft.Office.Tools.Outlook.Factory factory)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
5.  將新的 Outlook 表單區域項目加入專案。 開啟新表單區域的程式碼後置檔案，在檔案中尋找 *YourNewFormRegion*`Factory` 和 `WindowFormRegionCollection` 類別，然後將這些類別複製到剪貼簿。  
  
6.  刪除您加入專案的新表單區域。  
  
7.  在您要更新以便在改變目標的專案中使用之表單區域的程式碼後置檔案中，尋找 *YourOriginalFormRegion*`Factory` 和 `WindowFormRegionCollection` 類別，並且將這兩個類別取代為您從新的表單區域複製的程式碼。  
  
8.  在 *YourNewFormRegion*`Factory` 和 `WindowFormRegionCollection` 類別中搜尋 *YourNewFormRegion* 類別的所有參考，並且將每一個參考變更為 *YourOriginalFormRegion* 類別。 例如，如果您要更新的表單區域名為 `SalesDataFormRegion` ，而您在步驟 5 中建立的新表單區域名為 `FormRegion1`，則將 `FormRegion1` 的所有參考變更為 `SalesDataFormRegion`。  
  
#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>若要更新您從 Outlook 匯入之表單區域產生的程式碼  
  
1.  在程式碼編輯器中，開啟表單區域程式碼後置檔案。 此檔案的名稱為 *YourFormRegion*.Designer.cs 或 *YourFormRegion*.Designer.vb。 若要查看 Visual Basic 專案中的這個檔案，請按一下 [方案總管]  中的 [顯示所有檔案] 按鈕。  
  
2.  修改表單區域類別的宣告，使其衍生自<xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase>而不是 Microsoft.Office.Tools.Outlook.ImportedFormRegion。  
  
3.  修改表單區域類別的建構函式，如下列程式碼範例所示。  
  
     下列程式碼範例顯示在目標為 .NET Framework 3.5 的專案中，表單區域類別的建構函式。  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
     下列程式碼範例顯示在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]的專案中，表單區域類別的建構函式簽章。  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
4.  針對在表單區域類別中初始化控制項的 `InitializeControls` 方法中的每一個程式碼行修改程式碼，如下所示。  
  
     下列程式碼範例顯示如何在目標為 .NET Framework 3.5 的專案中初始化控制項。 在此程式碼，GetFormRegionControl 方法具有指定之控制項的傳回類型的型別參數。  
  
    ```vb  
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")  
    ```  
  
    ```csharp  
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");  
    ```  
  
     下列程式碼範例顯示如何在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]的專案中初始化控制項。 在此程式碼中， <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> 方法沒有類型參數。 您必須將傳回值轉型成要初始化之控制項的類型。  
  
    ```vb  
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)  
    ```  
  
    ```csharp  
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");  
    ```  
  
5.  將新的 Outlook 表單區域項目加入專案。 開啟新表單區域的程式碼後置檔案，在檔案中尋找 *YourNewFormRegion*`Factory` 和 `WindowFormRegionCollection` 類別，然後將這些類別複製到剪貼簿。  
  
6.  刪除您加入專案的新表單區域。  
  
7.  在您要更新以便在改變目標的專案中使用之表單區域的程式碼後置檔案中，尋找 *YourOriginalFormRegion*`Factory` 和 `WindowFormRegionCollection` 類別，並且將這兩個類別取代為您從新的表單區域複製的程式碼。  
  
8.  在 *YourNewFormRegion*`Factory` 和 `WindowFormRegionCollection` 類別中搜尋 *YourNewFormRegion* 類別的所有參考，並且將每一個參考變更為 *YourOriginalFormRegion* 類別。 例如，如果您要更新的表單區域名為 `SalesDataFormRegion` ，而您在步驟 5 中建立的新表單區域名為 `FormRegion1`，則將 `FormRegion1` 的所有參考變更為 `SalesDataFormRegion`。  
  
## <a name="instantiating-form-region-classes"></a>執行個體化表單區域類別  
 您必須修改可動態執行個體化特定表單區域類別的任何程式碼。 在.NET Framework 3.5 為目標的專案中，您可以直接執行個體化表單區域類別，例如 Microsoft.Office.Tools.Outlook.FormRegionManifest。 在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本的專案中，這些類別是您無法直接執行個體化的介面。  
  
 如果您的專案的目標 framework 變更為[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更新版本中，您必須使用具現化介面 Globals.Factory 屬性所提供的方法。 如需 Globals.Factory 屬性的詳細資訊，請參閱[全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。  
  
 下表列出的表單區域類型和方法，可用來執行個體化目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本專案中的類型。  
  
|類型|使用的 Factory 方法|  
|----------|---------------------------|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|  
  
## <a name="see-also"></a>請參閱  
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)  
  