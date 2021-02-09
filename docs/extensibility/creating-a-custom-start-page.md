---
title: 建立自訂起始頁 |Microsoft Docs
description: 瞭解如何建立自訂起始頁。 從空白起始頁面開始，將控制項新增至空白 UserControl 元素，然後測試您的頁面。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 65415c22da2815650278ac1190e7d19f54b96063
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853081"
---
# <a name="creating-a-custom-start-page"></a>建立自訂起始頁

您可以遵循本檔中的步驟來建立自訂起始頁。

## <a name="create-a-blank-start-page"></a>建立空白起始頁

首先，建立一個包含 Visual Studio 將辨識之標記結構的 *.xaml* 檔案，以建立空白的起始頁。 然後，新增標記和程式碼後端，以產生您想要的外觀和功能。

1. 建立 **WPF 應用程式** 類型的新專案， (**Visual c #**  >  **Windows 桌面**) 。

2. 加入 `Microsoft.VisualStudio.Shell.14.0` 的參考。

3. 在 XML 編輯器中開啟 XAML 檔案，然後將最上層元素變更 \<Window> 為元素， \<UserControl> 而不需移除任何命名空間宣告。

4. `x:Class`從最上層元素移除宣告。 這可讓 XAML 內容與裝載起始頁的 Visual Studio 工具視窗相容。

5. 將下列命名空間宣告加入至最上層 \<UserControl> 元素。

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     這些命名空間可讓您存取 Visual Studio 命令、控制項和 UI 設定。 如需詳細資訊，請參閱 [將 Visual Studio 命令新增至起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)。

     下列範例會在 *.xaml* 檔案中顯示空白起始頁的標記。 任何自訂內容都應該放在內部 <xref:System.Windows.Controls.Grid> 元素中。

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

6. 將控制項新增至空白 \<UserControl> 元素，以填入您的自訂起始頁。 如需如何新增 Visual Studio 特定功能的詳細資訊，請參閱 [將 Visual Studio 命令新增至起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)。

## <a name="test-and-apply-the-custom-start-page"></a>測試及套用自訂起始頁

請勿將 Visual Studio 的主要實例設定為執行自訂起始頁，直到您確認它不會損毀 Visual Studio。 相反地，請在實驗實例中進行測試。

### <a name="to-test-a-manually-created-custom-start-page"></a>若要測試手動建立的自訂起始頁

1. 將您的 XAML 檔案及任何支援的文字檔或標記檔案複製到 *%USERPROFILE%\My Documents\Visual Studio 2015 \ StartPages \\* 資料夾。

2. 如果您的起始頁參考了 Visual Studio 未安裝之元件中的任何控制項或類型，請複製元件，然後將它們貼到 *{Visual Studio 安裝資料夾 \\ } \Common7\IDE\PrivateAssemblies* 中。

3. 在 Visual Studio 的命令提示字元中，輸入 **devenv/Rootsuffix Exp** 以開啟 Visual Studio 的實驗實例。

4. 在實驗性實例中，移至 [**工具**  >  **選項**  >  **環境**  >  **啟動**] 頁面，然後從 [**自訂起始頁**] 下拉式清單中選取您的 XAML 檔案。

5. 在 [檢視]  功能表上，按一下 [起始頁] 。

     應該會顯示您的自訂起始頁。 如果您想要變更任何檔案，您必須關閉實驗性實例、進行變更、複製並貼上變更的檔案，然後重新開啟實驗實例以查看變更。

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>若要將自訂起始頁套用至 Visual Studio 的主要實例

- 測試您的起始頁併發現它穩定之後，請使用 [**選項**] 對話方塊中的 [**自訂起始頁**] 選項，將其選取為主要實例中的起始頁 Visual Studio

## <a name="see-also"></a>另請參閱

- [逐步解說：將自訂 XAML 新增至起始頁](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [將使用者控制項新增至起始頁](../extensibility/adding-user-control-to-the-start-page.md)
- [將 Visual Studio 命令新增至起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [逐步解說：在起始頁儲存使用者設定](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [部署自訂起始頁](../extensibility/deploying-custom-start-pages.md)
