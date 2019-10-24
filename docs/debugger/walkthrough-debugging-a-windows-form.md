---
title: 調試 Windows Form |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 701d156d5fdc23a5e98ac1de43c1882f3065171e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728323"
---
# <a name="walkthrough-debugging-a-windows-form"></a>逐步解說：偵錯 Windows Form
Windows Form 是其中一個最常見的受控應用程式。 Windows Form 會建立標準 Windows 應用程式。 您可以使用 Visual Basic、 C#或C++來完成本逐步解說。

 首先，您必須關閉任何已開啟的解決方案。

### <a name="to-prepare-for-this-walkthrough"></a>準備此逐步教學

- 如果您已經開啟開啟的方案，請將它關閉。 （**在 [檔案] 功能表上**，選取 [**關閉解決方案**]）。

## <a name="create-a-new-windows-form"></a>建立新的 Windows Form
 接下來，您將建立新的 Windows Form。

#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>若要建立此逐步解說的 Windows form

1. 在 [檔案 **] 功能表上，選擇 [** **新增**]，然後按一下 [**專案**]。

     [ **新增專案** ] 對話方塊隨即出現。

2. 在 [專案類型] 窗格中，開啟 [ **Visual Basic**]、[**視覺C#效果**] 或 [**視覺效果C++**  ] 節點，然後

    1. 針對 Visual Basic 或視覺C#效果，請選取 [ **Windows 桌面** > **windows Form 應用程式**]。

    2. 針對 [ C++視覺效果]，選取 [ **Windows 桌面應用程式**]。

3. 在 [**名稱**] 方塊中，為專案指定唯一的名稱（例如，Walkthrough_SimpleDebug）。

4. 按一下 [確定]。

     Visual Studio 會建立新的專案，並在 [Windows Forms 設計工具] 中顯示新的表單。 如需詳細資訊，請參閱[Windows Form 設計工具](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\))。

5. 在 [ **View** ] 功能表上，選取 [**工具箱**]。

     [工具箱] 便會開啟。 如需詳細資訊，請參閱[工具箱](../ide/reference/toolbox.md)。

6. 在 [工具箱] 中，按一下 [**按鈕**] 控制項，並將控制項拖曳至表單設計介面。 將按鈕放在表單上。

7. 在 [工具箱] 中，按一下 [ **TextBox** ] 控制項，並將控制項拖曳至表單設計介面。 將**TextBox**放在表單上。

8. 在表單設計介面上，按兩下 [] 按鈕。

     這會帶您前往 [字碼頁]。 游標應該在 `button1_Click` 中。

10. 在 `button1_Click` 函式中，新增下列程式碼：

    ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

11. 在 [建置] 功能表上，選取 [建置方案]。

     專案應該會建置而無錯誤。

## <a name="debug-your-form"></a>對您的表單進行 Debug
 現在，您已準備好開始進行調試。

#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>若要對此逐步解說所建立的 Windows Form 進行偵錯工具

1. 在 [來源] 視窗中，按一下與您新增的文字位於同一行的左邊界：

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

     會出現一個紅點，並且該行上的文字會以紅色反白顯示。 紅點表示中斷點。 如需詳細資訊，請參閱[中斷點](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)。 當您在偵錯工具下執行應用程式時，偵錯工具會在遇到程式碼的位置中斷執行。 接著您就可以檢視應用程式的狀態並對它進行偵錯。

    > [!NOTE]
    > 您也可以在任何一行程式碼上按一下滑鼠右鍵，指向 [**中斷點**]，然後按一下 [**插入中斷點**]，在該行上加入中斷點。

2. 在 [偵錯] 功能表上選擇 [啟動]。

     Windows Form 開始執行。

3. 在 [Windows] 表單上，按一下您新增的按鈕。

     在 Visual Studio 中，這會帶您前往在 [字碼頁] 上設定中斷點的那一行。 這行程式碼應該會以黃色反白顯示。 您現在可以檢視應用程式中的變數並控制其執行。 您的應用程式現在已停止執行，正在等候您的動作。

4. 在 [**調試**] 功能表上依序選擇 [ **Windows** **]、[監看式] 和 [** **Watch1**]。

5. 在 [ **Watch1** ] 視窗中，按一下空白資料列。 在 [**名稱**] 欄中，輸入 `textBox1.Text` （如果您使用 Visual Basic 或C#視覺效果）或 `textBox1->Text` （如果您C++使用的是），然後按 enter。

     [ **Watch1** ] 視窗會以引號顯示此變數的值，如下所示：

    `""`

6. 在 [偵錯] 功能表上，選擇 [逐步執行]。

     TextBox1 的值。 **Watch1**視窗中的文字會變更為：

    `Button was clicked!`

7. 在 [**調試**程式] 功能表上，選擇 [**繼續**] 繼續對程式進行偵測。

8. 在 Windows Form 上，再次按一下 [] 按鈕。

     Visual Studio 中斷執行。

9. 按一下代表中斷點的紅點。

     這會從您的程式碼中移除中斷點。

10. 在 [偵錯] 功能表中，選擇 [停止偵錯]。

## <a name="attach-to-your-windows-form-application-for-debugging"></a>附加至您的 Windows Form 應用程式以進行偵錯工具
 在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 中，您可以將偵錯工具附加至執行中的處理序。 如果您使用 Express Edition，則不支援這項功能。

#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>附加至 Windows Form 應用程式以進行偵錯工具

1. 在您先前建立的專案中，按一下左邊界，再次在您新增的那一行設定中斷點：

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

2. 在 [**調試**] 功能表上，選取 [**啟動但不進行調試**]。

     Windows Form 會開始在 Windows 下執行，就像您按兩下它的可執行檔一樣。 未附加偵錯工具。

3. 在 [**調試**程式] 功能表上，選取 [**附加至進程**]。 （您也可以在 [**工具**] 功能表上找到此命令）。

     [附加至處理序] 對話方塊隨即出現。

4. 在 [**可用的進程**] 窗格中，在 [**處理**] 資料行中尋找進程名稱（Walkthrough_SimpleDebug .exe），然後按一下它。

5. 按一下 [**附加**] 按鈕。

6. 在您的 Windows Form 中，按一下 [僅一個] 按鈕。

     偵錯工具會在中斷點中斷執行 Windows Form。

## <a name="see-also"></a>請參閱
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
- [偵錯工具安全性](../debugger/debugger-security.md)
