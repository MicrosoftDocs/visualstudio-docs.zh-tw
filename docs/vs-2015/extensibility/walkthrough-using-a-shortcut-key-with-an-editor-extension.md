---
title: 逐步解說：編輯器擴充功能搭配使用攠摝坫 |Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201950"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>逐步解說：在編輯器延伸模組中使用快速鍵
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在您的編輯器延伸模組中回應快速鍵。 下列逐步解說會示範如何使用快速鍵將文字檢視的檢視裝飾。 本逐步解說根據檢視區 adornment 編輯器範本，並可讓您使用新增 adornment + 字元。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF)  
  
1. 建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為 `KeyBindingTest`。  
  
2. 編輯器文字裝飾項目範本加入專案並將它命名`KeyBindingTest`。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3. 加入下列參考，並設定**CopyLocal**到`false`:  
  
    Microsoft.VisualStudio.Editor  
  
    Microsoft.VisualStudio.OLE.Interop  
  
    Microsoft.VisualStudio.Shell.14.0  
  
    Microsoft.VisualStudio.TextManager.Interop  
  
   在 KeyBindingTest 類別檔案中，將 PurpleCornerBox 中的類別名稱。 使用左邊界出現燈泡進行適當的變更。 在建構函式中，變更 adornment 圖層，從名稱**KeyBindingTest**要**PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>定義命令篩選  
 命令篩選器是實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>，藉由執行個體化 adornment 處理命令。  
  
1. 加入類別檔案，並將它命名為 `KeyBindingCommandFilter`。  
  
2. 使用陳述式加入下列程式碼。  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3. 名為 KeyBindingCommandFilter 的類別應該繼承自<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4. 文字檢視的私用欄位下, 一個命令中加入命令鏈結中，以及表示是否已新增命令篩選器旗標。  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5. 新增設定文字檢視的建構函式。  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6. 實作`QueryStatus()`方法，如下所示。  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. 實作`Exec()`方法，因此它會加入至檢視的紫色方塊如果 + 輸入字元。  
  
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
 Adornment 提供者必須將命令篩選器加入 [文字] 檢視。 在此範例中，提供者會實作<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>來接聽文字檢視建立事件。 此裝飾提供者也會匯出裝飾圖層，其定義 adornment 疊置順序。  
  
1. 在 KeyBindingTestTextViewCreationListener 檔案中，新增下列 using 陳述式：  
  
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
  
2. 在 adornment 層定義中，變更名稱從 AdornmentLayer **KeyBindingTest**要**PurpleCornerBox**。  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. 若要取得文字檢視配接器，您必須匯入<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>。  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. 變更<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法，讓它將加入`KeyBindingCommandFilter`。  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. `AddCommandFilter`取得文字檢視配接器處理常式，並將命令篩選器。  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>讓裝飾出現在每一行  
 原始的裝飾出現在每個字元 'a' 文字檔案中。 既然我們已變更程式碼來新增裝飾，以回應 '+' 字元，只能在一行上新增 adornment 其中 '+' 型別。 我們可以變更 adornment 程式碼，就會出現一次的裝飾每個 'a'。  
  
 在 KeyBindingTest.cs 檔案中，變更 CreateVisuals() 方法來逐一查看要裝飾 'a' 字元的檢視中的所有行。  
  
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
  
1. 建置 KeyBindingTest 方案，並在實驗執行個體中執行它。  
  
2. 建立或開啟文字檔案。 輸入一些文字包含字元 'a'，然後輸入 + [文字] 檢視中的任何位置。  
  
     紫色的平方應該會出現在檔案中的每個 'a' 字元。
