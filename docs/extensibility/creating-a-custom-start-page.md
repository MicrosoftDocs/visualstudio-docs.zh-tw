---
title: 建立自訂起始頁 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 2b0b8c6fde31f4f4d9573381e511465e60086add
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336671"
---
# <a name="creating-a-custom-start-page"></a>建立自訂起始頁

您可以依照這份文件中的步驟來建立自訂起始頁。

## <a name="create-a-blank-start-page"></a>建立空白起始頁

首先，請藉由建立的空白起始頁 *.xaml*具有 Visual Studio 可以辨識的標記結構的檔案。 然後，加入標記和程式碼後置來產生的外觀和您想要的功能。

1. 建立新的專案之型別的**WPF 應用程式**(**Visual C#**  > **Windows Desktop**)。

2. 加入 `Microsoft.VisualStudio.Shell.14.0` 的參考。

3. 在 XML 編輯器中開啟 XAML 檔案，並變更最上層\<視窗中 > 項目\<UserControl > 項目，但不會移除任何命名空間宣告。

4. 移除`x:Class`從最上層元素宣告。 這可讓 XAML 內容相容於 Visual Studio 工具視窗裝載 [入門] 頁面。

5. 將下列命名空間宣告加入至最上層\<UserControl > 項目。

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     這些命名空間可讓您存取 Visual Studio 命令、 控制項和 UI 設定。 如需詳細資訊，請參閱 <<c0> [ 加入 Visual Studio 命令，以起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)。

     下列範例示範中的標記 *.xaml*空白起始頁的檔案。 任何自訂的內容應該放在內部<xref:System.Windows.Controls.Grid>項目。

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

6. 將控制項新增至空\<UserControl > 填寫 自訂起始頁的項目。 如需如何新增功能的 Visual Studio 的特定資訊，請參閱[加入 Visual Studio 命令，以起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)。

## <a name="test-and-apply-the-custom-start-page"></a>測試並套用自訂起始頁

未設定執行自訂的 [入門] 頁面，直到您確認它並未損毀 Visual Studio 的 Visual Studio 的主要執行個體。 相反地，在測試實驗執行個體。

### <a name="to-test-a-manually-created-custom-start-page"></a>若要測試以手動方式建立自訂起始頁

1. 將您的 XAML 檔案，並支援文字檔案或標記檔案，為複製 *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\* 資料夾。

2. 如果您的起始頁會參考任何控制項或 Visual Studio 不會安裝的組件中的類型，將組件複製並貼在 *{Visual Studio 安裝資料夾} \Common7\IDE\PrivateAssemblies\\* .

3. 在 Visual Studio 命令提示字元中，輸入**devenv /rootsuffix Exp**開啟 Visual Studio 的實驗執行個體。

4. 在實驗執行個體中，移至**工具** > **選項** > **環境** > **啟動**頁面上，選取您的 XAML 檔案，從**自訂起始頁**下拉式清單。

5. 在 [檢視]  功能表上，按一下 [起始頁]  。

     應該會顯示您的自訂起始頁。 如果您想要變更任何檔案，您必須關閉實驗執行個體、 進行變更、 複製並貼變更的檔案，然後再重新開啟實驗的執行個體，以檢視所做的變更。

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>若要套用自訂起始頁在 Visual Studio 的主要執行個體

- 您已經測試您的起始頁，並發現它穩定之後，請使用**自訂起始頁**選項**選項**對話方塊中，將其選取為 Visual Studio 的主要執行個體中的 [開始] 頁面

## <a name="see-also"></a>另請參閱

- [逐步解說：將自訂的 XAML 加入至 [入門] 頁面](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [將使用者控制項加入至 [入門] 頁面](../extensibility/adding-user-control-to-the-start-page.md)
- [將 Visual Studio 命令加入至起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [逐步解說：起始頁上儲存使用者設定](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [部署自訂起始頁](../extensibility/deploying-custom-start-pages.md)