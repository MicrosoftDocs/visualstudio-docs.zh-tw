---
title: 逐步解說：搭配編輯器延伸模組使用快速鍵 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5c9cb20bafa552c47a2f599d12e6b66fdb2bde59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201950"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>逐步解說︰搭配編輯器延伸模組使用快速鍵
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在編輯器延伸模組中回應快速鍵。 下列逐步解說示範如何使用快速鍵，將視圖修飾加入至文字視圖。 本逐步解說是以「視口裝飾編輯器」範本為基礎，可讓您使用 + 字元來新增裝飾。  
  
## <a name="prerequisites"></a>Prerequisites  
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF)  
  
1. 建立 c # VSIX 專案。  (在 [ **新增專案** ] 對話方塊中，選取 [ **Visual c #/** 擴充性]，然後選取 [ **VSIX 專案**]。 ) 為方案命名 `KeyBindingTest` 。  
  
2. 將編輯器文字裝飾專案範本加入至專案，並將其命名為 `KeyBindingTest` 。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3. 新增下列參考，並將 **CopyLocal** 設定為 `false` ：  
  
    VisualStudio 編輯器  
  
    VisualStudio： Interop  
  
    VisualStudio. 14。0  
  
    VisualStudio. TextManager. Interop  
  
   在 KeyBindingTest 類別檔案中，將類別名稱變更為 PurpleCornerBox。 使用出現在左邊界的燈泡，以進行其他適當的變更。 在此函式內，將裝飾層的名稱從 **KeyBindingTest** 變更為 **PurpleCornerBox**：  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>定義命令篩選器  
 命令篩選器是的實作為 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ，它會藉由具現化裝飾來處理命令。  
  
1. 加入類別檔案，並將它命名為 `KeyBindingCommandFilter`。  
  
2. 使用陳述式加入下列程式碼。  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3. 名為 KeyBindingCommandFilter 的類別應該繼承自 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4. 新增文字視圖的私用欄位、命令鏈中的下一個命令，以及表示是否已新增命令篩選器的旗標。  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5. 加入設定文字視圖的函式。  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6. 依照下列方式執行 `QueryStatus()` 方法。  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. `Exec()`如果有輸入 + 字元，請執行方法，讓它將紫色方塊新增至 view。  
  
    ```csharp  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## <a name="adding-the-command-filter"></a>新增命令篩選器  
 裝飾提供者必須將命令篩選加入至文字視圖。 在此範例中，提供者會實作為 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 接聽文字視圖建立事件。 這個裝飾提供者也會匯出裝飾圖層，以定義裝飾的迭置順序。  
  
1. 在 KeyBindingTestTextViewCreationListener 檔案中，新增下列 using 語句：  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2. 在裝飾層定義中，將 AdornmentLayer 的名稱從 **KeyBindingTest** 變更為 **PurpleCornerBox**。  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. 若要取得文字視圖介面卡，您必須匯入 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> 。  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. 變更 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 方法，使其加入 `KeyBindingCommandFilter` 。  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. `AddCommandFilter`處理常式會取得文字視圖介面卡，並新增命令篩選器。  
  
    ```csharp  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  
  
## <a name="making-the-adornment-appear-on-every-line"></a>使裝飾出現在每一行  
 原始裝飾會出現在文字檔中的每個字元 ' a '。 既然我們已變更程式碼來新增裝飾以回應 ' + ' 字元，它就只會在輸入 ' + ' 的行上新增裝飾。 我們可以變更裝飾程式碼，使裝飾一次出現在每個 ' a ' 上。  
  
 在 KeyBindingTest.cs 檔案中，將 CreateVisuals ( # A1 方法變更為逐一查看視圖中的所有行，以裝飾 ' a ' 字元。  
  
```csharp  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
  
1. 建立 KeyBindingTest 方案，並在實驗實例中執行它。  
  
2. 建立或開啟文字檔。 輸入一些文字，其中包含字元 ' a '，然後在文字視圖的任何位置輸入 +。  
  
     檔案中的每個 ' a ' 字元都應出現紫色方塊。
