---
title: "逐步解說︰ 使用快速鍵的編輯器延伸模組 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，新的命令連結按鍵"
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# 逐步解說︰ 使用快速鍵的編輯器延伸模組
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在您的編輯器延伸模組中回應快速鍵。 下列逐步解說示範如何使用快速鍵，將檢視裝飾新增至文字檢視。 本逐步解說根據檢視區裝飾編輯器範本，並可讓您使用新增裝飾 \+ 字元。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## Managed Extensibility Framework \(MEF\)  
  
1.  建立 C\# VSIX 專案。 \(在 **新的專案** 對話方塊中，選取 **Visual C\# \/ 擴充性**, ，然後 **VSIX 專案**。\) 將方案命名為 `KeyBindingTest`。  
  
2.  編輯器文字裝飾項目範本加入至專案，並將它 `KeyBindingTest`。 如需詳細資訊，請參閱[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  加入下列參考，並設定 **CopyLocal** 至 `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 在 KeyBindingTest 類別檔案中，類別名稱的內容變更為 PurpleCornerBox。 使用在左邊界出現燈泡，進行適當變更。 內部建構函式，將變更從裝飾圖層名稱 **KeyBindingTest** 至 **PurpleCornerBox**:  
  
```c#  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## 定義命令的篩選  
 命令篩選器是實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, ，以處理命令，以具現化的裝飾。  
  
1.  將類別檔案，並將它 `KeyBindingCommandFilter`。  
  
2.  使用陳述式加入下列程式碼。  
  
    ```c#  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  名為 KeyBindingCommandFilter 的類別應該繼承自 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
    ```c#  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  加入私用欄位的文字檢視、 下一個命令中的命令鏈結和旗標，表示是否已加入命令篩選器。  
  
    ```c#  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  新增設定文字檢視的建構函式。  
  
    ```c#  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  實作 `QueryStatus()` 方法，如下所示。  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  實作 `Exec()` 方法，使它會新增至檢視紫色方塊如果 \+ 輸入字元。  
  
    ```c#  
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
  
## 在新增命令篩選器  
 文字檢視裝飾提供者必須加入命令篩選器。 在此範例中，提供者會實作 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 來接聽文字檢視建立事件。 此裝飾的提供者也會匯出裝飾圖層，亦即定義裝飾 Z 順序。  
  
1.  在 KeyBindingTestTextViewCreationListener 檔案中，新增下列 using 陳述式︰  
  
    ```c#  
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
  
2.  在裝飾層定義中，變更的名稱從 AdornmentLayer **KeyBindingTest** 至 **PurpleCornerBox**。  
  
    ```c#  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  若要取得文字檢視配接器，您必須匯入 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>。  
  
    ```c#  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  變更 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 方法，使其將 `KeyBindingCommandFilter`。  
  
    ```c#  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  `AddCommandFilter` 取得文字檢視配接器處理常式，並新增命令篩選器。  
  
    ```c#  
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
  
## 讓裝飾出現在每一行  
 原始裝飾出現在每個字元 'a' 文字檔案中。 既然我們已變更的程式碼，以加入裝飾回應 '\+' 字元，只能在一行上加入裝飾其中 '\+' 型別。 我們可以變更裝飾程式碼，就會出現一次的裝飾每 'a'。  
  
 在 KeyBindingTest.cs 檔案中，變更 CreateVisuals\(\) 方法來逐一查看裝飾 'a' 字元檢視中的所有行。  
  
```c#  
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
  
## 建置和測試程式碼  
  
1.  KeyBindingTest 方案中建置並執行它的實驗執行個體。  
  
2.  建立或開啟文字檔案。 輸入一些文字，包含字元 'a'，然後輸入 \+ 文字檢視中的任何位置。  
  
     紫色方應該會出現在每個檔案中的 'a' 字元。