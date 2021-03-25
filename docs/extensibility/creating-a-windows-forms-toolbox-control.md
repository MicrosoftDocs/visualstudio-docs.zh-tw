---
title: 建立 Windows Forms 工具箱控制項 |Microsoft Docs
description: 本逐步解說將示範如何使用 Windows Forms 工具箱控制項範本，以使用 Visual Studio SDK 來建立簡單的計數器控制項。
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42dcf30e7c31880357bb95e3858a2c70aa59f174
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089325"
---
# <a name="create-a-windows-forms-toolbox-control"></a>建立 Windows Forms 工具箱控制項

包含在 Visual Studio 擴充性工具 (VS SDK) 的 Windows Forms 工具箱控制項專案範本，可讓您建立在安裝擴充功能時自動新增的 [ **工具箱** ] 控制項。 本逐步解說示範如何使用範本建立可散發給其他使用者的簡單計數器控制項。

## <a name="prerequisites"></a>必要條件

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-the-toolbox-control"></a>建立工具箱控制項

Windows Forms 的 [工具箱控制項] 範本會建立未定義的使用者控制項，並提供將控制項加入 [ **工具箱**] 所需的所有功能。

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>使用 Windows Forms 工具箱控制項建立擴充功能

1. 建立名為的 VSIX 專案 `MyWinFormsControl` 。 您可以藉由搜尋 "vsix"，在 [ **新增專案** ] 對話方塊中尋找 VSIX 專案範本。

2. 當專案開啟時，加入名為的 **Windows Forms 工具箱控制項** 專案範本 `Counter` 。 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**加入新專案**] 對話方塊中，移至 [ **Visual c #** 擴充性]，  >  然後選取 **Windows Forms 工具箱控制項**

3. 這會新增使用者控制項、將 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> 控制項放在 [ **工具箱**] 中，以及在 VSIX 資訊清單中 **VisualStudio ToolboxControl** 資產專案以進行部署。

### <a name="build-a-user-interface-for-the-control"></a>建立控制項的使用者介面

`Counter`控制項需要兩個子控制項：用 <xref:System.Windows.Forms.Label> 來顯示目前的計數，以及將 <xref:System.Windows.Forms.Button> 計數重設為0。 不需要其他子控制項，因為呼叫端會以程式設計方式遞增計數器。

#### <a name="to-build-the-user-interface"></a>建置使用者介面

1. 在 **方案總管** 中，按兩下 [ *Counter* ]，在設計工具中開啟它。

2. 移除 **這裡的 Click！** 當您加入 Windows Forms 工具箱控制項專案範本時，預設會包含的按鈕。

3. 將控制項從 [ **工具箱**] 拖曳 `Label` 至設計介面，然後將它放在 `Button` 其下方的控制項。

4. 將整體使用者控制項的大小調整為150、50圖元，然後將按鈕控制項的大小調整為 50 20 圖元。

5. 在 [ **屬性** ] 視窗中，設定設計介面上控制項的下列值。

    |控制|屬性|值|
    |-------------|--------------|-----------|
    |`Label1`|**Text**|""|
    |`Button1`|**名稱**|btnReset|
    |`Button1`|**Text**|重設|

### <a name="code-the-user-control"></a>撰寫使用者控制項的程式碼

`Counter`控制項將公開方法來遞增計數器、每當計數器遞增時引發的事件、**重設** 按鈕，以及用來儲存目前計數的三個屬性、顯示文字，以及是否要顯示或隱藏 **重設** 按鈕。 `ProvideToolboxControl` 屬性會決定 [工具箱]  顯示 `Counter` 控制項的位置。

#### <a name="to-code-the-user-control"></a>撰寫使用者控制項的程式碼

1. 按兩下表單，以在程式碼視窗中開啟它的 load 事件處理常式。

2. 在事件處理常式方法上方的控制項類別中，建立一個整數來儲存計數器值和一個字串來儲存顯示文字，如下列範例所示。

    ```csharp
    int currentValue;
    string displayText;
    ```

3. 建立下列公用屬性宣告。

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    呼叫端可以存取這些屬性來取得和設定計數器的顯示文字，以及顯示或隱藏 [ **重設** ] 按鈕。 呼叫端可以取得唯讀屬性的目前值 `Value` ，但無法直接設定該值。

4. 將下列程式碼放在 `Load` 控制項的事件中。

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    在事件中設定 **標籤** 文字 <xref:System.Windows.Forms.UserControl.Load> ，可讓目標屬性在套用值之前載入。 在函式中設定 **標籤** 文字會導致空的 **標籤**。

5. 建立下列公用方法以遞增計數器。

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. 將事件的宣告加入 `Incremented` 至控制項類別。

    ```csharp
    public event EventHandler Incremented;
    ```

    呼叫端可以將處理常式加入至這個事件，以回應計數器值的變更。

7. 返回 [設計檢視]，然後按兩下 [ **重設** ] 按鈕以產生 `btnReset_Click` 事件處理常式。 然後，將它填入，如下列範例所示。

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. 在類別定義正上方的 `ProvideToolboxControl` 屬性宣告中，將第一個參數的值從 `"MyWinFormsControl.Counter"` 變更為 `"General"`。 這會設定主控 [工具箱] 控制項的項目群組名稱。

    下列範例會顯示 `ProvideToolboxControl` 屬性和調整過的類別定義。

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>測試控制項

 若要測試 [ **工具箱** ] 控制項，請先在開發環境中測試，然後在編譯的應用程式中進行測試。

#### <a name="to-test-the-control"></a>測試控制項

1. 按 **F5** **啟動調試**。

    此命令會建立專案，並開啟已安裝控制項之 Visual Studio 的第二個實驗實例。

2. 在 Visual Studio 的實驗實例中，建立 **Windows Forms 應用程式** 專案。

3. 在 **方案總管** 中，按兩下 [form1.vb *]，在* 設計工具中開啟它（如果尚未開啟）。

4. 在 [ **工具箱**] 中， `Counter` 控制項應該會顯示在 [ **一般** ] 區段中。

5. 將 `Counter` 控制項拖曳至表單，然後選取它。 `Value`、 `Message` 和 `ShowReset` 屬性會顯示在 [**屬性**] 視窗中，以及繼承自的屬性 <xref:System.Windows.Forms.UserControl> 。

6. 將 `Message` 屬性設定為 `Count:`。

7. 將 <xref:System.Windows.Forms.Button> 控制項拖曳至表單，然後將按鈕的 [名稱] 和 [text] 屬性設定為 `Test` 。

8. 按兩下按鈕以在程式碼視圖中開啟 *Form1* ，然後建立 click 處理常式。

9. 在按一下處理常式中，呼叫 `counter1.Increment()` 。

10. 在函式函數中，在呼叫之後， `InitializeComponent` 輸入， `counter1``.``Incremented +=` 然後按 **tab** 鍵兩次。

    Visual Studio 會產生事件的表單層級處理常式 `counter1.Incremented` 。

11. 反白顯示 `Throw` 事件處理常式中的語句，輸入 `mbox` ，然後按 **tab** 鍵兩次，以從 .mbox 程式碼片段產生訊息方塊。

12. 在下一行中，新增下列 `if` / `else` 區塊來設定 [**重設**] 按鈕的可見度。

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. 按 **F5**。

    表單隨即開啟。 `Counter`控制項會顯示下列文字。

    **計數：0**

14. 選取 [測試]。

    計數器會遞增，Visual Studio 會顯示訊息方塊。

15. 關閉訊息方塊。

    [ **重設** ] 按鈕會消失。

16. 選取 [ **測試** ]，直到計數器每次到達 **5** 次之後，再關閉訊息方塊。

    **重設** 按鈕隨即出現。

17. 選取 [重設]。

    計數器會重設為 **0**。

## <a name="next-steps"></a>下一步

當您建立 [**工具箱**] 控制項時，Visual Studio 會在專案的 \bin\debug\ 資料夾中建立名為專案名稱的檔案 *。* 您可以將 *.vsix* 檔案上傳至網路或網站，以部署控制項。 當使用者開啟 *.vsix* 檔案時，控制項就會安裝並新增至使用者電腦上的 Visual Studio **工具箱** 。 或者，您可以將 *.vsix* 檔案上傳至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ，讓使用者可以在 [**工具**  >  **擴充功能和更新**] 對話方塊中流覽，以找到該檔案。

## <a name="see-also"></a>另請參閱

- [延伸 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)
- [建立 WPF 工具箱控制項](../extensibility/creating-a-wpf-toolbox-control.md)
- [延伸 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)
- [Windows Forms 控制開發的基本概念](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
