---
title: 演練:使用具有編輯器擴展的 Shell 命令 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52b151b09c1bb7306b4270f9408d0f04a7600aa2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697160"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>演練:使用具有編輯器延伸的 shell 命令
從 VSPackage 中,您可以將選單命令等功能添加到編輯器中。 本演練演示如何通過調用功能表命令向編輯器中的文本檢視添加修飾。

 本演練演示了 VSPackage 與託管擴充性框架 (MEF) 元件部件的使用。 您必須使用 VSPackage 將選單命令註冊到 Visual Studio 外殼。 而且,您可以使用該命令存取 MEF 元件元件。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-menu-command"></a>使用選單指令建立延伸
 建立 VSPackage,將名為「**新增修飾」** 的選單命令放在 **「工具」** 選單上。

1. 建立名為的`MenuCommandTest`C# VSIX 專案,並新增自訂指令項目樣本名稱**Addadornment**。 關於詳細資訊,請參閱[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

2. 將打開名為 MenuCommandTest 的解決方案。 MenuCommandTestPackage 檔案具有創建功能表命令並將其放在 **「工具」** 選單上的程式碼。 此時,該命令只是導致出現消息框。 後續步驟將演示如何更改此功能以顯示註釋修飾。

3. 開啟 VSIX 清單編輯器中的*來源.擴展.vsix清單*檔案。 該`Assets`選項卡應具有 Microsoft 的行。

4. 保存並關閉*源.擴展.vsixmanifest*檔案。

## <a name="add-a-mef-extension-to-the-command-extension"></a>新增指令延伸到新的 MEF 延伸

1. 在 **「解決方案資源管理器」** 中,右鍵單擊解決方案節點,按下「**添加**」,然後按下 **「新專案**」。 在「**新增新項目」** 對話框中,按**下 Visual C#** 下的 **「擴充性**」,然後按一下**VSIX 專案**。 將專案命名為 `CommentAdornmentTest`。

2. 由於此專案將與強命名的 VSPackage 程式集進行互動,因此必須對程式集進行簽名。 您可以重用為 VSPackage 程式集建立的金鑰檔。

    1. 開啟項目屬性並選擇「**簽署**」 選項卡。

    2. 選擇**此應用程式的簽章**。

    3. 在**選擇強名稱金鑰檔**下,選擇為 MenuCommandTest 程式集產生的*Key.snk*檔。

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>請參考 VSPackage 專案中的 MEF 擴充
 由於要向 VSPackage 添加 MEF 元件,因此必須在清單中指定這兩種資產。

> [!NOTE]
> 有關 MEF 的詳細資訊,請參閱[託管擴展性框架 (MEF)。](/dotnet/framework/mef/index)

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>在 VSPackage 專案中引用 MEF 元件

1. 在 MenuCommandTest 專案中,在 VSIX 清單編輯器中打開*來源.擴展.vsix清單*檔。

2. 在「**資產**」選項卡上,按下 **「新建**」。。

3. 在 **「類型」** 清單中,選擇**Microsoft.VisualStudio.Mef 元件**。

4. 在 **「來源」** 清單中,選擇**目前解決方案中的項目**。

5. 在**項目**清單中,選擇**註解認證測試**。

6. 保存並關閉*源.擴展.vsixmanifest*檔案。

7. 確保 MenuCommandTest 專案具有對註釋驗證測試專案的引用。

8. 在註釋註釋測試專案中,將專案設置為生成程式集。 在**解決方案資源管理員**中,選擇專案並在「**將產生輸出複製到輸出目錄**」**屬性**的屬性視窗中尋找,並將其設定為**true**。

## <a name="define-a-comment-adornment"></a>定義註解修飾
 註釋修飾本身由追蹤所選文本的<xref:Microsoft.VisualStudio.Text.ITrackingSpan>和一些表示作者和文本描述的字串組成。

#### <a name="to-define-a-comment-adornment"></a>定義註解修飾

1. 在註解驗證測試中,新增新的類別檔將命名為`CommentAdornment`。

2. 加入下列參考：

    1. 微軟.VisualStudio.核心實用程式

    2. 微軟.VisualStudio.文本.資料

    3. 微軟.VisualStudio.文本.邏輯

    4. 微軟.VisualStudio.文字.UI

    5. 微軟.VisualStudio.文本.UI.Wpf

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. 添加以下`using`指令。

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. 該檔應包含名為的`CommentAdornment`類。

    ```csharp
    internal class CommentAdornment
    ```

5. 將三個字段添加到`CommentAdornment`<xref:Microsoft.VisualStudio.Text.ITrackingSpan>的類 中,作者和說明。

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. 添加初始化欄位的構造函數。

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>為修飾建立視覺元素
 為修飾定義可視元素。 在本演練中,定義從 Windows 演示文稿基礎 (WPF) 類<xref:System.Windows.Controls.Canvas>繼承的控制項。

1. 在註解驗證測試中建立一個類別,並命名它`CommentBlock`。

2. 添加以下`using`指令。

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

3. 使`CommentBlock`類<xref:System.Windows.Controls.Canvas>從 繼承。

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. 添加一些私有欄位以定義修飾的視覺方面。

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. 添加定義註釋修飾並添加相關文本的構造函數。

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

6. 還實現繪製<xref:System.Windows.Controls.Panel.OnRender%2A>修飾的事件處理程式。

    ```csharp
    protected override void OnRender(DrawingContext dc)
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

## <a name="add-an-iwpftextviewcreationlistener"></a>新增 IWpftext 檢視建立偵聽器
 是<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>MEF 元件部分,可用於偵聽創建事件。

1. 將類別檔加入到註解修飾測試項目並將名命名為`Connector`。

2. 添加以下`using`指令。

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. 聲明實現<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>的類,並將其匯出為<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute><xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>和 a。 內容類型屬性指定元件應用於的內容類型。 文字類型是所有非二進位檔案類型的基礎類型。 因此,創建的幾乎每個文本檢視都將是此類型。 文字檢視角色屬性指定元件應用於的文本視圖類型。 文件文字檢視角色通常顯示由行組成並存儲在檔案中的文本。

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. 實現<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>該方法,以便調用`Create()``CommentAdornmentManager`的靜態事件。

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. 添加可用於執行命令的方法。

    ```csharp
    static public void Execute(IWpfTextViewHost host)
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

## <a name="define-an-adornment-layer"></a>定義修飾層次
 要添加新修飾,必須定義修飾圖層。

### <a name="to-define-an-adornment-layer"></a>定義修飾層次

1. 在`Connector`類中,聲明<xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>類型的公共欄位,並將其匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>為 指定修飾圖層的唯一名稱<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>,以及定義此修飾圖層的 Z 順序關係到其他文本檢視圖層(文本、綴和選擇) 的欄位。

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>提供註解修飾
 定義修飾時,還實現註釋修飾提供程式和註釋修飾管理器。 註釋修飾提供程式保留註釋修飾清單,偵聽<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>基礎文本緩衝區上的事件,並在刪除基礎文本時刪除註釋修飾。

1. 將新的類別檔加入到註解修飾測試項目並將名命名為`CommentAdornmentProvider`。

2. 添加以下`using`指令。

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

4. 為文本緩衝區添加私有欄位以及與緩衝區相關的註釋修飾清單。

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. 添加`CommentAdornmentProvider`的構造函數。 此構造函數應具有私有訪問許可權,因為提供程式由`Create()`方法實例化。 建構函數將`OnBufferChanged`事件處理程式到事件<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>。

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
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. 新增 `Detach()` 方法。

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. 添加事件`OnBufferChanged`處理程式。

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. 添加`CommentsChanged`事件的聲明。

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. 創建一`Add()`個方法來添加修飾。

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

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

11. 新增方法`RemoveComments()`。

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
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

12. 添加一`GetComments()`個方法,返回給定快照範圍內的所有註釋。

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. 添加名為`CommentsChangedEventArgs`的 類,如下所示。

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>管理註解修飾
 註釋修飾管理器創建修飾並將其添加到修飾層。 它偵聽<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged><xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>和 事件,以便可以移動或刪除修飾。 它還偵聽添加或刪除註釋`CommentsChanged`時註釋修飾提供程式觸發的事件。

1. 將類別檔加入到註解修飾測試項目並將名命名為`CommentAdornmentManager`。

2. 添加以下`using`指令。

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

4. 添加一些私有欄位。

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. 添加將管理器訂閱<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>到<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>和事件以及`CommentsChanged`事件的建構函數。 構造函數是私有的,因為管理器由靜態`Create()`方法實例化。

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

6. 添加獲取`Create()`提供程式的方法,或在必要時創建提供程式。

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. 添加`CommentsChanged`處理程式。

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. 添加<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>處理程式。

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. 添加<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>處理程式。

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
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

10. 添加繪製註釋的私有方法。

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>使用選單指令加入註解修飾
 您可以使用選單命令通過實現 VSPackage`MenuItemCallback`的方法來建立註釋修飾。

1. 新增選單指令測試項目的以下參考:

    - 微軟.VisualStudio.文字管理員.互通

    - 微軟.VisualStudio.編輯器

    - 微軟.VisualStudio.文本.UI.Wpf

2. 開啟*AddAdornment.cs*檔案並`using`新增以下 指令。

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. 移除`Execute()`方法並添加以下命令處理程式。

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. 添加代碼以獲取活動檢視。 您必須取得`SVsTextManager`視覺工作室外殼才能`IVsTextView`啟動 。

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. 如果此文字檢視是編輯器文字檢視的實體,則可以將其轉換為介面,<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>然後取得<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>與關聯的<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。 使用<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>調`Connector.Execute()`用 方法,該方法獲取註釋修飾提供程式並添加修飾。 命令處理程式現在應如下所示:

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

6. 將 AddAdornmentHandler 方法設置為 AddAdornment 建構函數中 AddAdornment 命令的處理程式。

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

## <a name="build-and-test-the-code"></a>組建及測試代碼

1. 建置方案並開始偵錯。 應出現實驗實例。

2. 建立文字檔 鍵入某些文本,然後選擇它。

3. 在 **「工具」** 選單上,按下 **「調用添加修飾**」 。 氣球應顯示在文本視窗的右側,並且應包含類似於以下文本的文本。

     您的使用者名稱

     四分...

## <a name="see-also"></a>另請參閱
- [演練:將內容類型連結到檔案名副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
