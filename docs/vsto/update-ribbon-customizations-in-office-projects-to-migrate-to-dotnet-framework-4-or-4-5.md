---
title: 更新已遷移至 .NET Framework 4.5 的功能區自訂
description: 瞭解如果目標 framework 變更為 .NET Framework 4 或更新版本，您必須對專案程式碼進行變更。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a831bced793f13394a89d278a6be1cda959c775a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527935"
---
# <a name="update-ribbon-customizations-migrated-to-net-framework-45"></a>更新已遷移至 .NET Framework 4.5 的功能區自訂

  如果您的專案包含使用 **功能區 (視覺化設計工具)** 專案專案所建立的功能區自訂，則您必須在目標 framework 變更為或更新版本時，對專案程式碼進行下列變更 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 。

- 修改產生的功能區程式碼。

- 修改在執行時間具現化功能區控制項的任何程式碼、處理功能區事件，或以程式設計方式設定功能區元件的位置。

## <a name="update-the-generated-ribbon-code"></a>更新產生的功能區程式碼
 如果專案的目標 Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您必須執行下列步驟變更功能區項目產生的程式碼。 您需要更新的程式碼檔是根據程式語言和您建立專案的方式而定：

- 在 Visual Basic 專案中，或您在中建立的 Visual c # 專案中，或 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] 執行功能區程式碼後端檔案中的所有步驟 (*yourribbonitem.designer.vb*。Designer.cs 或 *yourribbonitem.designer.vb*。設計工具 .vb) 。 若要查看 Visual Basic 專案中的程式碼後端檔案，請按一下 **方案總管** 中的 [**顯示所有** 檔案] 按鈕。

- 在您于 Visual Studio 2008 中建立然後升級至的 Visual c # 專案中 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] ，執行功能區程式碼檔案中的前兩個步驟 (*yourribbonitem.designer.vb*.cs 或 *yourribbonitem.designer.vb*.Vb) ，然後執行功能區程式碼後端檔案中的其餘步驟。

### <a name="to-change-the-generated-ribbon-code"></a>變更產生的功能區程式碼

1. 修改功能區類別的宣告，使其衍生自 <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> 而不是 `Microsoft.Office.Tools.Ribbon.OfficeRibbon`。

2. 修改功能區類別的建構函式，如下所示。 如果您已將任何自己的程式碼加入至建構函式，請不要變更您的程式碼。 在 Visual Basic 專案中，僅修改無參數建構函式， 忽略其他建構函式。

     下列程式碼範例顯示在目標為 .NET Framework 3.5 的專案中，功能區類別的預設建構函式。

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
    {
        InitializeComponent();
    }
    ```

     下列程式碼範例顯示目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本之專案的功能區類別預設建構函式。

    ```vb
    Public Sub New()
        MyBase.New(Globals.Factory.GetRibbonFactory())
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
        : base(Globals.Factory.GetRibbonFactory())
    {
        InitializeComponent();
    }
    ```

3. 在 `InitializeComponent` 方法中，修改建構功能區控制項的任何程式碼，讓程式碼改用 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> 物件的其中一個協助程式方法。

    > [!NOTE]
    > 在 Visual C# 專案中，您必須展開名為 `Component Designer generated code` 的區域，以查看 `InitializeComponent` 方法。

     例如，假設在目標為 .NET Framework 3.5 的專案中，您的檔案包含下列執行個體化名為 `button1` 之 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> 的程式碼行。

    ```vb
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()
    ```

    ```csharp
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();
    ```

     在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本的專案中，您必須改用下列程式碼。

    ```vb
    Me.button1 = Me.Factory.CreateRibbonButton()
    ```

    ```csharp
    this.button1 = this.Factory.CreateRibbonButton();
    ```

     如需功能區控制項之 helper 方法的完整清單，請參閱具現 [化功能區控制項](#ribboncontrols)。

4. 在 Visual C# 專案中，將 `InitializeComponent` 方法中任何使用 <xref:System.EventHandler%601> 委派的程式碼行，修改為使用特定功能區委派。

     例如，假設在目標為 .NET Framework 3.5 的專案中，您的檔案包含下列處理 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> 事件的程式碼行。

    \<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> 在以或更新版本為目標的專案中 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ，您必須改為使用下列程式碼。

    \<CodeContentPlaceHolder>9 </CodeContentPlaceHolder> 如需功能區委派的完整清單，請參閱 [處理功能區事件](#ribbonevents)。

5. 在 Visual Basic 專案中，尋找位於檔案結尾的 `ThisRibbonCollection` 類別。 修改此類別的宣告，使其不再繼承自 `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection`。

## <a name="instantiate-ribbon-controls"></a><a name="ribboncontrols"></a> 具現化功能區控制項
 您必須修改可動態執行個體化功能區控制項的任何程式碼。 在目標為 .NET Framework 3.5 的專案中，功能區控制項是您在特定案例中可以直接執行個體化的類別。 在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本的專案中，這些控制項是您無法直接執行個體化的介面。 您必須使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> 物件提供的方法建立控制項。

 有兩種方法可以存取 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> 物件：

- 使用功能區類別的 Factory 屬性。 請從功能區類別中的程式碼使用此方法。

- 使用 `Globals.Factory.GetRibbonFactory` 方法。 請從功能區類別外的程式碼使用此方法。 如需全域類別的詳細資訊，請參閱 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。

  下列程式碼範例示範如何為目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本的專案，在功能區類別中建立 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton>。

\<CodeContentPlaceHolder>10 </CodeContentPlaceHolder> 
 \<CodeContentPlaceHolder> 11 </CodeContentPlaceHolder> 下表列出您可以用程式設計方式建立的控制項，以及用來在以或更新版本為目標的專案中建立控制項的方法 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 。

|控制|用於 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和更新版本專案的 RibbonFactory 方法|
|-------------| - |
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|

## <a name="handle-ribbon-events"></a><a name="ribbonevents"></a> 處理功能區事件
 您必須修改可處理功能區控制項事件的任何程式碼。 在目標為 .NET Framework 3.5 的專案中，這些事件是由泛型 <xref:System.EventHandler%601> 委派處理。 在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本的專案中，這些事件現在是由其他委派處理。

 下表列出目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本專案中的功能區事件以及它們的相關委派。

|事件|在 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 及更新版本的專案中要使用的委派|
|-----------| - |
|產生的功能區類別中的 <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> 事件|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>以程式設計方式設定功能區元件的位置
 您必須修改可設定功能區群組、索引標籤或控制項位置的任何程式碼。 在目標為 .NET Framework 3.5 的專案中，您可以使用靜態 `Microsoft.Office.Tools.Ribbon.RibbonPosition` 類別的 `AfterOfficeId` 和 `BeforeOfficeId` 方法，指派群組、索引標籤或控制項的 `Position` 屬性。 在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本專案中，您必須使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> 物件所提供的 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> 屬性來存取這些方法。

 有兩種方法可以存取 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> 物件：

- 使用功能區類別的 `Factory` 屬性。 請從功能區類別中的程式碼使用此方法。

- 使用 `Globals.Factory.GetRibbonFactory` 方法。 請從功能區類別外的程式碼使用此方法。 如需全域類別的詳細資訊，請參閱 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。

  下列程式碼範例示範如何為目標為 .NET Framework 3.5 的專案，在功能區類別中設定索引標籤的 `Position` 屬性。

```vb
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");
```

 下列程式碼範例示範在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 的專案中執行相同工作。

```vb
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");
```

## <a name="see-also"></a>另請參閱
- [將 Office 方案遷移至 .NET Framework 4 或更新版本](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
