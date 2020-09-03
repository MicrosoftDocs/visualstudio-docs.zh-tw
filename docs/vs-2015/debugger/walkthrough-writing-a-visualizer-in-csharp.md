---
title: '逐步解說：在 c # 中撰寫視覺化 |Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "67890472"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>逐步解說：在 C\# 中撰寫視覺化檢視

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說顯示如何使用 C# 撰寫簡易的視覺化檢視。 您在本逐步解說中建立的視覺化檢視會使用 Windows 表單訊息方塊來顯示字串內容。 這個簡單的字串視覺化程式本身並不實用，但它會顯示您必須遵循的基本步驟，以建立其他資料類型的更實用視覺化檢視。

> [!NOTE]
> 根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更您的設定，請移至 [ **工具** ] 功能表，然後選擇 [匯 **入和匯出設定**]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

視覺化程式碼必須放在 DLL 中，偵錯工具將會讀取這個 DLL。 因此，第一個步驟是建立 DLL 的類別庫專案。

#### <a name="to-create-a-class-library-project"></a>若要建立類別庫專案

1. 在 [檔案 **] 功能表上，選擇 [** **新增** ]，然後按一下 [ **新增專案**]。

2. 在 [ **新增專案** ] 對話方塊的 [ **專案類型**s] 底下，選取 [ **Visual c #**]。

3. 在 [ **範本** ] 方塊中，選擇 [ **類別庫**]。

4. 在 [ **名稱** ] 方塊中，為類別庫輸入適當的名稱，例如 MyFirstVisualizer。

5. 按一下 [確定]  。

   建立類別庫之後，必須新增 Microsoft.VisualStudio.DebuggerVisualizers.DLL 的參考，如此您才能使用於該處定義的類別。 不過，在加入參考之前，您必須重新命名一些類別，使其具有有意義的名稱。

#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>重新命名 Class1.cs 並新增 VisualStudio. Microsoft.visualstudio.debuggervisualizers.dll

1. 在 **方案總管**中，以滑鼠右鍵按一下 Class1.cs，然後在快捷方式功能表上選擇 [ **重新命名** ]。

2. 將名稱從 Class1.cs 變更為有意義的內容，例如 DebuggerSide.cs。

   > [!NOTE]
   > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 自動變更 DebuggerSide.cs 中的類別宣告，以符合新的檔案名。

3. 在 **方案總管**中，以滑鼠右鍵按一下 [ **參考** ]，然後在快捷方式功能表上選擇 [ **加入參考** ]。

4. 在 [ **加入參考** ] 對話方塊的 [ **.net** ] 索引標籤上，選擇 [Microsoft.VisualStudio.DebuggerVisualizers.DLL]。

5. 按一下 [確定]  。

6. 在 DebuggerSide.cs 中，將下列陳述式加入至 `using` 陳述式：

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   現在，您就可以準備建立偵錯工具端的程式碼。 這是在偵錯工具內執行的程式碼，用以顯示您要視覺化的資訊。 首先，您必須變更物件的宣告， `DebuggerSide` 以便繼承自基類 `DialogDebuggerVisualizer` 。

#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>若要繼承自 DialogDebuggerVisualizer

1. 在 DebuggerSide.cs 中，移至下列程式程式碼：

   ```csharp
   public class DebuggerSide
   ```

2. 將程式碼變更為：

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` 含有一個您必須覆寫的抽象方法 (`Show`)。

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>若要覆寫 DialogDebuggerVisualizer.Show 方法

- 在中 `public class DebuggerSide` ，新增下列 **方法：**

  ```csharp
  override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  `Show` 方法中包含實際建立視覺化檢視對話方塊 (或其他使用者介面) 的程式碼，並會在偵錯工具中顯示已傳遞至視覺化檢視的資訊。 您必須加入該程式碼，以建立對話方塊並顯示資訊。 在本逐步解說中，您將使用 Windows 表單訊息方塊進行上述動作。 首先，您必須加入 `using` system.object 的參考和語句。

#### <a name="to-add-systemwindowsforms"></a>若要加入 System.Windows.Forms

1. 在 **方案總管**中，以滑鼠右鍵按一下 [ **參考** ]，然後在快捷方式功能表上選擇 [ **加入參考** ]。

2. 在 [ **加入參考** ] 對話方塊的 [ **.net** ] 索引標籤上，選擇 [System.Windows.Forms.DLL]。

3. 按一下 [確定]  。

4. 在 DebuggerSide.cs 中，將下列陳述式加入至 `using` 陳述式：

   ```csharp
   using System.Windows.Forms;
   ```

   現在，您可以新增某些程式碼，建立並顯示視覺化檢視的使用者介面。 因為這是您的第一個視覺化檢視，所以我們會讓使用者介面保持簡單，並使用訊息方塊。

#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>在對話方塊中顯示視覺化檢視輸出

1. 在 `Show` 方法中新增下列程式碼：

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    這個程式碼範例不包括錯誤處理。 在真實視覺化檢視或其他任何類型的應用程式中，都應該包括錯誤處理功能。

2. 在 [ **組建** ] 功能表上，選擇 [ **組建 MyFirstVisualizer**]。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

   這是偵錯工具端的程式碼結尾。 但是還有一個步驟，就是加入告知偵錯項目端構成視覺化檢視類別集合的屬性。

#### <a name="to-add-the-debuggee-side-code"></a>若要加入偵錯工具端程式碼

1. 在語句之後但之前，將下列屬性程式碼新增至 DebuggerSide.cs `using` `namespace MyFirstVisualizer` ：

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target  = typeof(System.String),
   Description  = "My First Visualizer")]
   ```

2. 在 [ **組建** ] 功能表上，選擇 [ **組建 MyFirstVisualizer**]。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

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

2. 在 [ **組建** ] 功能表上，選擇 [ **組建 MyFirstVisualizer**]。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

   接下來，您必須建立可執行的專案，以呼叫視覺化檢視的 DLL。 為了簡單起見，我們將使用主控台應用程式專案。

#### <a name="to-add-a-console-application-project-to-the-solution"></a>若要將主控台應用程式專案加入至方案

1. 在 [檔案 **] 功能表上** ，選擇 [ **加入** ]，然後按一下 [ **新增專案**]。

2. 在 [ **加入新專案** ] 對話方塊的 [ **範本** ] 方塊中，選擇 [ **主控台應用程式**]。

3. 在 [ **名稱** ] 方塊中，為主控台應用程式輸入有意義的名稱，例如 `MyTestConsole` 。

4. 按一下 [確定]  。

   此時，你必須加入必要的參考，如此 MyTestConsole 才能呼叫 MyFirstVisualizer。

#### <a name="to-add-necessary-references-to-mytestconsole"></a>若要將必要參考加入至 MyTestConsole

1. 在 **方案總管**中，以滑鼠右鍵按一下 **MyTestConsole** ，然後選擇快捷方式功能表上的 [ **加入參考** ]。

2. 在 [ **加入參考** ] 對話方塊的 [ **.net** ] 索引標籤中，選擇 [Microsoft.VisualStudio.DebuggerVisualizers.DLL]。

3. 按一下 [確定]  。

4. 以滑鼠右鍵按一下 **MyTestConsole** ，然後選擇 [ **加入參考** ]。

5. 在 [ **加入參考** ] 對話方塊中，按一下 [ **專案** ] 索引標籤，然後按一下 [MyFirstVisualizer]。

6. 按一下 [確定]  。

   現在，您就可以加入程式碼來完成測試載入器。

#### <a name="to-add-code-to-mytestconsole"></a>若要將程式碼加入至 MyTestConsole

1. 在 **方案總管**中，以滑鼠右鍵按一下 Program.cs，然後在快捷方式功能表上選擇 [ **重新命名** ]。

2. 將名稱從 Program.cs 編輯為更有意義的名稱，例如 TestConsole.cs。

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 自動變更 TestConsole.cs 中的類別宣告，以符合新的檔案名。

3. 在 TestConsole.cs 中，將下列程式碼加入至 `using` 語句：

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

1. 在 **方案總管**中，以滑鼠右鍵按一下 **MyTestConsole** ，然後在快捷方式功能表上選擇 [ **設定為啟始專案** ]。

2. 在 [偵錯]**** 功能表上選擇 [啟動]****。

    主控台應用程式隨即啟動，並出現視覺化檢視，並顯示 "Hello，World" 字串。

   恭喜。 您已完成建置和測試第一個視覺化檢視。

   如果您想在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中使用視覺化檢閱，而不只是從測試控管中進行呼叫，就必須安裝該視覺化檢閱。 如需詳細資訊，請參閱 [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)。

## <a name="using-the-visualizer-item-template"></a>使用視覺化專案範本
 到目前為止，本逐步解說已說明如何以手動方式建立視覺化檢視。 這是做為學習練習的做法。 既然您已經知道簡單的視覺化程式如何運作，有更簡單的方法可以建立一個：使用視覺化程式專案範本。

 首先，您必須建立新的類別庫專案。

#### <a name="to-create-a-new-class-library"></a>若要建立新的類別庫

1. 在 [檔案 **] 功能表上** ，選擇 [ **加入** ]，然後按一下 [ **新增專案**]。

2. 在 [ **加入新專案** ] 對話方塊的 [ **專案類型**s] 下，選取 [ **Visual c #**]。

3. 在 [ **範本** ] 方塊中，選擇 [ **類別庫**]。

4. 在 [ **名稱** ] 方塊中，為類別庫輸入適當的名稱，例如 MySecondVisualizer。

5. 按一下 [確定]  。

   現在，您可以在其中新增視覺化檢視專案：

#### <a name="to-add-a-visualizer-item"></a>新增視覺化專案

1. 在 **方案總管**中，以滑鼠右鍵按一下 [MySecondVisualizer]。

2. 在快捷方式功能表上，選擇 [ **加入** ]，然後按一下 [ **新增專案**]。

3. 在 [ **加入新專案** ] 對話方塊的 [ **範本**] 底下， **Visual Studio 已安裝的範本**] 中，選取 **[偵錯工具視覺化**]。

4. 在 [ **名稱** ] 方塊中，輸入適當的名稱，例如 SecondVisualizer.cs。

5. 按一下 [新增] 。

   這就是這樣的。 查看檔案 SecondVisualizer.cs，並查看範本為您新增的程式碼。 請繼續進行，並使用程式碼進行實驗。 既然您已經瞭解基本概念，就可以開始建立更複雜且有用的視覺化檢視。

## <a name="see-also"></a>另請參閱

- [視覺化檢視架構](../debugger/visualizer-architecture.md)
- [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)
- [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)
