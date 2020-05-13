---
title: 建立自訂起始頁 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3ac0abfe9eedf1c03a8be3bacddbe06ff5698380
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739638"
---
# <a name="creating-a-custom-start-page"></a>建立自訂起始頁

您可以按照本文檔中的步驟創建自定義"起始頁"

## <a name="create-a-blank-start-page"></a>建立空白起始頁

首先,通過創建具有 Visual Studio 將識別的標記結構的 *.xaml*檔案,創建一個空白的起始頁。 然後,添加標記和代碼後面以生成所需的外觀和功能。

1. 創建**WPF 應用程式**類型 **(Visual C#** > **Windows 桌面**) 的新專案。

2. 加入 `Microsoft.VisualStudio.Shell.14.0` 的參考。

3. 在 XML 編輯器中打開 XAML\<檔,並將頂級視窗>元素更改為\<UserControl>元素,而無需刪除任何命名空間聲明。

4. 從頂級`x:Class`元素中刪除聲明。 這使得 XAML 內容與承載「開始頁面」的可視化工作室工具視窗相容。

5. 將以下命名空間聲明添加到頂級\<使用者控制>元素。

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     這些命名空間允許您訪問 Visual Studio 命令、控制件和 UI 設置。 有關詳細資訊,請參閱[將可視化工作室命令添加到"開始頁面](../extensibility/adding-visual-studio-commands-to-a-start-page.md)"。

     下面的範例顯示空白起始頁的 *.xaml*檔中的標記。 任何自定義內容都應位於內部<xref:System.Windows.Controls.Grid>元素中。

    ```vb
    <UserControl
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        xmlns:local="clr-namespace:StartPageHost"
        mc:Ignorable="d"
         Height="350" Width="525">
        <Grid>
        <!--Add content here.-->
        </Grid>
    </UserControl>
    ```

6. 將控制項添加到空\<使用者控制>元素以填充自訂起始頁。 有關如何添加特定於可視化工作室的功能的資訊,請參閱[將可視化工作室命令添加到"開始頁面](../extensibility/adding-visual-studio-commands-to-a-start-page.md)"。

## <a name="test-and-apply-the-custom-start-page"></a>測試並套用自訂起始頁

在驗證 Visual Studio 不會崩潰 Visual Studio 之前,不要將 Visual Studio 的主實例設置為運行自定義"開始頁」。。 而是在實驗實例中測試它。

### <a name="to-test-a-manually-created-custom-start-page"></a>測試手動建立的自訂開始頁

1. 將 XAML 檔以及任何支援的文字檔或標記檔案複製到 *%USERPROFILE%*我的文件_Visual Studio 2015_StartPages\\*資料夾。

2. 如果起始頁引用 Visual Studio 未安裝的程式集中的任何控制項或類型,請複製程式集,然後將它們貼上到 *[Visual Studio\\安裝資料夾]Common7_IDE_私有 程式集*中。

3. 在 Visual Studio 命令提示符中,鍵入**devenv /rootsuffix Exp**以打開 Visual Studio 的實驗實例。

4. 在實驗實例中,轉到 **「工具** > **選項** > **環境** > **啟動」** 頁,然後從 **「自訂起始頁」** 下拉清單中選擇 XAML 檔。

5. 在 [檢視] **** 功能表上，按一下 [起始頁] ****。

     應顯示自定義起始頁。 如果要更改任何檔,則必須關閉實驗實例、進行更改、複製和粘貼已更改的檔,然後重新打開實驗實例以查看更改。

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>在可視化工作室的主實例中應用自定義起始頁

- 測試「開始頁」並發現其穩定後,請使用 **「選項**」對話框中的 **「自訂起始頁」** 選項將其作為 Visual Studio 主實體中的起始頁選擇

## <a name="see-also"></a>另請參閱

- [演練:將自訂 XAML 新增到起始頁](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [將使用者控制件添加到"開始頁面"](../extensibility/adding-user-control-to-the-start-page.md)
- [將視覺化工作室指令加入到「開始」頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [演練:在「開始」頁上保存用戶設置](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [部署自訂起始頁](../extensibility/deploying-custom-start-pages.md)
