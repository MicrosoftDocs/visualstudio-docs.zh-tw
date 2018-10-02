---
title: 逐步解說：以使用時產生功能支援測試優先 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Generate From Usage
- Test-First Development
ms.assetid: 764c17a4-cd95-4c23-bf63-d92d9c5adfb2
caps.latest.revision: 68
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8a290eebec2c3847d41f36568196ec35935e332a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496642"
---
# <a name="walkthrough-test-first-support-with-the-generate-from-usage-feature"></a>逐步解說：以使用時產生功能支援測試優先
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[逐步解說： 使用產生的功能支援測試優先](https://docs.microsoft.com/visualstudio/ide/walkthrough-test-first-support-with-the-generate-from-usage-feature)。  
  
本主題示範如何使用支援「測試優先」開發的[使用時產生](../misc/generate-from-usage.md)功能。  
  
 *「測試先行」開發方式* (Test-first development) 這種軟體設計方法，要先根據產品規格撰寫單元測試，再撰寫測試成功所需要的原始程式碼。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 支援「測試先行」開發方式的做法是，當您第一次在測試案例中參考類型和成員，在它們被定義之前，以原始程式碼產生新的類型和成員。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 在盡可能不中斷工作流程的情況下產生新的類型和成員。 您可以建立類型、方法、屬性、欄位或建構函式的 Stub，但不離開目前所在的程式碼位置。 當您開啟對話方塊指定類型產生選項時，焦點會在對話方塊一關閉時，立即回到目前開啟的檔案。  
  
 [從用量產生] 功能可以和整合了 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的測試架構一起使用。 本主題會示範 Microsoft 單元測試架構。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>建立 Windows 類別庫專案和測試專案  
  
1.  在 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 或 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]中建立新的 Windows 類別庫專案。 將其命名為 `GFUDemo_VB` 或 `GFUDemo_CS`，視所用語言而定。  
  
2.  在 **方案總管**中，以滑鼠右鍵按一下上方的解決方案，指向 [加入] ，然後按一下 [新增專案] 。 在 [新增專案]  對話方塊左側的 [專案類型]  窗格中，按一下 [測試] 。  
  
3.  在 [範本]  窗格中按一下 [單元測試專案]  ，並接受預設名稱 UnitTestProject1。 下圖顯示當它出現在 [!INCLUDE[csprcs](../includes/csprcs-md.md)]時的對話方塊。 在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中，對話方塊看起來很類似。  
  
     ![[新增測試專案] 對話方塊](../ide/media/newproject-test.png "NewProject_Test")  
新增專案對話方塊  
  
4.  按一下 [確定]  關閉 [新增專案]  對話方塊。

5.  在您的類別專案內，於 [方案總管] 中，以滑鼠右鍵按一下 [參考] 項目，並按一下 [加入參考]。

6.  在 [參考管理員] 對話方塊中，選取 [專案]，然後選取您的單元測試專案。

7.  按一下 [確定] 以關閉 [參考管理員] 對話方塊。

8.  在 **Class1**檔案中，於最後一個現有 **using** 陳述式的正後方，針對測試專案加入 **using** 陳述式：

    * 在 Visual Basic 中，加入 `Using UnitTestProject1`
    
    * 在 C# 中，加入 `using UnitTestProject1;`
    
9.  儲存您的方案。 您已準備好可開始撰寫測試  
  
### <a name="to-generate-a-new-class-from-a-unit-test"></a>從單元測試產生新類別  
  
1.  測試專案包含名為 UnitTest1 的檔案。 在 **方案總管** 中按兩下這個檔案，在程式碼編輯器中開啟它。 已產生測試類別和測試方法。  
  
2.  找到類別 `UnitTest1` 的宣告，並將它重新命名為 `AutomobileTest`。 如果 C# 中有 `UnitTest1()` 建構函式，請將它重新命名為 `AutomobileTest()`。  
  
    > [!NOTE]
    >  IntelliSense 提供兩種完成 IntelliSense 陳述式的方式： *完成模式* (completion mode) 和 *建議模式*(suggestion mode)。 當類別和成員在使用前即已定義的情況下，請使用建議模式。 當 IntelliSense 視窗開啟時，您可以按 CTRL+ALT+SPACEBAR 在完成模式和建議模式之間切換。 如需詳細資訊，請參閱 [Using IntelliSense](../ide/using-intellisense.md) 。 當您在下個步驟輸入 `Automobile` 時，建議模式非常有幫助。  
  
3.  找到 `TestMethod1()` 方法並將它重新命名為 `DefaultAutomobileIsInitializedCorrectly()`。 在這個方法內，建立名為 `Automobile`的類別新執行個體，如下列圖例所示。 波浪底線隨即出現，這表示發生編譯時期錯誤，類型名稱下會出現智慧標籤。 智慧標籤的確切位置會因您使用 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 而不同。  
  
     ![Visual Basic 中的智慧標籤底線](../ide/media/genclass-underlinevb.png "GenClass_UnderlineVB")  
Visual Basic  
  
     ![C&#35; 中的智慧標籤底線](../ide/media/genclass-underline.png "GenClass_Underline")  
Visual C#  
  
4.  將滑鼠指標停留在智慧標籤上查看錯誤訊息，表示尚未定義任何名為 `Automobile` 的類型。 按一下智慧標籤，或按 CTRL+。 (CTRL+ 句號) 開啟 [從用量產生] 快顯功能表，如下圖所示。  
  
     ![Visual Basic 中的智慧標籤內容功能表](../ide/media/genclass-smartvb.png "GenClass_SmartVB")  
Visual Basic  
  
     ![C&#35; 中的智慧標籤內容功能表](../ide/media/genclass-smartcs.png "GenClass_SmartCS")  
Visual C#  
  
5.  您現在有兩種選擇。 您可以按一下 [產生 'Class Automobile']  在測試專案中建立新的檔案，並填入名為 `Automobile`的空類別。 這可以在新檔案中快速建立新類別，這個新檔案具有目前專案的預設存取修飾詞。 您也可以按一下 [產生新的類型]  開啟 [產生新的類型]  對話方塊。 提供的選項包括將類別放在現有的檔案，以及將檔案加入另一個專案中。  
  
     按一下 [產生新的類型]  開啟 [產生新的類型]  對話方塊，如下圖所示。 在 [專案]  清單中，按一下 [GFUDemo_VB]  或 [GFUDemo_CS]  指示 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 將檔案加入原始程式碼專案中，不是加入測試專案。  
  
     ![[產生新的類型] 對話方塊](../ide/media/genotherdialog.png "GenOtherDialog")  
[產生新的類型] 對話方塊  
  
6.  按一下 [確定]  關閉對話方塊，並建立新的檔案。  
  
7.  在 **方案總管**的 [GFUDemo_VB] 或 [GFUDemo_CS] 專案節點下，確認是否有新增的 Automobile.vb 或 Automobile.cs 檔案。 在程式碼編輯器中，焦點仍在 `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`。 您可以盡可能不中斷的方式繼續撰寫測試。  
  
### <a name="to-generate-a-property-stub"></a>產生屬性 Stub  
  
1.  假設產品規格規定 `Automobile` 類別有兩個公用屬性，名為 `Model` 和 `TopSpeed`。 這些屬性必須由預設的建構函式以 `"Not specified"` 和 `-1` 的預設值來初始化。 以下的單元測試會驗證預設建構函式是否將屬性設定為正確的預設值。  
  
     在 `DefaultAutomobileIsInitializedCorrectly`中加入下列程式碼行：  
  
     [!code-csharp[VbTDDWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#1)]
     [!code-vb[VbTDDWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#1)]  
  
     因為程式碼參考 `Automobile`上未定義的兩個屬性，所以會顯示智慧標籤。 按一下 `Model` 的智慧標籤，然後按一下 [產生屬性 Stub] 。 也產生 `TopSpeed` 屬性的屬性Stub。  
  
     在 `Automobile` 類別中，會從內容正確推斷出新屬性的類型。  
  
     下圖顯示智慧標籤的快顯功能表。  
  
     ![Visual Basic 中的產生屬性內容功能表](../ide/media/genpropertysmarttagvb.png "GenPropertySmartTagVB")  
Visual Basic  
  
     ![C&#35; 中的產生屬性內容功能表](../ide/media/genpropertysmarttagcs.png "GenPropertySmartTagCS")  
Visual C#  
  
### <a name="to-locate-the-source-code"></a>找出原始程式碼  
  
1.  使用 [巡覽至]  功能巡覽至 Automobile.cs 或 Automobile.vb 原始程式碼檔，以便驗證是否已產生新的屬性。  
  
     [巡覽至]  功能可讓您快速輸入文字字串，例如類型名稱或部分名稱，按一下結果清單中的項目移至想要的位置。  
  
     在程式碼編輯器按一下，然後按 CTRL+, (CTRL+逗號)，隨即開啟 [巡覽至]  對話方塊。 在文字方塊中輸入 `automobile`。 按一下清單中的 [汽車]  類別，然後按一下 [確定] 。  
  
     下圖即會顯示 [巡覽至]  視窗。  
  
     ![[巡覽至] 對話方塊](../ide/media/navigate-2.png "Navigate_2")  
[巡覽至] 視窗  
  
### <a name="to-generate-a-stub-for-a-new-constructor"></a>產生新建構函式的 Stub  
  
1.  在這個測試方法中，您會產生建構函式 Stub，它會初始化 `Model` 和 `TopSpeed` 屬性以獲得您指定的值。 稍後，您會加入更多的程式碼以完成測試。 請將下列其他測試方法加入您的 `AutomobileTest` 類別中。  
  
     [!code-csharp[VbTDDWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#2)]
     [!code-vb[VbTDDWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#2)]  
  
2.  按一下新類別建構函式下的智慧標籤，然後按一下 [產生建構函式 Stub] 。 請注意，在 `Automobile` 類別檔案中，新的建構函式已檢查建構函式呼叫中所使用的區域變數名稱，找到 `Automobile` 類別中具有相同名稱的屬性，並提供建構函式主體的程式碼將引數值儲存在 `Model` 和 `TopSpeed` 屬性中。 (在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]中，新建構函式的 `_model` 和 `_topSpeed` 欄位都是 `Model` 和 `TopSpeed` 屬性的隱含定義支援欄位。)  
  
3.  產生新的建構函式後， `DefaultAutomobileIsInitializedCorrectly`的預設建構函式呼叫下會出現波浪底線。 錯誤訊息指出 `Automobile` 類別沒有任何建構函式採用零引數。 若要產生沒有任何參數的明確預設建構函式，請按一下智慧標籤，然後按一下 [產生建構函式 Stub] 。  
  
### <a name="to-generate-a-stub-for-a-method"></a>產生方法的 Stub  
  
1.  假設規格規定，如果其 `Automobile` 和 `Model` 屬性設為預設值以外的值，新的 `TopSpeed` 就可以放入執行狀態。 請將下列各行加入 `AutomobileWithModelNameCanStart` 方法中。  
  
     [!code-csharp[VbTDDWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#3)]
     [!code-vb[VbTDDWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#3)]  
  
2.  按一下 `myAuto.Start` 方法呼叫的智慧標籤，然後按一下 [產生方法 Stub] 。  
  
3.  按一下 `IsRunning` 屬性的智慧標籤，然後按一下 [產生屬性 Stub] 。 現在 `Automobile` 類別包含下列程式碼。  
  
     [!code-csharp[VbTDDWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#4)]
     [!code-vb[VbTDDWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#4)]  
  
### <a name="to-run-the-tests"></a>執行測試  
  
1.  在 [單元測試]  功能表中指向 [執行單元測試] ，然後按一下 [所有測試] 。 這個命令會執行為目前的解決方案撰寫的所有測試架構中的全部測試。  
  
     在這個案例中，會有兩個測試，而且兩個測試都應該要失敗。 `DefaultAutomobileIsInitializedCorrectly` 測試失敗的原因是 `Assert.IsTrue` 條件傳回 `False`。 `AutomobileWithModelNameCanStart` 測試失敗的原因是 `Start` 類別的 `Automobile` 方法擲回例外狀況。  
  
     下圖顯示 [測試結果]  視窗。  
  
     ![失敗的測試結果](../ide/media/testsfailed.png "TestsFailed")  
測試結果視窗  
  
2.  在 [測試結果]  視窗中，在每個測試結果資料列按兩下，移至每一項測試失敗的位置。  
  
### <a name="to-implement-the-source-code"></a>實作原始程式碼  
  
1.  將下列程式碼加入預設建構函式中，讓 `Model`、 `TopSpeed` 和 `IsRunning` 屬性都初始化為正確的 `"Not specified"`、 `-1`和 `True` (`true`) 預設值。  
  
     [!code-csharp[VbTDDWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#5)]
     [!code-vb[VbTDDWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#5)]  
  
2.  呼叫 `Start` 方法時，它應該只有在 `IsRunning` 或 `Model` 屬性設為預設值以外的值時，才將 `TopSpeed` 旗標設為 true。 從方法主體移除 `NotImplementedException` ，並加入下列程式碼。  
  
     [!code-csharp[VbTDDWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#6)]
     [!code-vb[VbTDDWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#6)]  
  
### <a name="to-run-the-tests-again"></a>再次執行測試  
  
1.  在 [測試]  功能表中指向 [執行] ，然後按一下 [方案中的所有測試] 。 測試這一次會成功。 下圖顯示 [測試結果]  視窗。  
  
     ![成功的測試結果](../ide/media/testspassed.png "TestsPassed")  
測試結果視窗  
  
## <a name="see-also"></a>另請參閱  
 [使用時產生](../misc/generate-from-usage.md)   
 [撰寫程式碼](../ide/writing-code-in-the-code-and-text-editor.md)   
 [使用 IntelliSense](../ide/using-intellisense.md)   
 [對程式碼進行單元測試](../test/unit-test-your-code.md)



