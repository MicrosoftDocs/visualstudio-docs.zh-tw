---
title: 建立 Windows Forms 工具箱控制項 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 725d35d957e1b7aef285e0d666dc4ea15e5ceefd
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57872998"
---
# <a name="create-a-windows-forms-toolbox-control"></a>建立 Windows Forms 工具箱控制項
Windows Forms 工具箱控制項項目範本包含在 Visual Studio 擴充性工具 (VS SDK) 可讓您建立的控制項，會自動新增至**工具箱**安裝擴充功能時。 本主題說明如何使用範本來建立簡單的計數器控制項，您就可以散發給其他使用者。

## <a name="prerequisites"></a>必要條件
從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-windows-forms-toolbox-control"></a>建立 Windows Forms 工具箱控制項
Windows Forms 工具箱控制項範本建立未定義的使用者控制項，並提供的所有功能，才能將控制項加入**工具箱**。

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>建立使用 Windows Forms 工具箱控制項的延伸模組

1. 建立 VSIX 專案，名為`MyWinFormsControl`。 您可以找到在 VSIX 專案範本**新的專案**下方的對話方塊**Visual C#** > **擴充性**。

2. 當專案開啟時，新增**Windows Forms 工具箱控制項**名為的項目範本`Counter`。 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增** > **新項目**。 在 **加入新項目**對話方塊中，移至**Visual C#** > **擴充性**，然後選取**Windows Forms 工具箱控制項**

3. 這會將使用者控制項，新增`ProvideToolboxControlAttribute`<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>要放置在控制項**工具箱**，和**Microsoft.VisualStudio.ToolboxControl**資產部署的 VSIX 資訊清單中的項目。

### <a name="build-a-user-interface-for-the-control"></a>建置使用者介面控制項
`Counter`控制項，需要兩個子控制項：<xref:System.Windows.Forms.Label>來顯示目前的計數，和<xref:System.Windows.Forms.Button>計數重設為 0。 沒有任何其他子控制項所需的因為呼叫端會以程式設計方式遞增計數器。

#### <a name="to-build-the-user-interface"></a>建置使用者介面

1. 在 [**方案總管] 中**，按兩下*Counter.cs*在設計工具中開啟它。

2. 移除**按這裡 ！** 當您將 Windows Forms 工具箱控制項項目範本包含預設的按鈕。

3. 從**工具箱**，拖曳`Label`控制項，然後`Button`其下方的控制項至設計介面。

4. 調整 150 整體使用者控制項的大小、 50 像素為單位，並調整大小的按鈕控制項為 50，20 像素為單位。

5. 在 [**屬性**] 視窗中，設定下列值在設計介面上的控制項。

    |控制項|屬性|值|
    |-------------|--------------|-----------|
    |`Label1`|**Text**|""|
    |`Button1`|**名稱**|btnReset|
    |`Button1`|**Text**|重設|

### <a name="code-the-user-control"></a>使用者控制項的程式碼
`Counter`控制項會公開遞增計數器，此計數器會遞增，每當引發事件的方法**重設**按鈕，然後將目前的計數、 顯示文字，以及是否要顯示的三個屬性或隱藏**重設** 按鈕。 `ProvideToolboxControl` 屬性會決定 [工具箱]  顯示 `Counter` 控制項的位置。

#### <a name="to-code-the-user-control"></a>使用者控制項的程式碼

1. 按兩下表單，以開啟其 load 事件處理常式程式碼視窗中。

2. 上述事件處理常式方法中，控制項類別中建立要儲存的計數器值的字串和儲存的顯示文字，如下列範例所示的整數。

    ```csharp
    int currentValue;
    string displayText;
    ```

3. 建立下列公用屬性宣告。

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    呼叫端可以存取這些屬性，取得或設定計數器的顯示文字，以顯示或隱藏**重設** 按鈕。 呼叫端可以取得目前的唯讀值`Value`屬性，但它們不能值直接設定。

4. 將下列程式碼置於`Load`控制項事件。

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    設定**標籤**中的文字<xref:System.Windows.Forms.UserControl.Load>事件可讓載入前套用其值的目標屬性。 設定**標籤**建構函式中的文字會導致空**標籤**。

5. 建立下列公用方法，以遞增計數器。

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. 加入宣告`Incremented`控制項類別的事件。

    ```csharp
    public event EventHandler Incremented;
    ```

    呼叫端可以新增處理常式，此事件以回應變更計數器的值。

7. 返回設計檢視，然後按兩下**重設**按鈕，以產生`btnReset_Click`事件處理常式，然後在下列範例所示填入。

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. 在類別定義正上方的 `ProvideToolboxControl` 屬性宣告中，將第一個參數的值從 `"MyWinFormsControl.Counter"` 變更為 `"General"`。 這會設定主控 [工具箱] 控制項的項目群組名稱。

    下列範例會顯示 `ProvideToolboxControl` 屬性和調整過的類別定義。

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>測試控制項
 若要測試**工具箱**控制第一次在開發環境中進行測試，然後在已編譯的應用程式中進行測試。

#### <a name="to-test-the-control"></a>測試控制項

1. 請按 **F5**。

    這會建置專案，並開啟第二個安裝了控制項的 Visual Studio 的實驗性執行個體。

2. 在 Visual Studio 的實驗性執行個體，建立**Windows Forms 應用程式**專案。

3. 在 **方案總管**，按兩下*Form1.cs*開啟設計工具中，如果它尚未開啟。

4. 在 **工具箱**，則`Counter`控制項應該顯示在**一般**一節。

5. 拖曳`Counter`控制項至表單，然後加以選取。 `Value`， `Message`，並`ShowReset`屬性會顯示在**屬性**視窗中的，以及繼承自屬性<xref:System.Windows.Forms.UserControl>。

6. 將 `Message` 屬性設定為 `Count:`。

7. 拖曳<xref:System.Windows.Forms.Button>控制項至表單，並再設定名稱和文字屬性的按鈕`Test`。

8. 按兩下 button 以開啟*Form1.cs*中程式碼檢視，並建立 click 處理常式。

9. 在 click 處理常式呼叫`counter1.Increment()`。

10. 在建構函式，呼叫後面`InitializeComponent`，型別`counter1``.``Incremented +=`，然後按 **索引標籤** 兩次。

    Visual Studio 產生的表單層次處理常式`counter1.Incremented`事件。

11. 反白顯示`Throw`陳述式中的事件處理常式，型別`mbox`，然後按 **索引標籤** 兩次，以從 mbox 程式碼片段中產生一個訊息方塊。

12. 在下一行中，新增下列`if` / `else`區塊來設定的可見性**重設** 按鈕。

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. 請按 **F5**。

    表單隨即開啟。 `Counter`控制項會顯示下列文字。

    **計數：0**

14. 按一下 [測試] 。

    計數器遞增和 Visual Studio 會顯示訊息方塊。

15. 關閉訊息方塊。

    **重設**按鈕就會消失。

16. 按一下 **測試**直到在計數器達到**5**關閉訊息方塊的每一次。

    **重設**按鈕會再度出現。

17. 按一下 [重設] 。

    此計數器會重設為**0**。

## <a name="next-steps"></a>後續步驟
當您建置**工具箱**控制項，Visual Studio 會建立名為的檔案*ProjectName.vsix*您專案的 \bin\debug\ 資料夾中。 您可以將控制項部署上傳 *.vsix*檔案到網路或網站。 當使用者在開啟 *.vsix*是安裝檔案，該控制項，並將其加入 Visual Studio**工具箱**使用者的電腦上。 或者，您可以上傳 *.vsix*的檔案[Visual Studio Marketplace](https://marketplace.visualstudio.com/) ，讓使用者可以瀏覽來尋找它**工具** >  **延伸模組和更新**對話方塊。

## <a name="see-also"></a>另請參閱
- [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)
- [建立 WPF 工具箱控制項](../extensibility/creating-a-wpf-toolbox-control.md)
- [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)
- [Windows Form 控制項開發的基本概念](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
