---
title: 將屬性公開至屬性視窗 |Microsoft Docs
description: 深入瞭解物件的公用屬性。 您對這些屬性所做的變更會反映在屬性視窗中。
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9de86e956fe6a4d7841d519d7252b75ae216229
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075246"
---
# <a name="expose-properties-to-the-properties-window"></a>將屬性公開給屬性視窗

本逐步解說會將物件的公用屬性公開至 [ **屬性** ] 視窗。 您對這些屬性所做的變更會反映在 [ **屬性** ] 視窗中。

## <a name="prerequisites"></a>必要條件

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="expose-properties-to-the-properties-window"></a>將屬性公開給屬性視窗

在本節中，您會建立自訂工具視窗，並在 [ **屬性** ] 視窗中顯示相關聯的視窗窗格物件的公用屬性。

### <a name="to-expose-properties-to-the-properties-window"></a>將屬性公開給屬性視窗

1. 每個 Visual Studio 擴充功能都會從 VSIX 部署專案開始，其中包含延伸模組資產。 建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 名為的 VSIX 專案 `MyObjectPropertiesExtension` 。 您可以藉由搜尋 "vsix"，在 [ **新增專案** ] 對話方塊中找到 VSIX 專案範本。

2. 加入名為的自訂工具視窗專案範本，以新增工具視窗 `MyToolWindow` 。 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**加入新專案] 對話方塊** 中，移至 **Visual c # 專案** 擴充性  >   ，然後選取 [**自訂工具視窗]**。 在對話方塊底部的 [ **名稱** ] 欄位中，將檔案名變更為 *mytoolwindow] .cs*。 如需有關如何建立自訂工具視窗的詳細資訊，請參閱 [使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)模組。

3. 開啟 *mytoolwindow]* ，並新增下列 using 語句：

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. 現在將下欄欄位新增至 `MyToolWindow` 類別。

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. 將下列程式碼新增至 `MyToolWindow` 類別。

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

    `TrackSelection`屬性會使用 `GetService` 來取得 `STrackSelection` 服務，以提供 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 介面。 `OnToolWindowCreated`事件處理常式和 `SelectList` 方法會一起建立所選物件的清單，其中只包含工具視窗窗格物件本身。 `UpdateSelection`方法會告知 [**屬性**] 視窗顯示工具視窗窗格的公用屬性。

6. 建置此專案並開始偵錯。 應該會出現 Visual Studio 的實驗實例。

7. 如果看不到 [ **屬性** ] 視窗，請按 **F4** 開啟。

8. 開啟 **mytoolwindow]** 視窗。 您可以在 [**查看**  >  **其他視窗**] 中找到它。

    視窗隨即開啟，而且視窗窗格的公用屬性會出現在 [ **屬性** ] 視窗中。

9. 將 [**屬性**] 視窗中的 [**標題**] 屬性變更為 [**我的物件屬性**]。

     Mytoolwindow] 視窗標題會隨之變更。

## <a name="expose-tool-window-properties"></a>公開工具視窗屬性

在本節中，您會新增工具視窗並公開其屬性。 您對屬性所做的變更會反映在 [ **屬性** ] 視窗中。

### <a name="to-expose-tool-window-properties"></a>若要公開工具視窗屬性

1. 開啟 *mytoolwindow]*，並將公用布林值屬性 IsChecked 加入至 `MyToolWindow` 類別。

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

     這個屬性會從 WPF 核取方塊取得您稍後將建立的狀態。

2. 開啟 *MyToolWindowControl* ，並以下列程式碼取代 MyToolWindowControl 的函式。

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     這會提供 `MyToolWindowControl` 窗格的存取權 `MyToolWindow` 。

3. 在 *mytoolwindow]* 中，變更此函式，如下所示 `MyToolWindow` ：

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. 變更為 MyToolWindowControl 的設計檢視。

5. 刪除按鈕，並將核取方塊從 [ **工具箱** ] 新增至左上角。

6. 加入 Checked 和 Unchecked 事件。 選取設計檢視中的核取方塊。 在 [ **屬性** ] 視窗中，按一下 [ **屬性** ] 視窗) 右上方 (的 [事件處理常式] 按鈕。 在文字方塊中尋找 [ **已選取** ] 並輸入 **checkbox_Checked** ，然後在文字方塊中尋找 [ **未選取** ] 並輸入 **checkbox_Unchecked** 。

7. 新增核取方塊事件處理常式：

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

8. 建置此專案並開始偵錯。

9. 在實驗實例中，開啟 [ **mytoolwindow]** ] 視窗。

     在 [ **屬性** ] 視窗中尋找視窗的屬性。 [ **IsChecked** ] 屬性會出現在視窗底部的 [我的 **屬性** ] 類別之下。

10. 勾選 [ **mytoolwindow]** ] 視窗中的核取方塊。 [**屬性**] 視窗中的 [ **IsChecked** ] 變更為 [ **True**]。 清除 **mytoolwindow]** 視窗中的核取方塊。 [**屬性**] 視窗中的 [ **IsChecked** ] 變更為 [ **False**]。 在 [**屬性**] 視窗中變更 **IsChecked** 的值。 **Mytoolwindow]** 視窗中的核取方塊會變更以符合新的值。

    > [!NOTE]
    > 如果您必須處置 [ **屬性** ] 視窗中顯示的物件，請 `OnSelectChange` `null` 先使用選取容器來呼叫。 處置屬性或物件之後，您可以變更為已更新和清單的選取容器 <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> 。

## <a name="change-selection-lists"></a>變更選取清單

 在本節中，您會加入基本屬性類別的挑選清單，並使用工具視窗介面選擇要顯示的挑選清單。

### <a name="to-change-selection-lists"></a>變更選取清單

1. 開啟 *mytoolwindow]* ，並新增名為的公用類別 `Simple` 。

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

2. 將 `SimpleObject` 屬性新增至 `MyToolWindow` 類別，再加上兩個方法來切換視窗窗格和物件之間的 **屬性** 視窗選取範圍 `Simple` 。

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

3. 在 *MyToolWindowControl* 中，以下列程式程式碼取代核取方塊處理常式：

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

4. 建置此專案並開始偵錯。

5. 在實驗實例中，開啟 [ **mytoolwindow]** ] 視窗。

6. 在 [ **mytoolwindow]** ] 視窗中，選取核取方塊。 [ **屬性** ] 視窗會顯示 `Simple` 物件屬性： **SomeText** 和 **ReadOnly**。 清除核取方塊。 視窗的公用屬性會出現在 [ **屬性** ] 視窗中。

    > [!NOTE]
    > [ **SomeText** ] 的顯示名稱是 [ **我的文字**]。

## <a name="best-practice"></a>最佳做法

在這個逐步解說中， <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 會執行，讓可選取的物件集合和選取的物件集合都是相同集合。 只有選取的物件才會出現在屬性瀏覽器清單中。 如需更完整的 ISelectionContainer 執行，請參閱工具視窗範例。

Visual Studio 工具視窗會在 Visual Studio 會話之間保存。 如需保存工具視窗狀態的詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 。

## <a name="see-also"></a>另請參閱

- [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)
