---
title: 逐步解說： 搭配編輯器擴充功能使用 Shell 命令 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 02ff8a2be0d13af193a204ee6711bf7dfa11dee7
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566956"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>逐步解說： 搭配編輯器擴充功能使用 shell 命令
從 VSPackage，您可以將功能，例如功能表命令新增至編輯器。 本逐步解說示範如何加入在編輯器中文字檢視中的裝飾，藉由叫用功能表命令。  
  
 本逐步解說示範如何使用 Managed Extensibility Framework (MEF) 元件組件連同 VSPackage。 您必須使用 VSPackage 來向 Visual Studio shell 中的功能表命令。 您可以使用命令來存取 MEF 元件組件。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從下載中心取得。 它包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="create-an-extension-with-a-menu-command"></a>建立具有功能表命令的擴充功能  
 建立將名為的功能表命令的 VSPackage**新增 Adornment**上**工具**功能表。  
  
1.  建立名為 C# VSIX 專案`MenuCommandTest`，並新增自訂命令項目範本名稱**AddAdornment**。 如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的延伸模組](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  名為 MenuCommandTest 方案就會開啟。 MenuCommandTestPackage 檔案具有可建立功能表命令，並將它放在程式碼**工具**功能表。 到目前為止，此命令只會導致出現訊息方塊。 接下來的步驟將示範如何變更為顯示註解裝飾。  
  
3.  開啟*source.extension.vsixmanifest* VSIX 資訊清單編輯器 中的檔案。 `Assets` Microsoft.VisualStudio.VsPackage 命名 MenuCommandTest 索引標籤上應該有一個資料列。  
  
4.  儲存並關閉*source.extension.vsixmanifest*檔案。  
  
## <a name="add-a-mef-extension-to-the-command-extension"></a>加入命令擴充功能的 MEF 擴充功能  
  
1.  中**方案總管**，以滑鼠右鍵按一下方案節點，按一下**新增**，然後按一下 **新專案**。 在 [**加入新的專案**] 對話方塊中，按一下**擴充性**下**Visual C#**，然後**VSIX 專案**。 將專案命名為 `CommentAdornmentTest`。  
  
2.  因為這個專案與強式名稱 VSPackage 組件會互動，您必須簽署組件。 您可以重複使用已建立 VSPackage 組件金鑰檔案。  
  
    1.  開啟專案屬性，然後選取**簽署** 索引標籤。  
  
    2.  選取 **簽署組件**。  
  
    3.  底下**選擇強式名稱金鑰檔**，選取*Key.snk* MenuCommandTest 組件所產生的檔案。  
  
## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>MEF 中的延伸模組 VSPackage 專案，請參閱  
 因為您要新增為 MEF 元件的 vspackage，您必須指定這兩種類型的資產資訊清單中。  
  
> [!NOTE]
>  如需 MEF 的詳細資訊，請參閱[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)。  
  
### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>VSPackage 專案中的 MEF 元件參考  
  
1.  在 MenuCommandTest 專案中，開啟*source.extension.vsixmanifest* VSIX 資訊清單編輯器 中的檔案。  
  
2.  在 **資產**索引標籤上，按一下**新增**。  
  
3.  在 **型別**清單中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
4.  在 **來源**清單中，選擇**目前方案中的專案**。  
  
5.  在 **專案**清單中，選擇**CommentAdornmentTest**。  
  
6.  儲存並關閉*source.extension.vsixmanifest*檔案。  
  
7.  請確定 MenuCommandTest 專案具有 CommentAdornmentTest 專案的參考。  
  
8.  在 CommentAdornmentTest 專案中，設定要產生的組件的專案。 在**方案總管**、 選取的專案，然後查看**屬性**視窗**複製組建輸出到 OutputDirectory**屬性，並將它設定為 **，則為 true**。  
  
## <a name="define-a-comment-adornment"></a>定義註解 adornment  
 註解 adornment 本身組成<xref:Microsoft.VisualStudio.Text.ITrackingSpan>，追蹤選取的文字，以及一些字串，代表作者和描述的文字。  
  
#### <a name="to-define-a-comment-adornment"></a>若要定義註解 adornment  
  
1.  在 CommentAdornmentTest 專案中，加入新的類別檔案並將它命名`CommentAdornment`。  
  
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
  
3.  新增下列`using`陳述式。  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  此檔案應包含類別，名為`CommentAdornment`。  
  
    ```csharp  
    internal class CommentAdornment  
    ```  
  
5.  新增三個欄位，來`CommentAdornment`類別的<xref:Microsoft.VisualStudio.Text.ITrackingSpan>，作者和描述。  
  
    ```csharp  
    public readonly ITrackingSpan Span;  
    public readonly string Author;  
    public readonly string Text;  
    ```  
  
6.  新增初始化欄位的建構函式。  
  
    ```csharp  
    public CommentAdornment(SnapshotSpan span, string author, string text)  
    {  
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);  
        this.Author = author;  
        this.Text = text;  
    }  
    ```  
  
## <a name="create-a-visual-element-for-the-adornment"></a>建立裝飾視覺項目  
 定義您裝飾視覺項目。 此逐步解說中，定義繼承自 Windows Presentation Foundation (WPF) 類別的控制項<xref:System.Windows.Controls.Canvas>。  
  
1.  在 CommentAdornmentTest 專案中，建立類別並將它命名`CommentBlock`。  
  
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
  
3.  製作`CommentBlock`類別繼承自<xref:System.Windows.Controls.Canvas>。  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  加入一些私用欄位來定義裝飾的視覺效果。  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5.  新增的建構函式定義註解 adornment 並加入相關的文字。  
  
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
  
## <a name="add-an-iwpftextviewcreationlistener"></a>新增 IWpfTextViewCreationListener  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>所聆聽檢視建立事件時，您可以使用的 MEF 元件組件。  
  
1.  將類別檔案加入 CommentAdornmentTest 專案並將它命名`Connector`。  
  
2.  加入下列 `using` 陳述式。  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  宣告類別可實作<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>為"text"，<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>的<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>。 內容類型屬性會指定要套用之元件的內容類型。 文字類型是所有非二進位檔案類型的基底類型。 因此，幾乎每個建立的文字檢視將是這個型別。 文字檢視角色屬性會指定要套用之元件的 [文字] 檢視的類型。 文件文字檢視角色通常會顯示為線條所組成，而且會儲存在檔案的文字。  
  
     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  實作<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法，因此它會呼叫靜態`Create()`事件的`CommentAdornmentManager`。  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  加入的方法，您可以使用來執行命令。  
  
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
  
## <a name="define-an-adornment-layer"></a>定義裝飾圖層  
 若要加入新的裝飾，您必須定義 adornment 層。  
  
### <a name="to-define-an-adornment-layer"></a>若要定義的裝飾一層  
  
1.  在`Connector`類別中，宣告型別的公用欄位<xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>，指定唯一的名稱裝飾層和<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>其他文字定義此 adornment 圖層的疊置順序關聯性檢視層級 （文字、 插入號和選取項目）。  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="provide-comment-adornments"></a>提供註解裝飾  
 當您定義透過裝飾時，也實作註解 adornment 提供者和註解 adornment 管理員。 註解 adornment 提供者會保留一份註解裝飾、 聆聽<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>基礎的文字緩衝區，並刪除基礎的文字時，刪除註解該行上的事件。  
  
1.  將新的類別檔案加入至 CommentAdornmentTest 專案並將它命名`CommentAdornmentProvider`。  
  
2.  加入下列 `using` 陳述式。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  新增類別，名為`CommentAdornmentProvider`。  
  
    ```csharp  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  加入私用欄位的文字緩衝區和緩衝區相關的註解裝飾的清單。  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  新增的建構函式`CommentAdornmentProvider`。 這個建構函式應該具有私人存取，因為提供者具現化`Create()`方法。 建構函式加入`OnBufferChanged`事件處理常式來<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。  
  
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
  
12. 新增`GetComments()`方法會傳回在指定的快照集的範圍中的所有註解。  
  
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
  
13. 新增類別，名為`CommentsChangedEventArgs`、，如下所示。  
  
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
  
## <a name="manage-comment-adornments"></a>管理註解裝飾  
 註解 adornment manager 建立裝飾，並將它新增至 adornment 層。 聆聽<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>和<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>事件，讓它可以移動或刪除的裝飾。 它也會接聽`CommentsChanged`新增或移除註解時，會將註解 adornment 提供者所引發的事件。  
  
1.  將類別檔案加入 CommentAdornmentTest 專案並將它命名`CommentAdornmentManager`。  
  
2.  加入下列 `using` 陳述式。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  新增類別，名為`CommentAdornmentManager`。  
  
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
  
5.  加入訂閱的管理員的建構函式<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>並<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>事件，並且透過`CommentsChanged`事件。 建構函式是私用，因為 「 管理員 」 會具現化由靜態`Create()`方法。  
  
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
  
6.  新增`Create()`方法，可取得提供者，或若有需要，請建立一個。  
  
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
  
10. 加入私用方法繪製註解。  
  
     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]  
  
## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>使用功能表命令來新增註解 adornment  
 您可以使用功能表命令來建立註解 adornment 實作`MenuItemCallback`VSPackage 的方法。  
  
1.  將下列參考加入 MenuCommandTest 專案：  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  開啟*AddAdornment.cs*檔案，並新增下列`using`陳述式。  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  刪除`ShowMessageBox()`方法並加入下列的命令處理常式。  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  加入程式碼，以取得使用中的檢視。 您必須取得`SVsTextManager`以取得使用中的 Visual Studio shell 的`IVsTextView`。  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  如果此文字檢視是編輯器文字檢視的執行個體，您可以將它轉換成<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>介面，然後取得<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>及其相關聯<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。 使用<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>呼叫`Connector.Execute()`方法，其取得註解 adornment 提供者，並新增裝飾。 命令處理常式現在看起來應該類似以下程式碼：  
  
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
  
6.  將 AddAdornmentHandler 方法設定為 AddAdornment 命令 AddAdornment 建構函式中的處理常式。  
  
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
  
## <a name="build-and-test-the-code"></a>建置和測試程式碼  
  
1.  建置方案並開始偵錯。 實驗執行個體應該會出現。  
  
2.  建立文字檔 輸入一些文字，然後選取它。  
  
3.  在 **工具**功能表上，按一下**叫用加入 Adornment**。 球形文字說明應該會顯示 [文字] 視窗中，右邊，而且應該包含類似下列文字的文字。  
  
     您的使用者名稱  
  
     Fourscore...  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)