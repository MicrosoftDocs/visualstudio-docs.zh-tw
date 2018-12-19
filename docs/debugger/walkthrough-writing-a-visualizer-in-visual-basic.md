---
title: 在 Visual Basic 中撰寫視覺化檢視 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69534dbcd3a51ce5c6e4478c6fcc40a770de2548
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065444"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>逐步解說：在 Visual Basic 中撰寫視覺化檢視
本逐步解說顯示如何使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 撰寫簡易的視覺化檢視。 您在本逐步解說中建立的視覺化檢視會使用 Windows Form 訊息方塊顯示字串的內容。 這個簡易字串視覺化檢視是一個基本範例，示範如何建立更適用專案之其他資料型別的視覺化檢視。

> [!NOTE]
> 根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更設定，請在 [工具] 功能表中選擇 [匯入和匯出]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

視覺化檢視的程式碼必須放置在偵錯工具將讀取的 DLL 中。 第一步就是為 DLL 建立類別庫專案。

## <a name="create-and-prepare-a-class-library-project"></a>建立和準備類別庫專案

### <a name="to-create-a-class-library-project"></a>若要建立類別庫專案

1. 在 [檔案] 功能表上，選擇 [新增]，然後按一下 [新增專案]。

2. 在 **新的專案**對話方塊中，選取**Visual Basic**。

3. 底下 **.NET Standard**，按一下**類別庫**。

4. 在 [名稱] 方塊中，為該類別庫鍵入適當的名稱，例如 **MyFirstVisualizer**。

5. 按一下 [確定 **Deploying Office Solutions**]。

   建立類別庫之後，必須加入 Microsoft.VisualStudio.DebuggerVisualizers.DLL 的參考，如此您才能使用這個位置中定義的類別。 但請先為專案提供一個有意義的名稱。

### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>若要重新命名 Class1.vb 和加入 Microsoft.VisualStudio.DebuggerVisualizers

1. 在 [方案總管] 中以滑鼠右鍵按一下 [Class1.vb]，並從捷徑功能表中按一下 [重新命名]。

2. 將 Class1.vb 變更成有意義的名稱，例如 DebuggerSide.vb。

   > [!NOTE]
   >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動變更 DebuggerSide.vb 中的類別宣告，以符合新的檔案名稱。

3. 在 [方案總管] 中，以滑鼠右鍵按一下 [My First Visualizer]，然後在捷徑功能表上按一下 [新增參考]。

4. 在 [新增參考] 對話方塊的 [.NET] 索引標籤上，按一下 [Microsoft.VisualStudio.DebuggerVisualizers.DLL]。

5. 按一下 [確定 **Deploying Office Solutions**]。

6. 在 DebuggerSide.vb 中，將下列陳述式加入至 `Imports` 陳述式：

   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers
   ```

## <a name="add-the-debugger-side-code"></a>加入偵錯工具端程式碼
 現在，您就可以準備建立偵錯工具端的程式碼。 這是在偵錯工具內執行的程式碼，用以顯示您要視覺化的資訊。 首先，您必須變更 `DebuggerSide` 物件的宣告，使其繼承基底類別 (Base Class) `DialogDebuggerVisualizer`。

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>若要繼承自 DialogDebuggerVisualizer

1. 在 DebuggerSide.vb 中，移至下列程式碼行：

   ```vb
   Public Class DebuggerSide
   ```

2. 編輯程式碼使其看來如下所示：

   ```vb
   Public Class DebuggerSide
   Inherits DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` 含有一個您必須覆寫的抽象方法 `Show`。

### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>若要覆寫 DialogDebuggerVisualizer.Show 方法

- 在 `public class DebuggerSide` 中加入下列方法：

  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)

      End Sub
  ```

  `Show` 方法中包含實際建立視覺化檢視對話方塊 (或其他使用者介面) 的程式碼，並會在偵錯工具中顯示已傳遞至視覺化檢視的資訊。 您必須加入該程式碼，以建立對話方塊並顯示資訊。 在本逐步解說中，您將使用 Windows Form 訊息方塊進行上述動作。 首先，您必須加入 `Imports` 的參考和 <xref:System.Windows.Forms> 陳述式。

### <a name="to-add-systemwindowsforms"></a>若要加入 System.Windows.Forms

1.  在 [方案總管]中，以滑鼠右鍵按一下 [參考]，並從捷徑功能表中按一下 [新增參考]。

2.  在 [新增參考] 對話方塊的 [.NET] 索引標籤中，按一下 [System.Windows.Forms]。

3.  按一下 [確定 **Deploying Office Solutions**]。

4.  在 DebuggerSide.cs 中，將下列陳述式加入至 `Imports` 陳述式：

    ```vb
    Imports System.Windows.Forms
    ```

## <a name="create-your-visualizers-user-interface"></a>建立視覺化檢視的使用者介面
 現在，您可以加入某些程式碼，建立並顯示視覺化檢視的使用者介面。 由於這是您的第一個視覺化檢視，因此我們盡量簡化使用者介面，並且會使用訊息方塊。

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>若要在對話方塊中顯示視覺化檢視輸出

1.  在 `Show` 方法中，加入下列程式碼行：

    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())
    ```

     這個程式碼範例不包括錯誤處理。 在真實的視覺化檢視或其他任何類型的應用程式中，都應該包括錯誤處理功能。

2.  在 [建置] 功能表上按一下 [建置 MyFirstVisualizer]。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

## <a name="add-the-necessary-attribute"></a>加入必要屬性
 這是偵錯工具端的程式碼結尾。 但是還有一個步驟，就是加入告知偵錯項目端構成視覺化檢視類別集合的屬性。

### <a name="to-add-the-debugee-side-code"></a>若要加入偵錯項目端程式碼

1.  將下列屬性程式碼加入至 DebuggerSide.vb，放置在 `Imports` 陳述式之後，`namespace MyFirstVisualizer` 之前：

    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>
    ```

2.  在 [建置] 功能表上按一下 [建置 MyFirstVisualizer]。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

## <a name="create-a-test-harness"></a>建立 Test Harness
 這時，您的第一個視覺化檢視已完成。 如果您正確遵循這些步驟的話，應該能夠建置視覺化檢視，並將它安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。 但是，在將視覺化檢視安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之前，應該先進行測試以確定它能正確執行。 現在，您將建立 Test Harness 來執行這個視覺化檢閱，而不將它安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>若要加入顯示視覺化檢視的測試方法

1. 將下列方法加入至 `public DebuggerSide` 類別：

   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))
   visualizerHost.ShowVisualizer()
   End Sub
   ```

2. 在 [建置] 功能表上按一下 [建置 MyFirstVisualizer]。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

   接下來，您必須建立可執行的專案，以呼叫視覺化檢視的 DLL。 為簡單起見請使用主控台應用程式專案。

### <a name="to-add-a-console-application-project-to-the-solution"></a>若要將主控台應用程式專案加入至方案

1. 在 [檔案] 功能表上，依序按一下 [新增] 和 [新增專案]。

2. 在 **加入新的專案**對話方塊中，選取**Visual Basic**，然後按一下**主控台應用程式**。

3. 在 [名稱] 方塊中，為主控台應用程式鍵入有意義的名稱，例如 **MyTestConsole**。

4. 按一下 [確定 **Deploying Office Solutions**]。

   此時，你必須加入必要的參考，如此 MyTestConsole 才能呼叫 MyFirstVisualizer。

### <a name="to-add-necessary-references-to-mytestconsole"></a>若要將必要參考加入至 MyTestConsole

1.  在 [方案總管] 中以滑鼠右鍵按一下 [MyTestConsole]，然後在捷徑功能表中按一下 [新增參考]。

2.  在 [新增參考] 對話方塊的 [.NET] 索引標籤上，按一下 [Microsoft.VisualStudio.DebuggerVisualizers]。

3.  按一下 [確定 **Deploying Office Solutions**]。

4.  以滑鼠右鍵按一下 [MyTestConsole]，然後再次按一下 [新增參考]。

5.  在 [新增參考] 對話方塊中，按一下 [專案] 索引標籤，然後選取 [MyFirstVisualizer]。

6.  按一下 [確定 **Deploying Office Solutions**]。

## <a name="finish-your-test-harness-and-test-your-visualizer"></a>完成 Test Harness 並測試視覺化檢閱
 現在，您就可以加入程式碼來完成 Test Harness。

### <a name="to-add-code-to-mytestconsole"></a>若要將程式碼加入至 MyTestConsole

1. 在 [方案總管] 中以滑鼠右鍵按一下 [Program.vb]，並從捷徑功能表中按一下 [重新命名]。

2. 將 Module1.vb 編輯為適當的名稱，例如 **TestConsole.vb**。

    請注意，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動變更 TestConsole.vb 中的類別宣告，以符合新的檔案名稱。

3. 在 Testconsole.vb。 vb，新增下列`Imports`陳述式：

   ```vb
   Imports MyFirstVisualizer
   ```

4. 在 `Main` 方法中，加入下列程式碼：

   ```vb
   Dim myString As String = "Hello, World"
   DebuggerSide.TestShowVisualizer(myString)
   ```

   現在，您已經準備好可以測試第一個視覺化檢視。

### <a name="to-test-the-visualizer"></a>若要測試視覺化檢視

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [MyTestConsole]，並從捷徑功能表中按一下 [設定為啟始專案]。

2. 按一下 [偵錯] 功能表上的 [開始]。

    這時會啟動主控台應用程式。 視覺化檢視隨即出現，顯示字串 "Hello, World"。

   恭喜您！ 您已完成建置和測試第一個視覺化檢視。

   如果您想在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用視覺化檢閱，而不只是從測試控管中進行呼叫，就必須安裝該視覺化檢閱。 如需詳細資訊，請參閱[＜How to：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)。

## <a name="see-also"></a>另請參閱

- [視覺化檢視架構](../debugger/visualizer-architecture.md)
- [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)
- [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)