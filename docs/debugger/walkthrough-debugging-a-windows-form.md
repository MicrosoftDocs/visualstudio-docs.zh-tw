---
title: 偵錯 Windows Form |Microsoft Docs
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d0e04b407303b1d6f98862fdef36bb8228fd780
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851965"
---
# <a name="walkthrough-debugging-a-windows-form"></a>逐步解說：偵錯 Windows Form
Windows 表單是其中一個最常見的受管理應用程式。 在 Windows Form 建立標準的 Windows 應用程式。 您可以完成此逐步解說使用 Visual Basic 中， C#，或 c + +。  
  
 首先，您必須先關閉任何開啟的方案。  
  
### <a name="to-prepare-for-this-walkthrough"></a>準備此逐步教學  
  
-   如果您已經開啟方案，請將它關閉。 (在**檔案**功能表上，選取**關閉方案**。)  
  
## <a name="create-a-new-windows-form"></a>建立新的 Windows Form  
 接下來，您將建立新的 Windows Form。  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>若要建立 Windows 表單，在此逐步解說  
  
1.  在 **檔案**功能表上，選擇**新增**，按一下 **專案**。  
  
     [ **新增專案** ] 對話方塊隨即出現。  
  
2.  在 [專案類型] 窗格中，開啟**Visual Basic**，**視覺化C#** ，或**Visual c + +** 節點，然後  
  
    1.  Visual Basic 或 Visual C#，選取**Windows 桌面** > **Windows 表單應用程式**。  
  
    2.  Visual c + + 中，選取**Windows 桌面應用程式**。  
  
3.  在 **名稱**方塊中，為專案指定唯一的名稱 (例如 Walkthrough_SimpleDebug)。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
     Visual Studio 會建立新的專案，並在 Windows Form 設計工具中顯示新的表單。 如需詳細資訊，請參閱 < [Windows Form 設計工具](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\))。  
  
5.  在 **檢視**功能表上，選取**工具箱**。  
  
     [工具箱] 便會開啟。 如需詳細資訊，請參閱[工具箱](../ide/reference/toolbox.md)。  
  
6.  在 工具箱 中，按一下 **按鈕**控制項，將控制項拖曳至表單的設計介面。 將按鈕放在表單上。  
  
7.  在 [工具箱] 中，按一下**TextBox**控制項，將控制項拖曳至表單的設計介面。 卸除**TextBox**表單上。  
  
8. 表單設計介面上，按兩下按鈕。  
  
     這會帶您前往字碼頁。 資料指標應該在`button1_Click`。  
  
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
  
## <a name="debug-your-form"></a>偵錯您的表單  
 現在，您已準備好開始偵錯。  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>若要偵錯此逐步解說中建立的 Windows Form  
  
1.  在 [來源] 視窗中，按一下您所加入的文字的同一行的左邊的界：  
  
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
    >  您也可以以滑鼠右鍵按一下任何一行程式碼，指向**中斷點**，然後按一下**插入中斷點**這一行加入中斷點。  
  
2.  在 [偵錯] 功能表上選擇 [啟動]。  
  
     Windows Form 會開始執行。  
  
3.  Windows 在表單上，按一下 [新增] 按鈕。  
  
     在 Visual Studio 中，這會帶您前往的行，在程式碼 頁面上設定中斷點。 這行程式碼應該會以黃色反白顯示。 您現在可以檢視應用程式中的變數並控制其執行。 您的應用程式現在已停止執行，等待來自您的動作。  
  
4.  在上**偵錯** 功能表中，選擇**Windows**，然後**監看式**，然後按一下**監看式 1**。  
  
5.  在 **監看式 1**視窗中，按一下空白資料列。 在 **名稱**資料行中輸入`textBox1.Text`(如果您使用 Visual Basic 或 Visual C#) 或`textBox1->Text`（如果您使用 c + +），然後按 ENTER 鍵。  
  
     **監看式 1**視窗會顯示此變數的值以引號括起來：  
  
    `""`  
 
6.  在 [偵錯] 功能表上，選擇 [逐步執行]。  
  
     TextBox1.Text 變更的值**監看式 1**視窗：  
  
    `Button was clicked!`  
  
7.  在 **偵錯**功能表上，選擇**繼續**繼續偵錯您的程式。  
  
8.  在 Windows 表單中，再按一下 [] 按鈕。  
  
     Visual Studio 會中斷執行一次。  
  
9. 按一下紅點表示中斷點。  
  
     這會從您的程式碼移除中斷點。  
  
10. 在 [偵錯] 功能表中，選擇 [停止偵錯]。  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>附加至您的 Windows Form 應用程式進行偵錯  
 在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 中，您可以將偵錯工具附加至執行中的處理序。 如果您使用的 Express 版本，不支援這項功能。  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>若要附加至偵錯 Windows Form 應用程式  
  
1.  在您先前建立的專案中，按一下左邊界來一次一次在您加入的行中設定中斷點：  
  
     ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";   
  
2.  On the **Debug** menu, select **Start Without Debugging**.  
  
     The Windows Form starts running under Windows, just as if you had double-clicked its executable. The debugger is not attached.  
  
3.  On the **Debug** menu, select **Attach to Process**. (This command is also available on the **Tools** menu.)  
  
     The **Attach to Process** dialog box appears.  
  
4.  In the **Available Processes** pane, find the process name (Walkthrough_SimpleDebug.exe) in the **Process** column and click it.  
  
5.  Click the **Attach** button.  
  
6.  In your Windows Form, click the one and only button.  
  
     The debugger breaks execution of the Windows Form at the breakpoint.  
  
## See Also  
 [Debugging Managed Code](../debugger/debugging-managed-code.md)   
 [Debugger Security](../debugger/debugger-security.md)