---
title: "公開屬性，以 [屬性] 視窗 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7aed43ac4248c9bfd1e43d5e6c732a4fef3af529
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-properties-to-the-properties-window"></a>公開屬性，以 [屬性] 視窗
本逐步解說會公開公用屬性物件與**屬性**視窗。 您對這些屬性的變更會反映在**屬性**視窗。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="exposing-properties-to-the-properties-window"></a>公開屬性，以 [屬性] 視窗  
 在本節中，方法，您可以建立自訂的工具視窗，並顯示相關聯的視窗窗格物件中的公用屬性**屬性**視窗。  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>若要公開屬性，以 [屬性] 視窗  
  
1.  每個 Visual Studio 擴充功能開頭 VSIX 部署專案，以將包含延伸模組資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX 專案，名為`MyObjectPropertiesExtension`。 您可以找到 VSIX 專案範本，在**新專案**對話方塊底下**Visual C# / 擴充性**。  
  
2.  加入名為的自訂工具視窗項目範本加入工具視窗`MyToolWindow`。 在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在**加入新項目對話方塊**，請移至**Visual C# 項目 / 擴充性**選取**自訂工具視窗**。 在**名稱**在對話方塊底部欄位中，將檔案名稱變更為`MyToolWindow.cs`。 如需如何建立自訂的工具視窗的詳細資訊，請參閱[建立工具視窗擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
3.  開啟 MyToolWindow.cs 並加入下列 using 陳述式：  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  現在，加入下列欄位，以`MyToolWindow`類別。  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  將下列程式碼加入至 MyToolWindow 類別。  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection`屬性使用`GetService`取得`STrackSelection`服務，提供<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>介面。 `OnToolWindowCreated`事件處理常式和`SelectList`方法一起建立一份所選物件包含的工具視窗窗格物件本身。 `UpdateSelection`方法會告知**屬性**視窗，以顯示工具視窗窗格的公用屬性。  
  
6.  建置此專案並開始偵錯。 Visual Studio 的實驗執行個體應該會出現。  
  
7.  如果**屬性**看不到視窗中，按 F4 開啟它。  
  
8.  開啟**MyToolWindow**視窗。 您可以找到在**檢視 / 其他視窗**。  
  
     視窗隨即開啟，而且視窗窗格的公用屬性會出現在**屬性**視窗。  
  
9. 變更**標題**屬性**屬性**視窗**My 的物件屬性**。  
  
     MyToolWindow 視窗的標題會隨之變更。  
  
## <a name="exposing-tool-window-properties"></a>公開的工具視窗屬性  
 本節中，您可以加入工具視窗，並顯示其屬性。 您對內容的變更會反映在**屬性**視窗。  
  
#### <a name="to-expose-tool-window-properties"></a>若要公開 （expose） 工具視窗屬性  
  
1.  開啟 MyToolWindow.cs，然後新增公用的布林值屬性其 IsChecked MyToolWindow 類別。  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     這個屬性會取得其狀態從更新版本，您將建立的 WPF 核取方塊。  
  
2.  開啟 MyToolWindowControl.xaml.cs 和 MyToolWindowControl 建構函式取代成下列程式碼。  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     這可讓`MyToolWindowControl`存取`MyToolWindow`窗格。  
  
3.  在 MyToolWindow.cs，變更`MyToolWindow`建構函式，如下所示：  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  變更 MyToolWindowControl [設計] 檢視。  
  
5.  刪除的按鈕，並加入核取方塊，從**工具箱**至左上角。  
  
6.  新增已核取及取消核取事件。 在 [設計] 檢視中選取此核取方塊。 在**屬性**視窗中，按一下事件處理常式按鈕 (上方右側**屬性**視窗)。 尋找**已核取**和型別**checkbox_Checked**在文字方塊中，然後尋找**未核取**和型別**checkbox_Unchecked**在文字方塊中。  
  
7.  加入核取方塊事件處理常式：  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  建置此專案並開始偵錯。  
  
9. 在實驗執行個體中，開啟**MyToolWindow**視窗。  
  
     視窗的內容中尋找**屬性**視窗。 **IsChecked**屬性底下出現在視窗的底部**我內容**類別目錄。  
  
10. 簽入的核取方塊**MyToolWindow**視窗。 **其 IsChecked**中**屬性**視窗變更為**True**。 清除核取方塊，在**MyToolWindow**視窗。 **其 IsChecked**中**屬性**視窗變更為**False**。 值變更**IsChecked**中**屬性**視窗。 中的核取方塊**MyToolWindow**視窗會變更，以符合新值。  
  
    > [!NOTE]
    >  如果您必須處置的物件，會顯示在**屬性**視窗中，呼叫`OnSelectChange`與`null`選取容器第一次。 後正在處置的屬性或物件，您可以變更已更新的選取範圍容器<xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A>和<xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A>列出。  
  
## <a name="changing-selection-lists"></a>變更選取項目清單  
 在本節中，您可以加入選擇清單的基本屬性類別，並使用工具視窗介面選擇要顯示的選取項目清單。  
  
#### <a name="to-change-selection-lists"></a>若要變更選取項目清單  
  
1.  開啟 MyToolWindow.cs 並新增名為公用類別`Simple`。  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  將 SimpleObject 屬性加入 MyToolWindow 類別，再加上兩種方法可以切換**屬性**視窗選取視窗窗格之間和`Simple`物件。  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  在 MyToolWindowControl.cs，取代下列幾行的程式碼中的核取方塊處理常式：  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  建置此專案並開始偵錯。  
  
5.  在實驗執行個體中，開啟**MyToolWindow**視窗。  
  
6.  選取核取方塊，在**MyToolWindow**視窗。 **屬性**視窗會顯示`Simple`物件屬性， **SomeText**和**ReadOnly**。 清除核取方塊。 視窗的公用屬性會出現在**屬性**視窗。  
  
    > [!NOTE]
    >  顯示名稱**SomeText**是**我文字**。  
  
## <a name="best-practice"></a>最佳作法  
 在本逐步解說，<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>實作可選取的物件集合和所選的物件的集合是在相同的集合。 選取的物件會出現在屬性瀏覽器清單。 如需更完整的必須要有 ISelectionContainer 實作，請參閱 Reference.ToolWindow 範例。  
  
 Visual Studio 工具視窗將 Visual Studio 工作階段之間保存。 如需有關保存工具視窗狀態的詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。  
  
## <a name="see-also"></a>請參閱  
 [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)