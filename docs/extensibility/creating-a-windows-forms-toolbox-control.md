---
title: 建立 Windows 表單工具箱控制件 |微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7e7749302252c5d56f21c58de9b6ac23f898572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739578"
---
# <a name="create-a-windows-forms-toolbox-control"></a>建立 Windows 表單工具箱控制項

Visual Studio 擴充工具 (VS SDK) 中包含的 Windows 窗體工具箱控制項專案樣本允許您創建**工具箱**控制項,該控制檔在安裝擴充時會自動新增。 本演練演示如何使用範本創建可分發給其他用戶的簡單計數器控制項。

## <a name="prerequisites"></a>Prerequisites

從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-the-toolbox-control"></a>建立工具箱控制項

Windows 表單工具箱控制項樣本建立未定義的使用者控制項,並提供將控制項添加到**工具箱**所需的所有功能。

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>使用 Windows 表單工具箱控制件建立副檔名

1. 創建名為的`MyWinFormsControl`VSIX 專案。 您可以通過搜尋"vsix"在 **"新項目**"對話框中找到 VSIX 專案範本。

2. 打開專案時,添加名為的`Counter`Windows**窗體工具箱控制項**樣本。 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 在 **'新增新項目'** 對話框中,轉到**視覺化 C#** > **可擴充性**並選擇**Windows 窗體工具箱控制項**

3. 這將添加使用者控件,一個`ProvideToolboxControlAttribute`<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>將控制項放在**工具箱**中,以及**Microsoft.VisualStudio.Toolbox 控制**資產項目在 VSIX 清單中進行部署。

### <a name="build-a-user-interface-for-the-control"></a>為控制程式建構使用者介面

該`Counter`控制項需要兩個子控制項<xref:System.Windows.Forms.Label>: 一個用於顯示當前計數<xref:System.Windows.Forms.Button>,和將計數重置為 0。 不需要其他子控件,因為調用方將以程式設計方式增加計數器。

#### <a name="to-build-the-user-interface"></a>建置使用者介面

1. 在**解決方案資源管理器**中,按兩下*Counter.cs*在設計器中打開它。

2. 刪除 **「按下此處」!** 添加 Windows 窗體工具箱控制項項樣本時預設包含的按鈕。

3. 從**工具箱**中,拖動`Label`控件 ,`Button`然後將其下方 的控件拖動到設計圖面。

4. 將使用者整體控制件的大小調整到 150、50 像素,並將按鈕控制項的大小調整到 50、20 圖元。

5. 在 **「屬性」** 視窗中,為設計圖面上的控制項設定以下值。

    |控制|屬性|值|
    |-------------|--------------|-----------|
    |`Label1`|**Text**|""|
    |`Button1`|**名稱**|btnReset|
    |`Button1`|**Text**|重設|

### <a name="code-the-user-control"></a>編寫使用者控制程式的代碼

此`Counter`控制項會公開一個方法以遞增計數器、每當計數器增加時引發的事件、**一個「重置」** 按鈕以及儲存目前的計數、顯示文字以及是否顯示或隱藏 **「重置」** 按鈕的三個屬性。 `ProvideToolboxControl` 屬性會決定 [工具箱] **** 顯示 `Counter` 控制項的位置。

#### <a name="to-code-the-user-control"></a>編寫使用者控制程式的代碼

1. 按兩下單單以在程式碼視窗中打開其載入事件處理程式。

2. 在事件處理程式方法的上方,在控件類中創建一個整數來存儲計數器值和一個字串來存儲顯示文本,如下例所示。

    ```csharp
    int currentValue;
    string displayText;
    ```

3. 創建以下公共財產聲明。

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

    呼叫者可以存取這些屬性以取得和設定計數器的顯示文字,並顯示或隱藏 **「重置」** 按鈕。 調用方可以獲取唯`Value`讀屬性的當前值,但不能直接設置該值。

4. 將以下代碼放在控制項的`Load`事件中。

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    在<xref:System.Windows.Forms.UserControl.Load>事件中設定**Label**文本可使目標屬性在應用其值之前載入。 在建構函數中設定 **「標籤**」文本將導致**標籤**為空。

5. 創建以下公共方法以增加計數器。

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. 向控制項類添加`Incremented`事件的聲明。

    ```csharp
    public event EventHandler Incremented;
    ```

    呼叫方可以向此事件添加處理程式以回應計數器值的更改。

7. 返回到設計檢視並按兩下 **「重置**」按鈕以`btnReset_Click`生成 事件處理程式,然後填寫它,如以下示例所示。

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. 在類別定義正上方的 `ProvideToolboxControl` 屬性宣告中，將第一個參數的值從 `"MyWinFormsControl.Counter"` 變更為 `"General"`。 這會設定主控 [工具箱] **** 控制項的項目群組名稱。

    下列範例會顯示 `ProvideToolboxControl` 屬性和調整過的類別定義。

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>測試控制項

 要測試**工具箱**控件,請先在開發環境中測試它,然後在編譯的應用程式中對其進行測試。

#### <a name="to-test-the-control"></a>測試控制項

1. 以**F5** **以開始除錯**。

    此命令生成專案並打開已安裝控制項的 Visual Studio 的第二個實驗實例。

2. 在可視化工作室的實驗實例中,創建**Windows 窗體應用程式**專案。

3. 在**解決方案資源管理器**中,按兩下*Form1.cs*在設計器中打開它(如果尚未打開)。

4. 在**工具箱**中`Counter`,控制項應顯示在 **「常規」** 部分中。

5. 將`Counter`控件拖動到窗體中,然後選擇它。 `Message``Value`<xref:System.Windows.Forms.UserControl>屬性會顯示在 **「屬性」** 視窗中, 以及從繼承的屬性 。 `ShowReset`

6. 將 `Message` 屬性設為 `Count:`。

7. 將<xref:System.Windows.Forms.Button>控制器拖曳到表單,然後會按鈕的名稱與文字屬性設定`Test`為 。

8. 按兩下按鈕以在代碼檢視中打開*Form1.cs*並創建單擊處理程式。

9. 在按一下處理程式中,呼`counter1.Increment()`叫 。

10. 在構造函數中,在`InitializeComponent`調用 後鍵`counter1``.``Incremented +=`入 ,然後按**Tab**兩次。

    Visual Studio`counter1.Incremented`為 事件生成表單級處理程式。

11. 突顯事件`Throw`處理程式中的語句,鍵`mbox`入 ,然後按**Tab**兩次從 mbox 代碼段生成消息框。

12. 在下一行上,`if`/`else`添加以下塊以設置 **「重置」** 按鈕的可見性。

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. 按 **F5**。

    窗體將打開。 該`Counter`控件顯示以下文本。

    **計數: 0**

14. 按一下 [ **測試**]。

    計數器增量和可視化工作室顯示一個消息框。

15. 關閉消息框。

    **"重置**"按鈕將消失。

16. 按下 **「測試**」,直到計數器每次達到**5**個關閉消息框。

    **"重置"** 按鈕重新出現。

17. 按一下 [重設]****。

    計數器重置為**0**。

## <a name="next-steps"></a>後續步驟

生成**工具箱**控制項時,Visual Studio 會在專案的 [bin_調試] 資料夾中創建名為*ProjectName.vsix*的檔。 通過將 *.vsix*檔上傳到網路或網站,可以部署控制項。 當使用者打開 *.vsix*檔時,將安裝該控制項並將其添加到使用者電腦上的 Visual Studio**工具箱**中。 或者,您可以將 *.vsix*檔上傳到[可視化工作室應用商店](https://marketplace.visualstudio.com/),以便使用者可以通過在 **「工具** > **擴展和更新**」對話框中流覽來找到它。

## <a name="see-also"></a>另請參閱

- [擴展視覺工作室的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)
- [建立 WPF 工具箱控制項](../extensibility/creating-a-wpf-toolbox-control.md)
- [擴展視覺工作室的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)
- [Windows 表單控制式開發基礎知識](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
