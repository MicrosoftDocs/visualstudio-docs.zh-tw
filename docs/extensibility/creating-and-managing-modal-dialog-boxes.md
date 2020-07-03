---
title: 建立和管理模式對話方塊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2f4f296bb155bcde82235d962ae63c8fa4d41d7
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903782"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>建立和管理模式對話方塊
當您在 Visual Studio 內建立強制回應對話方塊時，必須確定對話方塊的父視窗已停用，同時顯示對話方塊，然後在對話方塊關閉之後重新啟用父視窗。 如果沒有這麼做，您可能會收到錯誤： *Microsoft Visual Studio 無法關閉，因為強制回應對話方塊正在作用中。關閉使用中的對話方塊，然後再試一次。*

有兩種方式可以執行這項作業。 如果您有 WPF 對話方塊，建議的方法是從衍生它 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> ，然後呼叫 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> 來顯示對話方塊。 如果您這樣做，就不需要管理父視窗的強制回應狀態。

如果您的對話方塊不是 WPF，或基於某些其他原因而無法衍生您的對話方塊類別 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> ，則您必須 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> 使用參數為0（false）來呼叫方法，然後再顯示對話方塊，並在關閉對話方塊之後使用參數1（true）再次呼叫方法，以取得對話方塊的父系。

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>建立衍生自 DialogWindow 的對話方塊

1. 建立名為**OpenDialogTest**的 VSIX 專案，並新增名為**OpenDialog**的功能表命令。 如需如何執行此動作的詳細資訊，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能。

2. 若要使用 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 類別，您必須將參考加入至下列元件（在 [**加入參考**] 對話方塊的 [架構] 索引標籤中）：

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. 在*OpenDialog.cs*中，新增下列 `using` 語句：

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. 宣告名為 `TestDialogWindow` 且衍生自的類別 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> ：

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. 若要能夠將對話方塊最小化並最大化，請將 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> 和設定 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> 為 true：

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. 在方法中，將現有的程式 `OpenDialog.ShowMessageBox` 代碼取代為下列內容：

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. 建置並執行應用程式。 應該會出現 Visual Studio 的實驗實例。 在實驗實例的 [**工具**] 功能表上，您應該會看到名為**Invoke OpenDialog**的命令。 當您按一下此命令時，您應該會看到對話方塊視窗。 您應該能夠將視窗最小化並最大化。

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>建立和管理不是衍生自 DialogWindow 的對話方塊

1. 在這個程式中，您可以使用您在上一個程式中建立的**OpenDialogTest**解決方案，並搭配相同的元件參考。

2. 新增下列宣告 `using` ：

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. 建立一個名為 `TestDialogWindow2` 且衍生自的類別 <xref:System.Windows.Window> ：

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. 將私用參考新增至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ：

    ```
    private IVsUIShell shell;
    ```

5. 新增可將參考設定為的函式 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ：

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. 在方法中，將現有的程式 `OpenDialog.ShowMessageBox` 代碼取代為下列內容：

    ```csharp
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));

    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);
    //get the owner of this dialog
    IntPtr hwnd;
    uiShell.GetDialogOwnerHwnd(out hwnd);
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;
    uiShell.EnableModeless(0);
    try
    {
        WindowHelper.ShowModal(testDialog2, hwnd);
    }
    finally
    {
        // This will take place after the window is closed.
        uiShell.EnableModeless(1);
    }
    ```

7. 建置並執行應用程式。 在 [**工具**] 功能表上，您應該會看到名為 [叫用**OpenDialog**] 的命令。 當您按一下此命令時，您應該會看到對話方塊視窗。
