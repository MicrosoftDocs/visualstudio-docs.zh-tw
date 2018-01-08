---
title: "逐步解說： 使用編輯器延伸模組中的 Shell 命令 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
caps.latest.revision: "46"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5a7f9426297ef28bdf4b829bd6697543f5aab55f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-using-a-shell-command-with-an-editor-extension"></a>逐步解說： 使用 Shell 命令的編輯器延伸模組
VSPackage，您可以加入至編輯器功能，例如功能表命令。 本逐步解說示範如何將裝飾文字在編輯器中檢視，藉由叫用功能表命令。  
  
 本逐步解說示範如何使用 Managed Extensibility Framework (MEF) 元件組件連同 VSPackage。 您必須使用 VSPackage 註冊功能表命令與 Visual Studio shell 之上，而且您可以使用命令來存取 MEF 元件組件。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-an-extension-with-a-menu-command"></a>建立擴充的功能表命令  
 建立 VSPackage，放入名為功能表命令**加入裝飾**上**工具**功能表。  
  
1.  C# VSIX 專案建立一個名為`MenuCommandTest`，並新增自訂命令項目範本名稱**AddAdornment**。 如需詳細資訊，請參閱[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  名為 MenuCommandTest 方案開啟。 MenuCommandTestPackage 檔案已建立功能表命令，並將它放在程式碼**工具**功能表。 此時，命令只會導致顯示訊息方塊。 接下來的步驟示範如何將這變更為顯示註解裝飾。  
  
3.  在 VSIX 資訊清單編輯器中，開啟 source.extension.vsixmanifest 檔案。 `Assets` Microsoft.VisualStudio.VsPackage 為 MenuCommandTest 索引標籤應該有一個資料列。  
  
4.  儲存並關閉 Source.extension.vsixmanifest 檔案。  
  
## <a name="adding-a-mef-extension-to-the-command-extension"></a>MEF 擴充功能加入命令擴充功能  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下方案節點，按一下**新增**，然後按一下 [**新專案**。 在**加入新的專案**對話方塊中，按一下 **擴充性**下**Visual C#**，然後**VSIX 專案**。 將專案命名為 `CommentAdornmentTest`。  
  
2.  因為這個專案與強式名稱 VSPackage 組件互動，您必須簽署組件。 您可以重複使用已建立 VSPackage 組件金鑰檔案。  
  
    1.  開啟專案屬性，並選取**簽署** 索引標籤。  
  
    2.  選取**簽署組件**。  
  
    3.  在下**選擇強式名稱金鑰檔**，選取 MenuCommandTest 組件所產生的 Key.snk 檔案。  
  
## <a name="referring-to-the-mef-extension-in-the-vspackage-project"></a>MEF 中的擴充功能的 VSPackage 專案參考  
 由於您要將為 MEF 元件加入 VSPackage，您必須指定這兩種資產資訊清單中。  
  
> [!NOTE]
>  如需 MEF 的詳細資訊，請參閱[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)。  
  
#### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>指將 VSPackage 專案 MEF 元件  
  
1.  在 MenuCommandTest 專案中，開啟 source.extension.vsixmanifest 檔案中，在 VSIX 資訊清單編輯器中。  
  
2.  在**資產**索引標籤上，按一下 **新增**。  
  
3.  在**類型**清單中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
4.  在**來源**清單中，選擇**目前方案中的專案**。  
  
5.  在**專案**清單中，選擇**CommentAdornmentTest**。  
  
6.  儲存並關閉 source.extension.vsixmanifest 檔案。  
  
7.  請確定 MenuCommandTest 專案具有 CommentAdornmentTest 專案的參考。  
  
8.  在 CommentAdornmentTest 專案中，設定要產生的組件的專案。 在**方案總管 中**、 選取的專案，然後查看**屬性**視窗**複製組建輸出至 OutputDirectory**屬性，並將它設定為**true**。  
  
## <a name="defining-a-comment-adornment"></a>定義註解裝飾  
 註解裝飾本身組成<xref:Microsoft.VisualStudio.Text.ITrackingSpan>，追蹤選取的文字，以及代表作者和描述的文字部分字串。  
  
#### <a name="to-define-a-comment-adornment"></a>若要定義註解裝飾  
  
1.  在 CommentAdornmentTest 專案中，加入新的類別檔案並將其命名`CommentAdornment`。  
  
2.  加入下列參考：  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  PresentationCore  
  
    8.  PresentationFramework  
  
    9. WindowsBase  
  
3.  加入下列`using`陳述式。  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  此檔案應該包含類別，名為`CommentAdornment`。  
  
    ```  
    internal class CommentAdornment  
    ```  
  
5.  將三個欄位加入`CommentAdornment`類別<xref:Microsoft.VisualStudio.Text.ITrackingSpan>、 作者和描述。  
  
    ```csharp  
    public readonly ITrackingSpan Span;  
    public readonly string Author;  
    public readonly string Text;  
    ```  
  
6.  加入的欄位初始化的建構函式。  
  
    ```csharp  
    public CommentAdornment(SnapshotSpan span, string author, string text)  
    {  
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);  
        this.Author = author;  
        this.Text = text;  
    }  
    ```  
  
## <a name="creating-a-visual-element-for-the-adornment"></a>建立裝飾的視覺項目  
 您也必須定義您裝飾視覺項目。 這個逐步解說中，定義繼承自 Windows Presentation Foundation (WPF) 類別的控制項<xref:System.Windows.Controls.Canvas>。  
  
1.  在 CommentAdornmentTest 專案中，建立類別並將其命名`CommentBlock`。  
  
2.  加入下列 `using` 陳述式。  
  
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
  
3.  請`CommentBlock`類別繼承自<xref:System.Windows.Controls.Canvas>。  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  加入一些私用欄位來定義裝飾的視覺外觀。  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5.  新增的建構函式定義註解裝飾，並將相關的文字。  
  
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
  
6.  也會實作<xref:System.Windows.Controls.Panel.OnRender%2A>繪製裝飾的事件處理常式。  
  
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
  
## <a name="adding-an-iwpftextviewcreationlistener"></a>加入 IWpfTextViewCreationListener  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>是 MEF 元件組件可讓您聆聽檢視建立事件。  
  
1.  將類別檔案加入至 CommentAdornmentTest 專案並將其命名`Connector`。  
  
2.  加入下列 `using` 陳述式。  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  宣告類別可實作<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的 「 文字 」 和<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>的<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>。 內容類型屬性指定元件所套用的內容的類型。 文字類型是所有非二進位檔案類型的基底類型。 因此，幾乎每個建立的文字檢視都屬於此類型。 文字檢視角色屬性會指定一種元件適用於文字檢視。 文件文字檢視角色通常會顯示線條所組成，且儲存在檔案中的文字。  
  
     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  實作<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法，使它呼叫靜態`Create()`事件`CommentAdornmentManager`。  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  加入可讓您執行命令的方法。  
  
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
  
## <a name="defining-an-adornment-layer"></a>定義裝飾圖層  
 若要加入新的裝飾，您必須定義裝飾圖層。  
  
#### <a name="to-define-an-adornment-layer"></a>若要定義裝飾圖層  
  
1.  在`Connector`類別，宣告類型的公用欄位<xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>指定裝飾圖層的唯一名稱和<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>，其他文字定義此裝飾圖層的疊置順序關聯性檢視層級 （文字、 插入號和選取範圍）。  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="providing-comment-adornments"></a>提供註解裝飾  
 當您定義裝飾時，也實作註解裝飾提供者和註解裝飾管理員。 註解裝飾提供者會保留一份註解裝飾時，接聽<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>基礎文字緩衝區，並刪除註解裝飾時將會刪除基礎文字上的事件。  
  
1.  將新的類別檔案加入至 CommentAdornmentTest 專案並將其命名`CommentAdornmentProvider`。  
  
2.  加入下列 `using` 陳述式。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  將類別命名為`CommentAdornmentProvider`。  
  
    ```csharp  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  加入私用欄位的文字緩衝和緩衝區相關的註解裝飾的清單。  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  新增的建構函式`CommentAdornmentProvider`。 這個建構函式應該有私用存取，因為提供者已具現化`Create()`方法。 建構函式加入`OnBufferChanged`事件處理常式來<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。  
  
    ```csharp  
    private CommentAdornmentProvider(ITextBuffer buffer)  
    {  
        this.buffer = buffer;  
        //listen to the Changed event so we can react to deletions.   
        this.buffer.Changed += OnBufferChanged;  
    }  
  
    ```  
  
6.  加入 `Create()` 方法。  
  
    ```csharp  
    public static CommentAdornmentProvider Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });  
    }  
  
    ```  
  
7.  加入 `Detach()` 方法。  
  
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
  
8.  新增`OnBufferChanged`事件處理常式。  
  
    ```csharp  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            Span span = comment.Span.GetSpan(e.After);  
            //if a comment does not span at least one character, its text was deleted.   
            if (span.Length != 0)  
            {  
                keptComments.Add(comment);  
            }  
        }  
  
        this.comments = keptComments;  
    }  
  
    ```  
  
     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]  
  
9. 加入宣告`CommentsChanged`事件。  
  
    ```csharp  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. 建立`Add()`將裝飾的方法。  
  
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
  
11. 新增`RemoveComments()`方法。  
  
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
  
12. 新增`GetComments()`方法會傳回在給定之快照集的範圍中所有註解。  
  
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
  
13. 將類別命名為`CommentsChangedEventArgs`、，如下所示。  
  
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
  
## <a name="managing-comment-adornments"></a>管理註解裝飾  
 註解裝飾管理員建立裝飾，並將它加入至裝飾圖層。 接聽項接聽<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>和<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>事件，讓它可以移動或刪除的裝飾。 它也會接聽`CommentsChanged`註解會新增或移除時，會將註解裝飾提供者所引發的事件。  
  
1.  將類別檔案加入至 CommentAdornmentTest 專案並將其命名`CommentAdornmentManager`。  
  
2.  加入下列 `using` 陳述式。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  將類別命名為`CommentAdornmentManager`。  
  
    ```csharp  
    internal class CommentAdornmentManager  
        {  
        }  
    ```  
  
4.  加入一些私用欄位。  
  
    ```csharp  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5.  新增的建構函式，以訂閱要經理<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>和<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>事件，並且透過`CommentsChanged`事件。 建構函式是私用，因為管理員具現化，由靜態`Create()`方法。  
  
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
  
6.  新增`Create()`方法，可取得提供者，或視需要建立一個。  
  
    ```csharp  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7.  新增`CommentsChanged`處理常式。  
  
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
  
8.  新增<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>處理常式。  
  
    ```csharp  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. 新增<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>處理常式。  
  
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
  
10. 加入私用的方法，繪製註解。  
  
     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]  
  
## <a name="using-the-menu-command-to-add-the-comment-adornment"></a>使用功能表命令加入註解裝飾  
 您可以使用功能表命令以建立註解裝飾藉由實作`MenuItemCallback`方法的 VSPackage。  
  
1.  加入下列參考加入 MenuCommandTest 專案：  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  開啟 AddAdornment.cs 檔案並加入下列`using`陳述式。  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  刪除 ShowMessageBox() 方法並加入下列的命令處理常式。  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  加入程式碼，以取得使用中的檢視。 您必須取得`SVsTextManager`取得作用中的 Visual Studio shell 的`IVsTextView`。  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  如果此文字 檢視編輯器的文字 檢視的執行個體，您可以將它轉換到<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>介面，然後取得<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>及其相關聯<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。 使用<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>呼叫`Connector.Execute()`其取得註解裝飾提供者，並新增裝飾的方法。 命令處理常式現在看起來應該像這樣：  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
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
  
6.  設定 AddAdornmentHandler 方法為 AddAdornment 命令 AddAdornment 建構函式中的處理常式。  
  
    ```csharp  
    private AddAdornment(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.AddAdornmentHandler;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
  
1.  建置方案並開始偵錯。 實驗執行個體應該會出現。  
  
2.  建立文字檔 輸入一些文字，然後選取它。  
  
3.  在**工具**功能表上，按一下 **叫用加入裝飾**。 氣球應該顯示文字視窗中，右邊，而且應該包含類似下列文字的文字。  
  
     您的使用者名稱  
  
     Fourscore...  
  
## <a name="see-also"></a>請參閱  
 [逐步解說︰將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)