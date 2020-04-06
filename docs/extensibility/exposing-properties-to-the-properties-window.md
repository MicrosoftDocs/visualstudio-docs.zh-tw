---
title: 向屬性視窗公開屬性 |微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f84962628ae550676e2c2eeb10c0f3baeca1bb58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711834"
---
# <a name="expose-properties-to-the-properties-window"></a>向「屬性」視窗公開屬性

本演練將物件的公共屬性公開到 **「屬性」** 視窗。 對這些屬性所做的更改將反映在 **「屬性」** 視窗中。

## <a name="prerequisites"></a>Prerequisites

從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="expose-properties-to-the-properties-window"></a>向「屬性」視窗公開屬性

在本節中,您將創建一個自定義工具視窗,並在 **「屬性」** 視窗中顯示關聯的視窗窗格物件的公共屬性。

### <a name="to-expose-properties-to-the-properties-window"></a>向「屬性」視窗公開屬性

1. 每個 Visual Studio 擴展都從 VSIX 部署專案開始,該專案將包含擴展資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]名為的`MyObjectPropertiesExtension`VSIX 專案。 您可以通過搜尋"vsix"在 **"新項目**"對話框中找到 VSIX 專案範本。

2. 通過添加名為`MyToolWindow`的自定義工具視窗項範本來添加工具視窗。 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 在 **「新增新項目」對話框**中,轉到**可視化 C# 項** > **擴充性**並選擇 **「自訂工具視窗**」。 在對話框底部的 **「 名稱」** 欄位中,將檔案名稱變更為*MyToolWindow.cs*。 有關如何建立自訂工具視窗的詳細資訊,請參閱[使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)。

3. 開啟*MyToolWindow.cs*並新增以下使用敘述:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. 現在向`MyToolWindow`類添加以下欄位。

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

    屬性`TrackSelection`用於`GetService`獲取提供`STrackSelection`<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>介面的服務。 事件`OnToolWindowCreated`處理程式和`SelectList`方法 共同建立僅包含工具視窗窗格物件本身的選定對象的清單。 該方法`UpdateSelection`告訴 **「屬性」** 視窗顯示工具視窗窗格的公共屬性。

6. 建置此專案並開始偵錯。 應出現視覺工作室的實驗實例。

7. 如果**屬性**視窗不可見,則通過按**F4**打開它。

8. 開啟 **「我的工具視窗」 視窗 。** 您可以在 **「查看** > **其他視窗**」 中找到它。

    視窗將打開,視窗窗格的公共屬性將顯示在**屬性「屬性」** 視窗中。

9. 將 **「屬性**」視窗中的**標題**屬性更改為 **「我的物件屬性**」 。

     "MyTool 視窗"視窗標題會相應地更改。

## <a name="expose-tool-window-properties"></a>公開工具視窗屬性

在本節中,添加工具視窗並公開其屬性。 對屬性所做的更改將反映在 **「屬性」** 視窗中。

### <a name="to-expose-tool-window-properties"></a>公開工具視窗屬性

1. 打開*MyToolWindow.cs*,並將公共布爾屬性"是檢查"添加`MyToolWindow`到類 中。

    ```csharp
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

     此屬性從稍後將創建的 WPF 複選框中獲取其狀態。

2. 打開*MyToolWindowControl.xaml.cs,* 並將 MyToolWindowControl 建構函數替換為以下代碼。

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     這允許`MyToolWindowControl``MyToolWindow`訪問 窗格。

3. 在*MyToolWindow.cs*`MyToolWindow`中, 更改建構函數如下所示:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. 更改為 MyToolWindowControl 的設計檢視。

5. 刪除該按鈕,並將複選框從 **「工具」框**添加到左上角。

6. 新增選中和未選中的事件。 選擇設計檢視中的複選框。 在「**屬性」** 視窗中,按一下事件處理程式按鈕(在 **「屬性」** 視窗的右上角)。 在文字框中尋找 **「已選中****」並鍵入checkbox_Checked,** 然後在文本框中尋找 **「未選中**」並鍵入**checkbox_Unchecked。**

7. 新增選取的盒事件處理程式:

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

9. 在實驗例中,開啟**MyTool 視窗**。

     在 **「屬性」** 視窗中尋找視窗的屬性。 **"IsChecked"** 屬性顯示在視窗底部,"**我的屬性**"類別下。

10. 選取**的 「MyTool 視窗」** 視窗中 的複選框。 **在****「屬性」** 視窗中選取的變更為**True**。 清除 **「MyTool 視窗」視窗中**的複選框。 **在****「屬性」** 視窗中選取的變更為**False**。 在 **「屬性」** 視窗中更改 **「 已檢查」** 的值。 **"MyToolWindow"視窗中**的複選框將更改以匹配新值。

    > [!NOTE]
    > 如果必須釋放「**屬性」** 視窗中顯示的物件,請`OnSelectChange``null`先使用 選擇容器進行調用。 處理屬性或物件後,可以更改為已更新<xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A><xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A>並 列出的選擇容器。

## <a name="change-selection-lists"></a>變更選取清單

 在本節中,您可以為基本屬性類添加選擇清單,並使用工具視窗介面選擇要顯示的選擇清單。

### <a name="to-change-selection-lists"></a>變更選取清單

1. 打開*MyToolWindow.cs*並添加名為`Simple`的公共 類。

    ```csharp
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

2. 新增屬性,以及兩個在`Simple`視窗窗格和 物件之間切換 **「屬性**」視窗選擇的方法。 `MyToolWindow``SimpleObject`

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

3. 在*MyToolWindowControl.cs*中,將複選框處理程式取代為以下代碼行:

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

5. 在實驗例中,開啟**MyTool 視窗**。

6. 在**MyTool 視窗視窗中**選擇複選框。 屬性**Properties**視窗`Simple`顯示 物件屬性「**某些文字**」和 **「唯讀」。** 清除複選框。 視窗的公共屬性將顯示在 **「屬性」** 視窗中。

    > [!NOTE]
    > **某些文字**的顯示名稱是 **「我的文字**」 。

## <a name="best-practice"></a>最佳做法

在本演練中,<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>實現可選擇的物件集合和所選物件集合是同一集合。 只有選取對象顯示在屬性瀏覽器清單中。 有關更完整的 I選擇容器實現,請參閱參考.ToolWindow 示例。

可視化工作室工具視窗在可視化工作室會話之間保留。 有關保留工具視窗狀態的詳細資訊,請參閱<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。

## <a name="see-also"></a>另請參閱

- [延伸屬性與屬性視窗](../extensibility/extending-properties-and-the-property-window.md)
