---
title: "公開屬性至屬性視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "屬性瀏覽器中公開的屬性 [Visual Studio SDK]，"
  - "屬性 [Visual Studio SDK]"
  - "屬性瀏覽器中，公開屬性"
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# 公開屬性至屬性視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本逐步解說會公開公用屬性的物件 **屬性** 視窗。 您對這些屬性的變更會反映在 **屬性** 視窗。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 公開屬性至屬性視窗  
 本節中，建立自訂工具視窗和相關聯的視窗窗格中物件的公用屬性顯示 **屬性** 視窗。  
  
#### 公開屬性 \[屬性\] 視窗  
  
1.  每個 Visual Studio 擴充功能開始 VSIX 部署專案，以將包含擴充資產。 建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX 專案，名為 `MyObjectPropertiesExtension`。 您可以找到 VSIX 專案範本，在 **新的專案** 下的對話方塊 **Visual C\# \/ 擴充性**。  
  
2.  新增名為的自訂工具視窗項目範本以新增工具視窗 `MyToolWindow`。 在 **方案總管\] 中**, ，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**。 在 **加入新項目\] 對話方塊**, ，請移至 **Visual C\# 項目 \/ 擴充性** ，然後選取 **自訂工具視窗**。 在 **名稱** 欄位底部的 \[\] 對話方塊中，變更的檔案名稱 `MyToolWindow.cs`。 如需如何建立自訂工具視窗的詳細資訊，請參閱 [建立擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
3.  開啟 MyToolWindow.cs，並新增下列 using 陳述式:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  現在加入下列欄位，以 `MyToolWindow` 類別。  
  
    ```c#  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  將下列程式碼加入至 MyToolWindow 類別。  
  
    ```c#  
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
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection` 屬性使用 `GetService` 取得 `STrackSelection` 服務，提供 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 介面。`OnToolWindowCreated` 事件處理常式和 `SelectList` 方法一起建立一份所選物件，其中包含只會將工具視窗窗格物件本身。`UpdateSelection` 方法會告訴 **屬性** 視窗可以顯示工具\] 視窗窗格中的公用屬性。  
  
6.  建置此專案並開始偵錯。 Visual Studio 的實驗執行個體應該會出現。  
  
7.  如果 **屬性** 看不到視窗中，按 F4 開啟它。  
  
8.  開啟 **MyToolWindow** 視窗。 您可以找到它在 **檢視 \/ 其他視窗**。  
  
     視窗隨即開啟，並在窗格的公用屬性會出現在 **屬性** 視窗。  
  
9. 變更 **標題** 屬性 **屬性** 視窗 **我的物件內容**。  
  
     MyToolWindow 視窗標題會隨之改變。  
  
## 公開工具視窗屬性  
 本節中，將工具視窗，並顯示其屬性。 您對內容的變更會反映在 **屬性** 視窗。  
  
#### 若要公開 \(expose\) 工具視窗屬性  
  
1.  開啟 MyToolWindow.cs，並新增公用的布林值屬性 IsChecked MyToolWindow 類別。  
  
    ```c#  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     這個屬性會取得其狀態從 WPF 核取方塊，您將在稍後建立。  
  
2.  開啟 MyToolWindowControl.xaml.cs，並以下列程式碼取代 MyToolWindowControl 建構函式。  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     這可讓 `MyToolWindowControl` 存取 `MyToolWindow` 窗格。  
  
3.  在 MyToolWindow.cs，變更 `MyToolWindow` 建構函式，如下所示:  
  
    ```c#  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  將變更為 MyToolWindowControl 的設計檢視。  
  
5.  \[刪除\] 按鈕，並新增一個核取方塊，從 **工具箱** 至左上角。  
  
6.  加入核取和未核取的事件。 在 \[設計\] 檢視中選取此核取方塊。 在 **屬性** \] 視窗中，按一下事件處理常式按鈕 \(上方方 **屬性** 視窗\)。 尋找 **Checked** 和型別 **checkbox\_Checked** 在文字方塊中，然後尋找 **未核取** 和型別 **checkbox\_Unchecked** 在文字方塊中。  
  
7.  加入核取方塊事件處理常式:  
  
    ```c#  
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
  
9. 在實驗執行個體中，開啟 **MyToolWindow** 視窗。  
  
     視窗的內容中尋找 **屬性** 視窗。**IsChecked** 屬性底下出現在視窗的底部 **我內容** 類別。  
  
10. 簽入\] 核取方塊 **MyToolWindow** 視窗。**IsChecked** 中 **屬性** 視窗變更為 **True**。 清除核取方塊，在 **MyToolWindow** 視窗。**IsChecked** 中 **屬性** 視窗變更為 **False**。 值變更 **IsChecked** 中 **屬性** 視窗。 在核取方塊 **MyToolWindow** \] 視窗中變更，以符合新值。  
  
    > [!NOTE]
    >  如果您必須處置的物件，會顯示在 **屬性** \] 視窗中，呼叫 `OnSelectChange` 與 `null` 選取容器第一次。 之後處置物件的屬性，您可以變更為已更新的選取項目容器 <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> 和 <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> 列出。  
  
## 變更選取項目清單  
 本節中，您會加入基本屬性類別選取項目清單，與使用工具視窗介面來選擇要顯示的選取項目清單。  
  
#### 若要變更選取項目清單  
  
1.  開啟 MyToolWindow.cs，並新增名為公用類別 `Simple`。  
  
    ```c#  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
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
  
2.  將 SimpleObject 屬性加入至 MyToolWindow 類別，再加上兩種方法可以切換 **屬性** 視窗選取視窗窗格之間和 `Simple` 物件。  
  
    ```c#  
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
  
3.  在 MyToolWindowControl.cs，取代這行程式碼中的核取方塊處理常式:  
  
    ```c#  
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
  
5.  在實驗執行個體中，開啟 **MyToolWindow** 視窗。  
  
6.  選取核取方塊，在 **MyToolWindow** 視窗。**屬性** \] 視窗會顯示 `Simple` 物件屬性， **SomeText** 和 **ReadOnly**。 清除核取方塊。 視窗的公用屬性會出現在 **屬性** 視窗。  
  
    > [!NOTE]
    >  顯示名稱 **SomeText** 是 **我文字**。  
  
## 最佳作法  
 在本逐步解說， <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 實作，這樣可選取的物件集合和所選的物件的集合都是相同的集合。 選取的物件會出現在屬性瀏覽器清單。 如需更完整的 ISelectionContainer 方式，請參閱 Reference.ToolWindow 範例。  
  
 Visual Studio 工作階段之間保留 visual Studio 工具視窗。 如需保存的工具視窗狀態的詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。  
  
## 請參閱  
 [擴充屬性和 \[屬性\] 視窗](../Topic/Extending%20Properties%20and%20the%20Property%20Window.md)