---
title: 逐步解說： 使用快速鍵編輯器延伸模組與 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f3d0a9f8f730808cd8179599669342b530f921a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>逐步解說： 使用快速鍵編輯器延伸模組與
在您的編輯器延伸模組，您可以回應快速鍵。 下列逐步解說示範如何使用快速鍵將檢視裝飾加入文字檢視。 本逐步解說根據檢視區裝飾編輯器範本，並可讓您使用新增裝飾 + 字元。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF)  
  
1.  建立 C# VSIX 專案。 (在**新專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名`KeyBindingTest`。  
  
2.  編輯器文字裝飾項目範本加入至專案並將其命名`KeyBindingTest`。 如需詳細資訊，請參閱[編輯器項目範本以建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  將下列參考加入並設定**CopyLocal**至`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 KeyBindingTest 類別檔案中類別名稱的內容變更為 PurpleCornerBox。 用於燈泡出現在左邊界中進行適當的變更。 建構函式，內變更 從裝飾圖層名稱**KeyBindingTest**至**PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>定義命令篩選器  
 命令篩選器是實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>，藉由執行個體化裝飾處理命令。  
  
1.  將類別檔案並將其命名`KeyBindingCommandFilter`。  
  
2.  使用陳述式加入下列程式碼。  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  名為 KeyBindingCommandFilter 的類別應該繼承自<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  加入私用欄位的文字檢視中下, 一個命令中的命令鏈結和旗標，表示是否已加入命令篩選器。  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  新增設定的文字檢視的建構函式。  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  實作`QueryStatus()`方法，如下所示。  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  實作`Exec()`方法，使它會加入至檢視紫色方塊如果 + 輸入字元。  
  
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
 裝飾的提供者必須將命令篩選器加入文字檢視。 在此範例中，提供者會實作<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>聆聽文字檢視建立事件。 此裝飾提供者也會匯出裝飾圖層，會定義裝飾的 Z 順序。  
  
1.  在 KeyBindingTestTextViewCreationListener 檔案中，加入下列 using 陳述式：  
  
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
  
2.  在裝飾層定義中，變更名稱從 AdornmentLayer **KeyBindingTest**至**PurpleCornerBox**。  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  若要取得文字檢視配接器，您必須匯入<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>。  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  變更<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法，使其將`KeyBindingCommandFilter`。  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  `AddCommandFilter`取得文字檢視配接器處理常式，並將命令篩選器。  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>進行裝飾出現在每一行  
 原始裝飾出現在每個字元 'a' 文字檔案中。 既然我們已變更的程式碼，以回應為 '+' 字元加入裝飾，只能在一行上加入裝飾其中 '+' 型別。 我們可以變更裝飾程式碼，就會出現一次的裝飾每隔 'a'。  
  
 在 KeyBindingTest.cs 檔案中，變更 CreateVisuals() 方法來逐一查看裝飾 'a' 字元檢視中的所有行。  
  
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
  
1.  建置 KeyBindingTest 方案，並在實驗執行個體中執行。  
  
2.  建立或開啟文字檔。 輸入一些文字包含字元 'a'，然後輸入 + 文字檢視中的任何位置。  
  
     紫色正方形應該會出現在每個檔案中的 'a' 字元。