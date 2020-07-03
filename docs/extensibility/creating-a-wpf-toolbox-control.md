---
title: 建立 WPF 工具箱控制項 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6aa6051648e495e21f7954a737f7b572ce6a6f2
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903950"
---
# <a name="create-a-wpf-toolbox-control"></a>建立 WPF 工具箱控制項

WPF （Windows Presentation Framework） [工具箱控制項] 範本可讓您建立在安裝擴充功能時自動新增至 [**工具箱**] 的 wpf 控制項。 本逐步解說將示範如何使用範本建立可散發給其他使用者的 [**工具箱**] 控制項。

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-the-toolbox-control"></a>建立工具箱控制項

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>使用 WPF 工具箱控制項建立擴充功能

1. 建立名為的 VSIX 專案 `MyToolboxControl` 。 藉由搜尋「vsix」，您可以在 [**新增專案**] 對話方塊中尋找 VSIX 專案範本。

2. 當專案開啟時，加入名為的**WPF 工具箱控制項**專案範本 `MyToolboxControl` 。 在 [**方案總管**中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**加入新專案**] 對話方塊中，移至 [ **Visual c #** 擴充性]，  >  **Extensibility**然後選取 [ **WPF 工具箱控制項**]。 在視窗底部的 [**名稱**] 欄位中，將命令檔名稱變更為*MyToolboxControl.cs*。

    方案現在包含一個使用者控制項、一個 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> 將控制項加入 [**工具箱**] 中的，以及一個用於部署的 VSIX 資訊清單中的**VisualStudio. ToolboxControl**資產專案。

#### <a name="to-create-the-control-ui"></a>建立控制項 UI

1. 在設計工具中開啟*MyToolboxControl。*

    設計工具會顯示包含了 <xref:System.Windows.Controls.Button> 控制項的 <xref:System.Windows.Controls.Grid> 控制項。

2. 排列方格版面配置。 當您選取 <xref:System.Windows.Controls.Grid> 控制項時，方格的頂端和左邊緣會出現藍色控制列。 您可以按一下橫條圖，將資料列和資料行加入方格中。

3. 將子控制項加入至方格。 您可以將子控制項從 [**工具箱**] 拖曳至方格的某個區段，或在 XAML 中設定其和屬性，藉以放置該子控制項 `Grid.Row` `Grid.Column` 。 下列範例會在方格的頂端列加上兩個標籤，並在第二個數據列上加入一個按鈕。

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>重新命名控制項

 根據預設，您的控制項會在 [**工具箱**] 中顯示為**MyToolboxControl** ，位於名為**MyToolboxControl. MyToolboxControl**的群組中。 您可以在*MyToolboxControl.xaml.cs*檔案中變更這些名稱。

1. 在程式碼視圖中開啟*MyToolboxControl.xaml.cs* 。

2. 尋找 `MyToolboxControl` 類別，並將它重新命名為 TestControl。 （最快速的方法是重新命名類別，然後從內容功能表中選取 [**重新命名**]，然後完成步驟。 （如需 [**重新命名**] 命令的詳細資訊，請參閱[重新命名重構（c #）](../ide/reference/rename.md)）。

3. 移至 `ProvideToolboxControl` 屬性，並將第一個參數的值變更為**Test**。 這是將在 [**工具箱**] 中包含控制項的組名。

    產生的程式碼看起來應該像這樣：

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>組建、測試和部署

 當您對專案進行調試時，您應該會在 Visual Studio 的實驗實例的 [**工具箱**] 中找到安裝的控制項。

### <a name="to-build-and-test-the-control"></a>建置和測試控制項

1. 重建專案並開始進行調試。

2. 在 Visual Studio 的新執行個體中建立 WPF 應用程式專案。 請確定 XAML 設計工具已開啟。

3. 在 [工具箱] **** 中尋找控制項，並將它拖曳至設計介面。

4. 開始對 WPF 應用程式進行偵錯工具。

5. 確認您的控制項出現。

### <a name="to-deploy-the-control"></a>部署內容

1. 建立測試的專案之後，您可以在專案的 [\bin\debug] 資料夾中找到 *.vsix*檔案。 \*

2. 您可以按兩下 *.vsix*檔案並遵循安裝程式，將它安裝在本機電腦上。 若要卸載控制項，請移至 [**工具**]  >  [擴充功能**和更新**]，尋找控制項延伸模組，然後按一下 [**卸載**]。

3. 將 *.vsix*檔案上傳到網路或網站。

    如果您將檔案上傳到[Visual Studio Marketplace](https://marketplace.visualstudio.com/)網站，其他使用者可以使用**Tools**  >  Visual Studio 中的工具**擴充功能和更新**，在線上尋找控制項並安裝它。
