---
title: 逐步解說：撰寫視覺化檢視C#|Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b95ac29f3084bf8899249039ffbaa7da8c2294f
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67890472"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>逐步解說：在 C 中撰寫視覺化檢視\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說顯示如何使用 C# 撰寫簡易的視覺化檢視。 您在本逐步解說中建立的視覺化檢視會使用 Windows 表單訊息方塊來顯示字串內容。 這個簡易字串視覺化檢視不是特別適用於本身，但它會顯示建立更有用的視覺化檢視，其他資料類型時，所必須遵循的基本步驟。

> [!NOTE]
> 根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更您的設定，請前往**工具**功能表，然後選擇**匯入和匯出設定**。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)

視覺化檢視程式碼必須放置在 DLL 中，將讀取偵錯工具。 因此，第一個步驟是為 DLL 建立類別庫專案。

#### <a name="to-create-a-class-library-project"></a>若要建立類別庫專案

1. 在上**檔案**功能表上，選擇**新增**，然後按一下 **新專案**。

2. 在 **新的專案**對話方塊的 **專案類型**s 中，選取**Visual C#** 。

3. 在 **範本**方塊中，選擇**類別庫**。

4. 在 [名稱]  方塊中，為該類別庫鍵入適當的名稱，例如 MyFirstVisualizer。

5. 按一下 [確定 **Deploying Office Solutions**]。

   建立類別庫之後，必須新增 Microsoft.VisualStudio.DebuggerVisualizers.DLL 的參考，如此您才能使用於該處定義的類別。 加入參考之前，不過，您必須重新命名一些類別，使得它們具有有意義的名稱。

#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>若要將 Class1.cs 重新命名和加入 Microsoft.VisualStudio.DebuggerVisualizers

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下 Class1.cs，然後選擇**重新命名**快顯功能表上。

2. 將名稱改從 Class1.cs 有意義的名稱，例如 debuggerside.cs。

   > [!NOTE]
   > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會自動變更 debuggerside.cs 中，以符合新的檔案名稱中的類別宣告。

3. 在 **方案總管 中**，以滑鼠右鍵按一下**參考**，然後選擇 **加入參考**快顯功能表上。

4. 在 **加入參考**對話方塊的  **.NET**索引標籤上，選擇 Microsoft.VisualStudio.DebuggerVisualizers.DLL。

5. 按一下 [確定 **Deploying Office Solutions**]。

6. 在 DebuggerSide.cs 中，將下列陳述式加入至 `using` 陳述式：

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   現在，您就可以準備建立偵錯工具端的程式碼。 這是在偵錯工具內執行的程式碼，用以顯示您要視覺化的資訊。 首先，您必須變更的宣告`DebuggerSide`物件，以便繼承自基底類別`DialogDebuggerVisualizer`。

#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>若要繼承自 DialogDebuggerVisualizer

1. 在 debuggerside.cs 中，移至下列程式碼行：

   ```csharp
   public class DebuggerSide
   ```

2. 將程式碼變更：

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` 含有一個您必須覆寫的抽象方法 (`Show`)。

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>若要覆寫 DialogDebuggerVisualizer.Show 方法

- 在 `public class DebuggerSide` 中新增下列**方法：**

  ```csharp
  override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  `Show` 方法中包含實際建立視覺化檢視對話方塊 (或其他使用者介面) 的程式碼，並會在偵錯工具中顯示已傳遞至視覺化檢視的資訊。 您必須加入該程式碼，以建立對話方塊並顯示資訊。 在本逐步解說中，您將使用 Windows 表單訊息方塊進行上述動作。 首先，您必須加入的參考和`using`System.Windows.Forms 的陳述式。

#### <a name="to-add-systemwindowsforms"></a>若要加入 System.Windows.Forms

1. 在 **方案總管 中**，以滑鼠右鍵按一下**參考**，然後選擇 **加入參考**快顯功能表上。

2. 在 **加入參考**對話方塊的  **.NET**索引標籤上，選擇 System.Windows.Forms.DLL。

3. 按一下 [確定]  。

4. 在 DebuggerSide.cs 中，將下列陳述式加入至 `using` 陳述式：

   ```csharp
   using System.Windows.Forms;
   ```

   現在，您可以新增某些程式碼，建立並顯示視覺化檢視的使用者介面。 因為這是您第一個視覺化檢視時，我們將會簡化使用者介面，並將訊息方塊。

#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>在對話方塊中顯示視覺化檢視輸出

1. 在 `Show` 方法中，加入下列程式碼行：

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    這個程式碼範例不包括錯誤處理。 在真實視覺化檢視或其他任何類型的應用程式中，都應該包括錯誤處理功能。

2. 在 **建置**功能表上，選擇**建置 MyFirstVisualizer**。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

   這是偵錯工具端的程式碼結尾。 但是還有一個步驟，就是加入告知偵錯項目端構成視覺化檢視類別集合的屬性。

#### <a name="to-add-the-debuggee-side-code"></a>若要新增的偵錯項目端程式碼

1. 加入 debuggerside.cs 中中的下列屬性程式碼之後,`using`陳述式之前`namespace MyFirstVisualizer`:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target  = typeof(System.String),
   Description  = "My First Visualizer")]
   ```

2. 在 **建置**功能表上，選擇**建置 MyFirstVisualizer**。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

   這時，您的第一個視覺化檢視已完成。 如果您正確遵循這些步驟的話，應該能夠建置視覺化檢視，並將它安裝至 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中。 但是，在將視覺化檢視安裝至 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 之前，應該先進行測試以確定它能正確執行。 現在，您將建立 Test Harness 來執行這個視覺化檢閱，而不將它安裝至 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中。

#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>新增顯示視覺化檢視的測試方法

1. 將下列方法加入至 `public DebuggerSide` 類別：

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. 在 **建置**功能表上，選擇**建置 MyFirstVisualizer**。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

   接下來，您必須建立可執行的專案，以呼叫視覺化檢視的 DLL。 為了簡單起見，我們將使用的主控台應用程式專案。

#### <a name="to-add-a-console-application-project-to-the-solution"></a>若要將主控台應用程式專案加入至方案

1. 在上**檔案**功能表上，選擇**新增**，然後按一下 **新專案**。

2. 在 **加入新的專案**對話方塊中，於**範本**方塊中，選擇 **主控台應用程式**。

3. 在 **名稱**方塊中，輸入有意義的名稱，為主控台應用程式，例如`MyTestConsole`。

4. 按一下 [確定]  。

   此時，你必須加入必要的參考，如此 MyTestConsole 才能呼叫 MyFirstVisualizer。

#### <a name="to-add-necessary-references-to-mytestconsole"></a>若要將必要參考加入至 MyTestConsole

1. 在 **方案總管 中**，以滑鼠右鍵按一下**MyTestConsole** ，然後選擇 **加入參考**快顯功能表上。

2. 在 **加入參考** 對話方塊中， **.NET**索引標籤上，選擇 Microsoft.VisualStudio.DebuggerVisualizers.DLL。

3. 按一下 [確定 **Deploying Office Solutions**]。

4. 以滑鼠右鍵按一下**MyTestConsole** ，然後選擇**加入參考**一次。

5. 在 **加入參考** 對話方塊中，按一下**專案**索引標籤，然後按一下 MyFirstVisualizer。

6. 按一下 [確定 **Deploying Office Solutions**]。

   現在，您就可以加入程式碼來完成測試載入器。

#### <a name="to-add-code-to-mytestconsole"></a>若要將程式碼加入至 MyTestConsole

1. 在 **方案總管 中**，以滑鼠右鍵按一下 Program.cs，然後選擇**重新命名**快顯功能表上。

2. 編輯 Program.cs 中的名稱，以更有意義的名稱，例如 TestConsole.cs。

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會自動變更 TestConsole.cs 以符合新的檔案名稱中的類別宣告。

3. 在 TestConsole.cs，加入下列程式碼`using`陳述式：

   ```csharp
   using MyFirstVisualizer;
   ```

4. 在 `Main` 方法中，加入下列程式碼：

   ```
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   現在，您已經準備好可以測試第一個視覺化檢視。

#### <a name="to-test-the-visualizer"></a>若要測試視覺化檢視

1. 在 **方案總管 中**，以滑鼠右鍵按一下**MyTestConsole** ，然後選擇 **設定為啟始專案**快顯功能表上。

2. 在 [偵錯]  功能表上選擇 [啟動]  。

    在主控台應用程式啟動和視覺化檢視會出現並顯示的字串"Hello，World"。

   恭喜您！ 您已完成建置和測試第一個視覺化檢視。

   如果您想在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中使用視覺化檢閱，而不只是從測試控管中進行呼叫，就必須安裝該視覺化檢閱。 如需詳細資訊，請參閱[如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)。

## <a name="using-the-visualizer-item-template"></a>使用視覺化檢視項目範本
 到目前為止，本逐步解說示範了如何以手動方式建立視覺化檢視。 這是學習練習。 既然您已經知道簡單的視覺化檢視的運作方式，是建立一個更簡單的方法： 使用視覺化檢視項目範本。

 首先，您必須建立新的類別庫專案。

#### <a name="to-create-a-new-class-library"></a>若要建立新的類別庫

1. 在上**檔案**功能表上，選擇**新增**，然後按一下 **新專案**。

2. 在 **加入新的專案**對話方塊的 **專案類型**s 中，選取**Visual C#** 。

3. 在 **範本**方塊中，選擇**類別庫**。

4. 在 **名稱**方塊中，輸入適當的類別程式庫，例如 MySecondVisualizer 名稱。

5. 按一下 [確定]  。

   現在，您可以將視覺化檢視項目加入它：

#### <a name="to-add-a-visualizer-item"></a>若要新增的視覺化檢視項目

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下 MySecondVisualizer。

2. 在捷徑功能表，選擇**新增**，然後按一下**新項目**。

3. 在 **加入新項目**對話方塊的 **範本**， **Visual Studio 安裝的範本**，選取**偵錯工具視覺化檢視**。

4. 在 **名稱**方塊中，輸入適當的名稱，例如 SecondVisualizer.cs。

5. 按一下 [加入]  。

   這就是這麼簡單。 SecondVisualizer.cs 的檔案，並檢視範本新增為您的程式碼。 請繼續並實驗程式碼。 既然您已經知道的基本概念，就可以建立您自己的更複雜且實用的視覺化檢視。

## <a name="see-also"></a>另請參閱

- [視覺化檢視架構](../debugger/visualizer-architecture.md)
- [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)
- [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)
