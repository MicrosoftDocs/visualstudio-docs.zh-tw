---
title: 建立 WPF 工具箱控制件 |微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
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
ms.openlocfilehash: c1400efb0095760bf1cee302dd33dcf6ebb90152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739576"
---
# <a name="create-a-wpf-toolbox-control"></a>建立 WPF 工具箱控制項

以 WPF(Windows 展示框架)工具箱控制樣本,您可以創建在安裝擴充名時自動添加到**工具箱**中的 WPF 控制件。 本演練演示如何使用範本創建可分發給其他使用者**的工具箱**控件。

從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-the-toolbox-control"></a>建立工具箱控制項

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>使用 WPF 工具箱控制器

1. 創建名為的`MyToolboxControl`VSIX 專案。 您可以通過搜尋"vsix"在 **"新項目**"對話框中找到 VSIX 專案範本。

2. 打開專案時,添加名為`MyToolboxControl`**的 WPF 工具箱控制**項範本。 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 在 **'新增新項目'** 對話框中,跳到**視覺化 C#** > **可擴充性**並選擇**WPF 工具箱控制件**。 在視窗底部的**名稱「 欄**位中」,將指令檔名變更為*MyToolboxControl.cs*。

    該解決方案現在包含一個使用者控件,一`ProvideToolboxControlAttribute`<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>個將控制項添加到**工具箱**,以及**Microsoft.VisualStudio.Toolbox控制**資產條目,用於部署。

#### <a name="to-create-the-control-ui"></a>建立控制者介面

1. 在設計器中打開*MyToolboxControl.xaml。*

    設計工具會顯示包含了 <xref:System.Windows.Controls.Button> 控制項的 <xref:System.Windows.Controls.Grid> 控制項。

2. 排列網格佈局。 選擇<xref:System.Windows.Controls.Grid>控制項時,藍色控制列將顯示在網格的頂部和左邊緣。 您可以通過按一下條形來向網格添加行和列。

3. 將子控制項添加到網格。 可以通過將子控件從**工具箱**拖動到網格的一部分,或者通過在 XAML 中設置其`Grid.Row`和`Grid.Column`屬性來定位子控制件。 下面的示例在網格的頂行上添加兩個標籤,在第二行上添加一個按鈕。

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>重新命名控制項

 預設情況下,您的控制項會顯示在名為**MyToolboxControl.MyToolbox 控制**群組中的 **「我的工具箱控制」工具箱中**。 **Toolbox** 您可以在*MyToolboxControl.xaml.cs*檔中更改這些名稱。

1. 在代碼檢視中打開*MyToolboxControl.xaml.cs。*

2. 查找類`MyToolboxControl`並將其重命名為測試控制。 (執行此操作的最快方法是重命名類,然後從上下文菜單中選擇 **"重新命名**"並完成這些步驟。 ( 有關**重新命名**指令的詳細資訊,請參閱[重新命名重構 (C#)](../ide/reference/rename.md)。

3. 轉到`ProvideToolboxControl`屬性 並將第一個參數的值更改為 **「測試**」。 這是將在**工具箱**中包含控制項的元件名稱。

    產生的代碼應如下所示:

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

## <a name="build-test-and-deployment"></a>組建、測試及部署

 除錯專案時,應找到安裝在 Visual Studio 實驗實例**工具箱**中的控制項。

### <a name="to-build-and-test-the-control"></a>建置和測試控制項

1. 重建專案並開始調試。

2. 在 Visual Studio 的新執行個體中建立 WPF 應用程式專案。 確保 XAML 設計器處於打開狀態。

3. 在 [工具箱] **** 中尋找控制項，並將它拖曳至設計介面。

4. 開始調試 WPF 應用程式。

5. 驗證控件是否出現。

### <a name="to-deploy-the-control"></a>部署內容

1. 產生測試專案後,您可以在專案的 _bin_除\*錯 資料夾中找到 *.vsix*檔。

2. 您可以透過雙擊 *.vsix*檔案並遵循安裝過程將其安裝在本地電腦上。 要卸載控制項,請轉到 **「工具** > **擴展」和「更新」** 並查找控制項延伸,然後單擊「**卸載**」。

3. 將 *.vsix*檔上載到網路或網站。

    如果將檔上載到[可視化工作室應用商店](https://marketplace.visualstudio.com/)網站,其他使用者可以使用 Visual Studio 中的**工具** > **擴展和更新**連線查找控制項並安裝它。
