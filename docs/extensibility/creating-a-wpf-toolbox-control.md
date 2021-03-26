---
title: 建立 WPF 工具箱控制項 |Microsoft Docs
description: 瞭解如何使用 WPF 工具箱控制項範本建立可散發給其他使用者的 [工具箱] 控制項。
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1dccdeb09a938b3b0bbbab803faeed538001b825
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089247"
---
# <a name="create-a-wpf-toolbox-control"></a>建立 WPF 工具箱控制項

WPF (Windows Presentation Framework) 工具箱控制項範本可讓您建立在安裝擴充功能時，自動新增至 **工具箱** 的 wpf 控制項。 本逐步解說示範如何使用範本建立可散發給其他使用者的 [ **工具箱** ] 控制項。

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-the-toolbox-control"></a>建立工具箱控制項

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>使用 WPF 工具箱控制項建立擴充功能

1. 建立名為的 VSIX 專案 `MyToolboxControl` 。 您可以藉由搜尋 "vsix"，在 [ **新增專案** ] 對話方塊中找到 VSIX 專案範本。

2. 當專案開啟時，加入名為的 **WPF 工具箱控制項** 專案範本 `MyToolboxControl` 。 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**加入新專案**] 對話方塊中，移至 [ **Visual c #** 擴充性]，  >  然後選取 [ **WPF 工具箱控制項**]。 在視窗底部的 [ **名稱** ] 欄位中，將命令檔名稱變更為 *MyToolboxControl .cs*。

    方案現在包含使用者控制項、將 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> 控制項新增至 **工具箱** 的，以及用於部署的 VSIX 資訊清單中的 **VisualStudio. ToolboxControl** 資產專案。

#### <a name="to-create-the-control-ui"></a>建立控制項 UI

1. 在設計工具中開啟 *MyToolboxControl。*

    設計工具會顯示包含了 <xref:System.Windows.Controls.Button> 控制項的 <xref:System.Windows.Controls.Grid> 控制項。

2. 排列格線版面配置。 當您選取 <xref:System.Windows.Controls.Grid> 控制項時，藍色控制列會出現在方格的上邊緣和左邊緣。 您可以按一下橫條，將資料列和資料行加入方格中。

3. 將子控制項新增至方格。 您可以將子控制項從 [ **工具箱** ] 拖曳至方格的某個區段，或 `Grid.Row` 在 XAML 中設定其和屬性，藉以放置子控制項 `Grid.Column` 。 下列範例會在方格的頂端資料列上加入兩個標籤，並在第二個數據列上加上一個按鈕。

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>重新命名控制項

 根據預設，您的控制項會以 **MyToolboxControl** 的形式出現在 [**工具箱**] 中，名為 **MyToolboxControl. MyToolboxControl** 的群組中。 您可以在 *MyToolboxControl* 中變更這些名稱。

1. 在程式碼視圖中開啟 *MyToolboxControl* 。

2. 找出 `MyToolboxControl` 類別，並將它重新命名為 TestControl。  (最快的方法是重新命名類別，然後從內容功能表中選取 [ **重新命名** ]，然後完成步驟。  (如需 **重新命名** 命令的詳細資訊，請參閱 [重新命名重構 (c # )](../ide/reference/rename.md)。 ) 

3. 移至 `ProvideToolboxControl` 屬性，並將第一個參數的值變更為 **Test**。 這是將在 [ **工具箱**] 中包含控制項的組名。

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

 當您對專案進行偵錯工具時，您應該會在 Visual Studio 的實驗實例的 [ **工具箱** ] 中找到所安裝的控制項。

### <a name="to-build-and-test-the-control"></a>建置和測試控制項

1. 重建專案並開始進行調試。

2. 在 Visual Studio 的新執行個體中建立 WPF 應用程式專案。 請確定 XAML 設計工具已開啟。

3. 在 [工具箱]  中尋找控制項，並將它拖曳至設計介面。

4. 開始進行 WPF 應用程式的偵錯工具。

5. 確認您的控制項已出現。

### <a name="to-deploy-the-control"></a>部署內容

1. 建立測試過的專案之後，您可以在專案的 * \bin\debug 資料夾中找到 *.vsix 檔案。* \*

2. 您可以按兩下 *.vsix* 檔案並遵循安裝程式，將它安裝在本機電腦上。 若要卸載控制項，請移至 [**工具**  >  **擴充功能和更新**]，並尋找控制項延伸模組，然後按一下 [**卸載**]。

3. 將 *.vsix* 檔案上傳至網路或網站。

    如果您將檔案上傳至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)網站，其他使用者可以使用  >  Visual Studio 中的工具 **擴充功能和更新** 來線上尋找並安裝該控制項。
