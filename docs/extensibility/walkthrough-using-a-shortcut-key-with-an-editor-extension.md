---
title: 使用快速鍵搭配編輯器延伸模組
description: 瞭解如何使用快速鍵將視圖修飾加入至文字視圖。 本逐步解說是以「區裝飾編輯器」範本為基礎。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2d49fa9e858d65529e466f6ed960835ab8c2324
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061949"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>逐步解說：搭配編輯器延伸模組使用快速鍵
您可以在編輯器延伸模組中回應快速鍵。 下列逐步解說示範如何使用快速鍵，將視圖修飾加入至文字視圖。 本逐步解說是以「視口裝飾編輯器」範本為基礎，可讓您使用 + 字元來新增裝飾。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-managed-extensibility-framework-mef-project"></a>建立 Managed Extensibility Framework (MEF) 專案

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

在 KeyBindingTestTextViewCreationListener .cs 類別檔案中，將 AdornmentLayer 的名稱從 **KeyBindingTest** 變更為 **PurpleCornerBox**：

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>處理 TYPECHAR 命令
在 Visual Studio 2017 15.6 版之前，在編輯器延伸模組中處理命令的唯一方式是執行以 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 命令篩選器為基礎的命令。 Visual Studio 2017 15.6 版引進了以編輯器命令處理常式為基礎的新式簡化方法。 接下來的兩節將示範如何使用舊版和新式方法來處理命令。

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>定義 Visual Studio 2017 15.6 版之前 (的命令篩選) 

 命令篩選器是的實作為 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ，它會藉由具現化裝飾來處理命令。

1. 加入類別檔案，並將它命名為 `KeyBindingCommandFilter`。

2. 新增下列 using 指示詞。

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. 名為 KeyBindingCommandFilter 的類別應該繼承自 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. 新增文字視圖的私用欄位、命令鏈中的下一個命令，以及表示是否已新增命令篩選器的旗標。

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
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

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. 執行 `Exec()` 方法，以便在輸入加號 () 字元時，將紫色方塊加入視圖 **+** 。

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>在 Visual Studio 2017 15.6 版之前新增命令篩選器 () 
 裝飾提供者必須將命令篩選加入至文字視圖。 在此範例中，提供者會實作為 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 接聽文字視圖建立事件。 這個裝飾提供者也會匯出裝飾圖層，以定義裝飾的迭置順序。

1. 在 KeyBindingTestTextViewCreationListener 檔案中，新增下列 using 指示詞：

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

2. 若要取得文字視圖介面卡，您必須匯入 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> 。

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. 變更 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 方法，使其加入 `KeyBindingCommandFilter` 。

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. `AddCommandFilter`處理常式會取得文字視圖介面卡，並新增命令篩選器。

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>執行命令處理常式 (從 Visual Studio 2017 15.6 版開始) 

首先，更新專案的 Nuget 參考，以參考最新的編輯器 API：

1. 以滑鼠右鍵按一下專案，然後選取 [ **管理 Nuget 套件**]。

2. 在 **Nuget 封裝管理員** 中，選取 [ **更新** ] 索引標籤，選取 [ **選取所有封裝** ] 核取方塊，然後選取 [ **更新**]。

命令處理常式是的實，它會藉由具現 <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601> 化裝飾來處理命令。

1. 加入類別檔案，並將它命名為 `KeyBindingCommandHandler`。

2. 新增下列 using 指示詞。

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. 名為 KeyBindingCommandHandler 的類別應該繼承自 `ICommandHandler<TypeCharCommandArgs>` ，並將其匯出為 <xref:Microsoft.VisualStudio.Commanding.ICommandHandler> ：

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. 新增命令處理常式的顯示名稱：

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. 依照下列方式執行 `GetCommandState()` 方法。 因為此命令處理常式會處理核心編輯器 TYPECHAR 命令，所以可以將啟用命令的程式委派給核心編輯器。

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. 執行 `ExecuteCommand()` 方法，以便在輸入加號 () 字元時，將紫色方塊加入視圖 **+** 。

   ```csharp
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```

   7. 將裝飾層定義從 *KeyBindingTestTextViewCreationListener* 檔複製到 *KeyBindingCommandHandler .cs* ，然後刪除 *KeyBindingTestTextViewCreationListener .cs* 檔案：

   ```csharp
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;
   ```

## <a name="make-the-adornment-appear-on-every-line"></a>使裝飾出現在每一行

原始裝飾會出現在文字檔中的每個字元 ' a '。 既然我們已變更程式碼以新增裝飾以回應 **+** 字元，它只會在輸入字元的行上新增裝飾 **+** 。 我們可以變更裝飾程式碼，使裝飾一次出現在每個 ' a ' 上。

在 *KeyBindingTest .cs* 檔案中，變更 `CreateVisuals()` 方法以逐一查看視圖中的所有行，以裝飾 ' a ' 字元。

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

## <a name="build-and-test-the-code"></a>建立並測試程式碼

1. 建立 KeyBindingTest 方案，並在實驗實例中執行它。

2. 建立或開啟文字檔。 輸入一些文字，其中包含字元 ' a '，然後 **+** 在文字視圖的任何位置輸入。

     檔案中的每個 ' a ' 字元都應出現紫色方塊。
