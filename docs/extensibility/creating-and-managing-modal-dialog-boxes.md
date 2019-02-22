---
title: 建立和管理強制回應對話方塊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfd0fb71aaca9cb3de2d7cc6d3b6229042a4e7fa
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318403"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>建立和管理強制回應對話方塊
當您建立強制回應對話方塊，在 Visual Studio 內時，您必須確定當對話方塊出現時，停用 [] 對話方塊中的父視窗，然後在關閉對話方塊之後，重新啟用父視窗。 如果不這麼做，您可能會收到錯誤：*由於強制回應對話方塊正在使用 Microsoft Visual Studio 無法關閉。請關閉使用中的對話方塊，然後重試。*

有兩種執行此動作。 建議的方式，如果您有 [WPF] 對話方塊中，是從它衍生出來<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>，然後呼叫<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A>顯示對話方塊。 如果您這麼做，您不需要管理父視窗的強制回應狀態。

如果您的對話方塊中不是 WPF，或某些其他原因，您不能衍生您的對話方塊類別從<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>，則您必須呼叫來取得對話方塊中的父代<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A>並自行管理強制回應狀態，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A>方法顯示對話方塊，並關閉對話方塊後呼叫一次與參數 1 (true) 方法前 0 (false) 的參數。

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>建立衍生自 DialogWindow 對話方塊

1. 建立 VSIX 專案，名為**OpenDialogTest** ，並新增名為的功能表命令**OpenDialog**。 如需如何執行這項操作的詳細資訊，請參閱[建立具有功能表命令的延伸模組](../extensibility/creating-an-extension-with-a-menu-command.md)。

2. 若要使用<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>類別，您必須加入下列組件的參考 (在的 [Framework] 索引標籤中**加入參考**對話方塊):

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. 在  *OpenDialog.cs*，新增下列`using`陳述式：

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. 宣告類別，名為`TestDialogWindow`衍生自<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. 若要能夠降至最低，並最大化 對話方塊中，設定<xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>和<xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A>設為 true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. 在 `OpenDialog.ShowMessageBox`方法，以下列內容取代現有的程式碼：

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. 建置並執行應用程式。 Visual Studio 的實驗執行個體應該會出現。 在 **工具**的實驗執行個體的功能表您應該會看到名為的命令**叫用 OpenDialog**。 當您按一下此命令時，您應該會看到 [對話方塊] 視窗。 您應該能夠降至最低，並將視窗最大化。

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>建立和管理對話方塊中，不是衍生自 DialogWindow

1. 此程序中，您可以使用**OpenDialogTest**您在具有相同的組件參考的上一個程序中建立的方案。

2. 新增下列`using`宣告：

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. 建立一個名為`TestDialogWindow2`衍生自<xref:System.Windows.Window>:

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. 加入私用參考<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:

    ```
    private IVsUIShell shell;
    ```

5. 新增至設定參考的建構函式<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. 在 `OpenDialog.ShowMessageBox`方法，以下列內容取代現有的程式碼：

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

7. 建置並執行應用程式。 在 [**工具**] 功能表您應該會看到名為的命令**叫用 OpenDialog**。 當您按一下此命令時，您應該會看到 [對話方塊] 視窗。
