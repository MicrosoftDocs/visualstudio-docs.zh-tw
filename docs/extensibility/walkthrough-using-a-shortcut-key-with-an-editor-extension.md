---
title: 演練:使用帶有編輯器擴展的快速鍵 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651598c0dbe746a9a26a6d60ce72b02853f98d47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697156"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>演練:使用帶有編輯器延伸的捷徑
您可以回應編輯器擴展中的快速鍵。 以下演練演示如何使用快捷鍵向文本視圖添加檢視修飾。 這個演練基於視口修飾編輯器範本,它允許您使用 + 字元添加修飾。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-managed-extensibility-framework-mef-project"></a>建立系統延伸架構 (MEF) 專案

1. 創建 C# VSIX 專案。 ( 在 **'新增項目'** 對話框中,選擇**視覺化 C# / 可擴充性**,然後選擇**VSIX 專案**。命名解決方案`KeyBindingTest`。

2. 加入專案加入編輯器文字修飾樣本並將命名`KeyBindingTest`。 關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 新增以下參考並將**CopyLocal**`false`設定為 :

    微軟.VisualStudio.編輯器

    微軟.VisualStudio.OLE.Interop

    微軟.VisualStudio.shell.14.0

    微軟.VisualStudio.文字管理員.互通

   在 KeyBindingTest 類檔中,將類名稱更改為紫色 CornerBox。 使用左側邊距中顯示的燈泡進行其他適當的更改。 在建構函數中,將修飾圖層的名稱從**鍵綁定測試**更改為**紫色CornerBox:**

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

在KeyBindingTestTextViewCreationListener.cs類檔中,將修飾層的名稱從**鍵綁定測試**更改為**紫色CornerBox:**

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>處理 TYPECHAR 命令
在 Visual Studio 2017 版本 15.6 之前,在<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>編輯器擴展中處理命令 的唯一方法是實現基於命令篩選器。 Visual Studio 2017 版本 15.6 引入了一種基於編輯器命令處理程序的現代簡化方法。 接下來的兩節演示如何使用舊式方法和現代方法處理命令。

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>定義命令篩選器(在 Visual Studio 2017 版本 15.6 之前)

 命令篩選器是<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>的 實現,它通過實例化修飾來處理命令。

1. 加入類別檔案，並將它命名為 `KeyBindingCommandFilter`。

2. 使用指令添加以下內容。

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. 名為 KeyBinding 命令篩選器的類<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>應從 繼承。

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. 為文本檢視、命令鏈中的下一個命令添加私有欄位,以及一個標誌,以表示是否已添加命令篩選器。

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. 新增設定文本檢視的建構函數。

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. 實現方法`QueryStatus()`如下。

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. 實現該方法`Exec()`,以便在鍵入加號**+**( ) 字元時向檢視添加紫色框。

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>新增指令篩選器(在 Visual Studio 2017 版本 15.6 之前)
 修飾提供程式必須向文字檢視添加命令篩選器。 在此範例中,提供程式實現<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>偵聽文本檢視創建事件。 此修飾提供程式還匯出修飾層,該層定義修飾的 Z 順序。

1. 在鍵繫結測試文字檢視建立偵聽器檔中,使用指令新增以下內容:

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

2. 要取得文字檢視配接器,必須匯入<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>。

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. 變更<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法來新增`KeyBindingCommandFilter`。

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. 處理程式`AddCommandFilter`取得文字檢視卡機並加入指令篩選器。

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>實現命令處理程式 (從 Visual Studio 2017 版本 15.6 開始)

首先,更新專案的 Nuget 引用以參考最新的編輯器 API:

1. 右鍵單擊項目並選擇 **「管理 Nuget 包**」。

2. 在**Nuget 套件管理器**中,選擇「**更新**」選項卡,**選擇「選擇所有包**」複選框,然後選擇 **「更新**」。

命令處理程式是<xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>的 實現,它通過實例化修飾來處理命令。

1. 加入類別檔案，並將它命名為 `KeyBindingCommandHandler`。

2. 使用指令添加以下內容。

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. 名為 KeyBindingCommandHandler 的`ICommandHandler<TypeCharCommandArgs>`類別應 從繼承<xref:Microsoft.VisualStudio.Commanding.ICommandHandler>,並將其 匯出為 :

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. 新增命令處理程式的顯示名稱:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. 實現方法`GetCommandState()`如下。 由於此命令處理程式處理核心編輯器 TYPECHAR 命令,因此可以將啟用該命令委派給核心編輯器。

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. 實現該方法`ExecuteCommand()`,以便在鍵入加號**+**( ) 字元時向檢視添加紫色框。

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

   7. 將修飾圖層定義從*KeyBindingTestTextViewCreationListener.cs*檔案複製到*KeyBindingCommandHandler.cs,* 然後刪除*KeyBindingTestTextViewCreationListener.cs*檔案:

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

## <a name="make-the-adornment-appear-on-every-line"></a>使修飾出現在每行上

原始修飾出現在文本檔中的每個字元"a"上。 現在,我們更改了代碼以添加修飾以回應**+** 該字元,它僅在鍵入字元**+** 的行上添加修飾。 我們可以更改修飾代碼,以便修飾再次出現在每個"a"上。

在*KeyBindingTest.cs*檔案中`CreateVisuals()`,更改方法以遍轉檢視中的所有行以修飾「a」字元。

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

## <a name="build-and-test-the-code"></a>組建及測試代碼

1. 構建金鑰綁定測試解決方案並在實驗實例中運行它。

2. 建立或打開文字檔。 鍵入一些包含字元"a"的單詞,然後在文字**+** 視圖中鍵入任意位置。

     檔中的每個"a"字元上都應出現紫色方塊。
