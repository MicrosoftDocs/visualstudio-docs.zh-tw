---
title: 建立與管理模式對話框 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 786a2fbe2b75c51420668eb1ab6f596213d3da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739490"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>建立與管理模式對話框
在 Visual Studio 中建立模式對話框時,必須確保在顯示對話方塊時禁用對話框的父視窗,然後在關閉對話框後重新啟用父視窗。 如果不這樣做,您可能會收到錯誤 *:Microsoft Visual Studio 無法關閉,因為模式對話框處於活動狀態。關閉活動對話框,然後重試。*

有兩種方法可以做到這一點。 如果具有 WPF 對話框,則建議的方法是從<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>派生 它<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A>,然後調用 以顯示對話方塊。 如果這樣做,則不需要管理父視窗的模式狀態。

如果對話框不是 WPF,或者由於其他原因無法從<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>派生 對話方塊類,則必須<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A>通過自己調用和管理模式狀態來獲取對話框的父級,方法是在顯示對話方塊之前調用參數為<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A>0(false) 的方法,並在關閉對話方塊後再次調用該方法,參數為 1(true)。

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>建立對話框視窗派生的對話框

1. 建立名為**OpenDialogTest 的**VSIX 專案,並加入名為**OpenDialog**的選單指令 。 有關如何執行此操作的詳細資訊,請參考[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

2. 要使用<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>類別,必須新增對以下程式集的引用(在 **'新增引用**'對話框的'框架'選項卡中):

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. 在*OpenDialog.cs*中`using`,加入以下文句:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. 宣告已使用<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>`TestDialogWindow`的命名類別:

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. 為了能夠最小化和最大化對話框,請設置<xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A><xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A>和 true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. 在`OpenDialog.ShowMessageBox`方法中,將現有代碼取代為以下內容:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. 建置並執行應用程式。 應出現視覺工作室的實驗實例。 在實驗實例**的「工具」** 選單上,您應該看到名為 **「調用 OpenDialog」** 的命令。 按一下此命令時,應看到對話框視窗。 您應該能夠最小化和最大化視窗。

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>建立與管理未從對話框視窗派生的對話框

1. 對於此過程,可以使用在上一過程中創建的**OpenDialogTest**解決方案,並使用相同的程式集引用。

2. 新增以下`using`宣告:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. 建立名為`TestDialogWindow2`的類別,該類別<xref:System.Windows.Window>的類別 :

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. 加入對<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>的私有引用。

    ```
    private IVsUIShell shell;
    ```

5. 添加將引用設定為<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>的構造函數。

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. 在`OpenDialog.ShowMessageBox`方法中,將現有代碼取代為以下內容:

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

7. 建置並執行應用程式。 在 **「工具」** 選單上,您應該看到名為 **「調用打開對話**」的命令。 按一下此命令時,應看到對話框視窗。
