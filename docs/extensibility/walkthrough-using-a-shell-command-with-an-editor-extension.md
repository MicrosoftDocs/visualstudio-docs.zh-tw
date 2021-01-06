---
title: 搭配編輯器延伸模組使用 shell 命令
description: 瞭解如何藉由叫用功能表命令，在編輯器中將裝飾加入至文本視圖。 從 VSPackage，您可以將功能表命令之類的功能加入編輯器中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38d855ebe34c54d06159ecd958a8b1d31ae0131f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877815"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>逐步解說：搭配編輯器延伸模組使用 shell 命令
從 VSPackage，您可以將功能表命令之類的功能加入編輯器中。 本逐步解說示範如何藉由叫用功能表命令，在編輯器中將裝飾加入至文本視圖。

 本逐步解說將示範如何使用 VSPackage 搭配 Managed Extensibility Framework (MEF) 元件部分。 您必須使用 VSPackage 向 Visual Studio shell 註冊功能表命令。 而且，您可以使用命令來存取 MEF 元件部分。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-menu-command"></a>使用功能表命令建立擴充功能
 建立 VSPackage，將名為 [ **新增裝飾** ] 的功能表命令放在 [ **工具** ] 功能表上。

1. 建立名為的 c # VSIX 專案 `MenuCommandTest` ，然後新增自訂命令專案範本名稱 **AddAdornment**。 如需詳細資訊，請參閱 [使用功能表命令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)模組。

2. 名為 MenuCommandTest 的方案隨即開啟。 MenuCommandTestPackage 檔案具有可建立功能表命令的程式碼，並將它放在 [ **工具** ] 功能表上。 此時，命令只會顯示訊息方塊。 稍後的步驟將示範如何將此變更為顯示批註裝飾。

3. 在 VSIX 資訊清單編輯器中開啟 *extension.vsixmanifest* 檔案。 索引標籤 `Assets` 應該會有一個名為 MenuCommandTest 的 VisualStudio VsPackage 資料列。

4. 儲存並關閉 *extension.vsixmanifest* 檔案。

## <a name="add-a-mef-extension-to-the-command-extension"></a>將 MEF 延伸模組新增至命令延伸模組

1. 在 **方案總管** 中，以滑鼠右鍵按一下方案節點，然後按一下 [ **加入**]，再按一下 [ **新增專案**]。 在 [**加入新專案**] 對話方塊中，**按一下**[ **Visual c #**] 底下的 [擴充性]，然後按一下 [ **VSIX 專案** 將專案命名為 `CommentAdornmentTest`。

2. 因為這個專案會與強式名稱的 VSPackage 元件互動，所以您必須簽署元件。 您可以重複使用已針對 VSPackage 元件建立的金鑰檔。

    1. 開啟專案屬性，然後選取 [ **簽署** ] 索引標籤。

    2. 選取 **[簽署元件**]。

    3. 在 **[選擇強式名稱金鑰** 檔] 底下，選取針對 MenuCommandTest 元件所產生的 *金鑰 .snk* 檔案。

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>請參閱 VSPackage 專案中的 MEF 延伸模組
 由於您要將 MEF 元件新增至 VSPackage，因此您必須在資訊清單中同時指定這兩種資產。

> [!NOTE]
> 如需 MEF 的詳細資訊，請參閱 [Managed Extensibility Framework (mef) ](/dotnet/framework/mef/index)。

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>若要參考 VSPackage 專案中的 MEF 元件

1. 在 MenuCommandTest 專案中，在 VSIX 資訊清單編輯器中開啟 *extension.vsixmanifest* 檔案。

2. 在 [ **資產** ] 索引標籤上，按一下 [ **新增**]。

3. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio. [microsoft.visualstudio.mefcomponent]**]。

4. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

5. 在 [ **專案** ] 清單中，選擇 [ **CommentAdornmentTest**]。

6. 儲存並關閉 *extension.vsixmanifest* 檔案。

7. 請確定 MenuCommandTest 專案具有 CommentAdornmentTest 專案的參考。

8. 在 CommentAdornmentTest 專案中，設定專案以產生元件。 在 [**方案總管** 中，選取專案並查看 [**將組建輸出複製到 OutputDirectory** ] 屬性的 [**屬性**] 視窗，並將它設定為 [ **true**]。

## <a name="define-a-comment-adornment"></a>定義批註裝飾
 批註裝飾本身包含的 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 會追蹤選取的文字，以及表示作者和文字描述的一些字串。

#### <a name="to-define-a-comment-adornment"></a>若要定義批註裝飾

1. 在 CommentAdornmentTest 專案中，加入新的類別檔案，並將它命名為 `CommentAdornment` 。

2. 加入下列參考：

    1. VisualStudio. CoreUtility

    2. VisualStudio 資料

    3. VisualStudio。

    4. VisualStudio。

    5. VisualStudio （Wpf）

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. 新增下列指示詞 `using` 。

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. 檔案應包含名為的類別 `CommentAdornment` 。

    ```csharp
    internal class CommentAdornment
    ```

5. 將三個欄位加入至的 `CommentAdornment` 類別 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 、作者和描述。

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. 加入可初始化欄位的函式。

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>建立裝飾的視覺元素
 定義裝飾的視覺元素。 針對此逐步解說，請定義繼承自 Windows Presentation Foundation (WPF) 類別的控制項 <xref:System.Windows.Controls.Canvas> 。

1. 在 CommentAdornmentTest 專案中建立類別，並將它命名為 `CommentBlock` 。

2. 新增下列指示詞 `using` 。

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. 讓 `CommentBlock` 類別繼承自 <xref:System.Windows.Controls.Canvas> 。

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. 加入一些私用欄位，以定義裝飾的視覺效果層面。

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. 加入定義批註裝飾的函式，並加入相關文字。

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. 也可執行 <xref:System.Windows.Controls.Panel.OnRender%2A> 繪製裝飾的事件處理常式。

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>新增 IWpfTextViewCreationListener
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>是一種 MEF 元件部分，您可以用來接聽視圖建立事件。

1. 將類別檔案新增至 CommentAdornmentTest 專案，並將其命名為 `Connector` 。

2. 新增下列指示詞 `using` 。

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. 宣告可執行檔類別 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> ，並將其匯出為 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" 和 <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> 的 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 。 Content type 屬性會指定要套用元件的內容種類。 文字類型是所有非二進位檔案類型的基底類型。 因此，幾乎每個建立的文字視圖都屬於這種類型。 Text view role 屬性指定要套用元件的文字視圖種類。 Document text view role 通常會顯示由程式碼組成的文字，並儲存在檔案中。

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. 執行 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 方法，讓它呼叫的靜態 `Create()` 事件 `CommentAdornmentManager` 。

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. 新增可讓您用來執行命令的方法。

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>定義裝飾層
 若要加入新的裝飾，您必須定義裝飾層。

### <a name="to-define-an-adornment-layer"></a>若要定義裝飾層

1. 在 `Connector` 類別中，宣告類型的公用欄位 <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> ，並使用 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 指定裝飾層的唯一名稱的來匯出，以及將 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> 這個裝飾圖層的迭置順序關聯性定義為其他文字視圖圖層 (文字、插入號和選取範圍) 。

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>提供批註裝飾
 當您定義裝飾時，也會執行批註裝飾提供者和批註裝飾管理員。 批註裝飾提供者會保留批註裝飾清單、接聽 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 基礎文字緩衝區上的事件，並在刪除基礎文字時刪除批註裝飾。

1. 將新的類別檔案加入至 CommentAdornmentTest 專案，並將其命名為 `CommentAdornmentProvider` 。

2. 新增下列指示詞 `using` 。

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. 新增名為 `CommentAdornmentProvider`的類別。

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. 新增文字緩衝區的私用欄位，以及與緩衝區相關的批註裝飾清單。

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. 新增的函式 `CommentAdornmentProvider` 。 這個函式應該有私用存取，因為提供者是由方法具現化 `Create()` 。 此函數會將 `OnBufferChanged` 事件處理常式加入至 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 事件。

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. 新增 `Create()` 方法。

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. 新增 `Detach()` 方法。

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. 加入 `OnBufferChanged` 事件處理常式。

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. 加入事件的宣告 `CommentsChanged` 。

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. 建立 `Add()` 新增裝飾的方法。

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. 加入 `RemoveComments()` 方法。

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. 新增 `GetComments()` 方法，以傳回指定之快照集範圍中的所有批註。

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. 新增名為的類別 `CommentsChangedEventArgs` ，如下所示。

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>管理批註裝飾
 批註裝飾管理員會建立裝飾，並將其新增至裝飾層。 它會接聽 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 和 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> 事件，讓它可以移動或刪除裝飾。 `CommentsChanged`當加入或移除批註時，它也會接聽批註裝飾提供者所引發的事件。

1. 將類別檔案新增至 CommentAdornmentTest 專案，並將其命名為 `CommentAdornmentManager` 。

2. 新增下列指示詞 `using` 。

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. 新增名為 `CommentAdornmentManager`的類別。

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. 新增一些私用欄位。

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. 加入可訂閱管理員和事件的函式 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> ，以及事件的訂閱者 `CommentsChanged` 。 此函式是私用的，因為管理員是由靜態方法具現化 `Create()` 。

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. 新增 `Create()` 可取得提供者的方法，或在必要時建立一個提供者。

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. 加入 `CommentsChanged` 處理常式。

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. 加入 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> 處理常式。

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. 加入 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 處理常式。

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. 新增用來繪製批註的私用方法。

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>使用功能表命令來新增批註裝飾
 您可以使用功能表命令來建立批註裝飾，方法是執行 `MenuItemCallback` VSPackage 的方法。

1. 將下列參考加入至 MenuCommandTest 專案：

    - VisualStudio. TextManager. Interop

    - VisualStudio 編輯器

    - VisualStudio （Wpf）

2. 開啟 *AddAdornment.cs* 檔案，並新增下列指示詞 `using` 。

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. 刪除 `Execute()` 方法並加入下列命令處理常式。

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. 加入程式碼以取得使用中的視圖。 您必須取得 `SVsTextManager` Visual Studio shell 的來取得使用中的 `IVsTextView` 。

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. 如果此文字視圖是編輯器文字視圖的實例，您可以將它轉換成介面，然後 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> 取得 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 和其相關聯的 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> 。 使用 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 來呼叫 `Connector.Execute()` 方法，此方法會取得批註裝飾提供者並新增裝飾。 命令處理常式現在看起來應該像此程式碼：

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. 將 AddAdornmentHandler 方法設定為 AddAdornment 函式中 AddAdornment 命令的處理常式。

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>建立並測試程式碼

1. 建置方案並開始偵錯。 實驗實例應會出現。

2. 建立文字檔 輸入一些文字，然後選取它。

3. 按一下 [ **工具** ] 功能表上的 [叫用 **新增裝飾**]。 批註提示應該會顯示在文字視窗的右邊，而且應該包含類似下列文字的文字。

     」

     Fourscore...

## <a name="see-also"></a>請參閱
- [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
