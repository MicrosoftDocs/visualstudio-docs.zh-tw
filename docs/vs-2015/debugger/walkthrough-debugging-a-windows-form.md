---
title: 逐步解說： 偵錯 Windows Form |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
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
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53bd1af80b9d86b6a8e22d7bdfd79cee92554a15
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219649"
---
# <a name="walkthrough-debugging-a-windows-form"></a>逐步解說：偵錯 Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 表單是其中一個最常見的受管理應用程式。 在 Windows Form 建立標準的 Windows 應用程式。 您可以完成此逐步解說使用 Visual Basic、 C# 或 c + +。  
  
 首先，您必須先關閉任何開啟的方案。  
  
### <a name="to-prepare-for-this-walkthrough"></a>準備此逐步教學  
  
-   如果您已經開啟方案，請將它關閉。 (在**檔案**功能表上，選取**關閉方案**。)  
  
## <a name="create-a-new-windows-form"></a>建立新的 Windows Form  
 接下來，您將建立新的 Windows Form。  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>若要建立 Windows 表單，在此逐步解說  
  
1.  在 **檔案**功能表上，選擇**新增**，按一下 **專案**。  
  
     [ **新增專案** ] 對話方塊隨即出現。  
  
2.  在 [專案類型] 窗格中，開啟**Visual Basic**， **Visual C#**，或**Visual c + +** 節點，然後  
  
    1.  Visual Basic 或 Visual C#，請選取**Windows**節點，然後選取**Windows Form 應用程式**中**範本**窗格。  
  
    2.  Visual c + + 中，選取**CLR**節點，然後選取**Windows Form 應用程式**中**範本**窗格...  
  
3.  在 **範本**窗格中，選取**Windows 應用程式**。  
  
4.  在 **名稱**方塊中，為專案指定唯一的名稱 (例如 Walkthrough_SimpleDebug)。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
     Visual Studio 會建立新的專案，並在 Windows Form 設計工具中顯示新的表單。 如需詳細資訊，請參閱 < [Windows Form 設計工具](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15)。  
  
6.  在 **檢視**功能表上，選取**工具箱**。  
  
     [工具箱] 便會開啟。 如需詳細資訊，請參閱[工具箱](../ide/reference/toolbox.md)。  
  
7.  在 工具箱 中，按一下** 按鈕**控制項，將控制項拖曳至表單的設計介面。 將按鈕放在表單上。  
  
8.  在 [工具箱] 中，按一下**TextBox**控制項，將控制項拖曳至表單的設計介面。 卸除**TextBox**表單上。  
  
9. 表單設計介面上，按兩下按鈕。  
  
     這會帶您前往字碼頁。 資料指標應該在`button1_Click`。  
  
10. 函式中`button1_Click`。，新增下列程式碼：  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. 在 [建置] 功能表上，選取 [建置方案]。  
  
     未出現任何錯誤，應該可以建置專案。  
  
## <a name="debug-your-form"></a>偵錯您的表單  
 現在，您已準備好開始偵錯。  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>若要偵錯此逐步解說中建立的 Windows Form  
  
1.  在 [來源] 視窗中，按一下您所加入的文字的同一行的左邊的界：  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     會出現一個紅點，並且該行上的文字會以紅色反白顯示。 紅點表示中斷點。 如需詳細資訊，請參閱 <<c0> [ 中斷點](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)。 當您在偵錯工具下執行應用程式時，偵錯工具會在遇到程式碼的位置中斷執行。 接著您就可以檢視應用程式的狀態並對它進行偵錯。  
  
    > [!NOTE]
    >  您也可以以滑鼠右鍵按一下任何一行程式碼，指向**中斷點**，然後按一下**插入中斷點**這一行加入中斷點。  
  
2.  ON**偵錯**功能表上，選擇**開始**。  
  
     Windows Form 會開始執行。  
  
3.  Windows 在表單上，按一下 [新增] 按鈕。  
  
     在 Visual Studio 中，這會帶您前往的行，在程式碼 頁面上設定中斷點。 這行程式碼應該會以黃色反白顯示。 您現在可以檢視應用程式中的變數並控制其執行。 您的應用程式現在已停止執行，等待來自您的動作。  
  
4.  在上**偵錯** 功能表中，選擇**Windows**，然後**監看式**，然後按一下**監看式 1**。  
  
5.  在 **監看式 1**視窗中，按一下空白資料列。 在 **名稱**資料行中輸入`textBox1.Text`（如果您使用 Visual Basic、 Visual C# 或 J#） 或`textBox1->Text`（如果您使用 c + +），然後按 ENTER 鍵。  
  
     **監看式 1**視窗會顯示此變數的值以引號括起來：  
  
    ```  
    ""  
    ```  
  
6.  在 **偵錯**功能表上，選擇**逐步執行**。  
  
     TextBox1.Text 變更的值**監看式 1**視窗：  
  
    ```  
    Button was clicked!  
    ```  
  
7.  在 **偵錯**功能表上，選擇**繼續**繼續偵錯您的程式。  
  
8.  在 Windows 表單中，再按一下 [] 按鈕。  
  
     Visual Studio 會中斷執行一次。  
  
9. 按一下紅點表示中斷點。  
  
     這會從您的程式碼移除中斷點。  
  
10. 在 **偵錯**功能表上，選擇**停止偵錯**。  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>附加至您的 Windows Form 應用程式進行偵錯  
 在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 中，您可以將偵錯工具附加至執行中的處理序。 如果您使用的 Express 版本，不支援這項功能。  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>若要附加至偵錯 Windows Form 應用程式  
  
1.  在您先前建立的專案中，按一下左邊界來一次一次在您加入的行中設定中斷點：  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2.  在 **偵錯**功能表上，選取**啟動但不偵錯**。  
  
     Windows Form 會開始執行 Windows，就如同您必須按兩下可執行檔。 不附加偵錯工具。  
  
3.  在 **偵錯**功能表上，選取**附加至處理序**。 (這個命令也是位於**工具**功能表。)  
  
     [附加至處理序]  對話方塊隨即出現。  
  
4.  在 **可用的處理序**窗格中，尋找處理程序中的名稱 (Walkthrough_SimpleDebug.exe)**程序**資料行，然後按一下它。  
  
5.  按一下 [**附加**] 按鈕。  
  
6.  在 Windows 表單中，按一下一個並只有 按鈕。  
  
     偵錯工具在中斷點中斷執行的 Windows Form。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)



