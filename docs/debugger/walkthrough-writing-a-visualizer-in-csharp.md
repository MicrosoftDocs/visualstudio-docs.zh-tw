---
title: '以 c # 撰寫視覺化檢視 |Microsoft Docs'
description: '遵循逐步解說，以 c # 建立簡單的視覺化檢視。 它會顯示使用和不使用視覺化檢視專案範本時所需的步驟。'
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: a6ce1a6d9f2f8a36d892d484cf9353e1312758b4
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549507"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>逐步解說：在 C\# 中撰寫視覺化檢視

本逐步解說顯示如何使用 C# 撰寫簡易的視覺化檢視。 您將在本逐步解說中建立的視覺化檢視會使用 Windows 表單來顯示字串的內容。 這個簡單的字串視覺化程式本身並不實用，但它會顯示您必須遵循的基本步驟，以建立其他資料類型的更實用視覺化檢視。

> [!NOTE]
> 根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更您的設定，請移至 [**工具**] 功能表，然後選擇 [匯 **入和匯出設定**。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

視覺化程式碼必須放在 DLL 中，偵錯工具將會讀取這個 DLL。 因此，第一個步驟是建立 DLL 的類別庫專案。

## <a name="create-a-visualizer-manually"></a>手動建立視覺化檢視

請遵循下列工作來建立視覺化檢視。

### <a name="to-create-a-class-library-project"></a>若要建立類別庫專案

* 建立新的類別庫專案。

    ::: moniker range=">=vs-2019"
    選擇 **[** 檔案  >  **新增**  >  **Project**]。 在 [語言] 下拉式清單中，選擇 [ **c #**]。 在 [搜尋] 方塊中，輸入 **類別庫**，然後選擇 [**類別庫]， (.NET Framework)**。 按一下 [下一步] 。 在出現的對話方塊中，輸入名稱，然後 `MyFirstVisualizer` 按一下 [ **建立**]。

    針對視覺化程式專案，請確定您選取的是 .NET Framework 類別庫，而不是 .net。 雖然需要 .NET Framework 視覺化，但呼叫的應用程式可以是 .net Core。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **Project**]。 在 [**新增專案**] 對話方塊的左窗格中，選擇 [ **Visual c #**] 底下的 [ **.NET Framework**]，然後在中間窗格中選擇 [**類別庫] (.NET Framework)**。

    輸入類別庫的適當名稱（例如），然後 `MyFirstVisualizer` 按一下 [ **建立** **] 或 [確定]**。
    ::: moniker-end

   建立類別庫之後，必須新增 Microsoft.VisualStudio.DebuggerVisualizers.DLL 的參考，如此您才能使用於該處定義的類別。 不過，在加入參考之前，您必須重新命名一些類別，使其具有有意義的名稱。

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>若要重新命名 Class1 並新增 VisualStudio. Microsoft.visualstudio.debuggervisualizers.dll

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [Class1]，然後在快捷方式功能表上選擇 [ **重新命名** ]。

2. 將名稱從 Class1 變更為有意義的名稱，例如 Debuggerside.vb .cs。

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 自動變更 Debuggerside.vb 中的類別宣告，使其符合新的檔案名。

3. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **參考** ]，然後在快捷方式功能表上選擇 [ **加入參考** ]。

4. 在 [ **加入參考** ] 對話方塊的 [ **流覽** ] 索引標籤上，選取 **[流覽** ] 並尋找 Microsoft.VisualStudio.DebuggerVisualizers.DLL。

    您可以在 Visual Studio 的安裝目錄的 *\<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* 子目錄中找到 DLL。

5. 按一下 [確定]  。

6. 在 Debuggerside.vb 中，將下列內容新增至指示詞 `using` ：

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   現在，您就可以準備建立偵錯工具端的程式碼。 這是在偵錯工具內執行的程式碼，用以顯示您要視覺化的資訊。 首先，您必須變更物件的宣告， `DebuggerSide` 以便繼承自基類 `DialogDebuggerVisualizer` 。

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>若要繼承自 DialogDebuggerVisualizer

1. 在 Debuggerside.vb 中，移至下列程式程式碼：

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
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  `Show` 方法中包含實際建立視覺化檢視對話方塊 (或其他使用者介面) 的程式碼，並會在偵錯工具中顯示已傳遞至視覺化檢視的資訊。 您必須加入該程式碼，以建立對話方塊並顯示資訊。 在本逐步解說中，您將使用 Windows Form 訊息方塊進行上述動作。 首先，您必須 `using` 為 System. Windows 加入參考和指示詞。形式。

### <a name="to-add-systemwindowsforms"></a>若要加入 System.Windows.Forms

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **參考** ]，然後在快捷方式功能表上選擇 [ **加入參考** ]。

2. 在 [ **加入參考** ] 對話方塊的 [ **流覽** ] 索引標籤上，選取 **[流覽**]，然後尋找 System.Windows.Forms.DLL。

    您可以在 *C：\ Windows \Microsoft.NET\Framework\v4.0.30319* 中找到 DLL。

3. 按一下 [確定]  。

4. 在 Debuggerside.vb 中，將下列內容新增至指示詞 `using` ：

   ```csharp
   using System.Windows.Forms;
   ```

   現在，您可以新增某些程式碼，建立並顯示視覺化檢視的使用者介面。 因為這是您的第一個視覺化檢視，所以我們會讓使用者介面保持簡單，並使用訊息方塊。

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>在對話方塊中顯示視覺化檢視輸出

1. 在 `Show` 方法中新增下列程式碼：

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    這個程式碼範例不包括錯誤處理。 在真實視覺化檢視或其他任何類型的應用程式中，都應該包括錯誤處理功能。

2. 在 [ **組建** ] 功能表上，選擇 [ **組建 MyFirstVisualizer**]。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

   這是偵錯工具端的程式碼結尾。 但是還有一個步驟，就是加入告知偵錯項目端構成視覺化檢視類別集合的屬性。

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>若要加入型別，以針對偵錯工具端程式碼將型別視覺化

在偵錯工具端程式碼中，您可以使用屬性來指定要將物件來源) 視覺化 (物件來源的型別 <xref:System.Diagnostics.DebuggerVisualizerAttribute> 。 `Target`屬性會設定要視覺化的型別。

1. 將下列屬性程式碼新增至 Debuggerside.vb，在指示詞之後， `using` 但在前面 `namespace MyFirstVisualizer` ：

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. 在 [ **組建** ] 功能表上，選擇 [ **組建 MyFirstVisualizer**]。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

   這時，您的第一個視覺化檢視已完成。 如果您正確遵循這些步驟的話，應該能夠建置視覺化檢視，並將它安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。 但是，在將視覺化檢視安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之前，應該先進行測試以確定它能正確執行。 現在，您將建立 Test Harness 來執行這個視覺化檢閱，而不將它安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>新增顯示視覺化檢視的測試方法

1. 將下列方法加入至 `public DebuggerSide` 類別：

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. 在 [ **組建** ] 功能表上，選擇 [ **組建 MyFirstVisualizer**]。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。

   接下來，您必須建立可執行的專案，以呼叫視覺化檢視的 DLL。 為了簡單起見，請使用主控台應用程式專案。

### <a name="to-add-a-console-application-project-to-the-solution"></a>若要將主控台應用程式專案加入至方案

1. 在方案總管中，以滑鼠右鍵按一下方案，選擇 [**加入**]，然後按一下 [**新增 Project**。

    ::: moniker range=">=vs-2019"

    選擇 **[** 檔案  >  **新增**  >  **Project**]。 在 [語言] 下拉式清單中，選擇 [ **c #**]。 在 [搜尋] 方塊中，輸入 **主控台應用** 程式，然後選擇主控台應用程式 **(.NET Framework)** 或適用于 .net 的 **主控台應用程式**。 按一下 [下一步] 。 在出現的對話方塊中，輸入名稱，然後 `MyTestConsole` 按一下 [ **建立**]。

    > [!NOTE]
    > 如果您想要使用測試控管輕鬆地測試視覺化檢視，請建立 .NET Framework 主控台應用程式。 您可以改為建立 .NET 主控台應用程式，但 .NET 尚未支援稍後所述的測試控管，因此您必須安裝視覺化程式來進行測試。 針對 .NET 主控台應用程式，請先在這裡建立主控台應用程式，並新增必要的 DLL 和專案參考，然後依照 [加入偵錯工具端資料物件](#add-a-debuggee-side-data-object)中所述的步驟進行。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **Project**]。 在 [新增專案] 對話方塊左窗格的 [Visual C#] 下，選擇 [Windows Desktop]，然後在中間窗格中選擇 [主控台應用程式 (.NET Framework)]。

    輸入類別庫的適當名稱（例如），然後 `MyTestConsole` 按一下 **[確定]**。
    ::: moniker-end

   此時，你必須加入必要的參考，如此 MyTestConsole 才能呼叫 MyFirstVisualizer。

### <a name="to-add-necessary-references-to-mytestconsole"></a>若要將必要參考加入至 MyTestConsole

1. 在 **方案總管** 中，以滑鼠右鍵按一下 **MyTestConsole** ，然後選擇快捷方式功能表上的 [ **加入參考** ]。

2. 在 [ **加入參考** ] 對話方塊的 **[流覽** ] 索引標籤中，選擇 [Microsoft.VisualStudio.DebuggerVisualizers.DLL]。

3. 按一下 [確定]  。

4. 以滑鼠右鍵按一下 **MyTestConsole** ，然後選擇 [ **加入參考** ]。

5. 在 [ **加入參考** ] 對話方塊中，按一下 [ **專案** ] 索引標籤，然後按一下 [MyFirstVisualizer]。

6. 按一下 [確定]  。

   現在，您就可以加入程式碼來完成測試載入器。

### <a name="to-add-code-to-mytestconsole"></a>若要將程式碼加入至 MyTestConsole

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [Program]，然後在快捷方式功能表上選擇 [ **重新命名** ]。

2. 將 Program. .cs 的名稱編輯成更有意義的名稱，例如 Testconsole.vb .cs。

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 自動變更 Testconsole.vb 中的類別宣告，使其符合新的檔案名。

3. 在 Testconsole.vb 中，將下列程式碼新增至指示詞 `using` ：

   ```csharp
   using MyFirstVisualizer;
   ```

4. 在 `Main` 方法中，加入下列程式碼：

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   現在，您已經準備好可以測試第一個視覺化檢視。

### <a name="to-test-the-visualizer"></a>若要測試視覺化檢視

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **MyTestConsole** ]，然後選擇快捷方式功能表上的 [**設定為啟動 Project** ]。

2. 在 [偵錯] 功能表上選擇 [啟動]。

    主控台應用程式隨即啟動，並出現視覺化檢視，並顯示 "Hello，World" 字串。

   恭喜。 您剛建立並測試了第一個視覺化檢視！

   如果您想在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用視覺化檢閱，而不只是從測試控管中進行呼叫，就必須安裝該視覺化檢閱。 如需詳細資訊，請參閱 [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)。

::: moniker range=">=vs-2019"
## <a name="add-a-debuggee-side-data-object"></a>加入調試的端資料物件

在本節中，您會從 `System.String` 資料物件切換至自訂資料物件。  

1. 在方案總管中，以滑鼠右鍵按一下方案，選擇 [**加入**]，然後按一下 [**新增 Project**。 在 [語言] 下拉式清單中，選擇 [ **c #**]。 在 [搜尋] 方塊中，輸入 **類別庫**，然後選擇 [**類別庫] (.NET Framework)** 或 **類別庫** 以進行 .NET Standard。

   >[!NOTE]
   >如果您使用 .NET Framework 測試主控台應用程式，請確定您已建立 .NET Framework 類別庫專案。

1. 按一下 [下一步] 。 在出現的對話方塊中，輸入名稱，然後 `MyDataObject` 按一下 [ **建立**]。

1.  ( .NET Standard 類別庫僅) 方案總管中，請以滑鼠右鍵按一下專案，然後選擇 [**編輯 Project** 檔]。 將 `<TargetFramework>` 值變更為 `netstandard2.0` 。

   ```xml
   <TargetFramework>netstandard2.0</TargetFramework>
   ```

1. 在 `MyDataObject` 命名空間內，將預設程式碼取代為下列程式碼。

   ```csharp
   [Serializable] 
   public class CustomDataObject
   {
      public CustomDataObject()
      {
         this.MyData = "MyTestData";
      }
      public string MyData { get; set; }
   }
   ```

   針對唯讀的視覺化程式，例如在此範例中，不需要實 [VisualizerObjectSource](/dotnet/api/microsoft.visualstudio.debuggervisualizers.visualizerobjectsource)的方法。

   接下來，將 MyFirstVisualizer 專案更新為使用新的資料物件。

1. 在 [MyFirstVisualizer] 專案底下的方案總管中，以滑鼠右鍵按一下 [ **參考** ] 節點，然後選擇 [ **加入參考**]。

1. 在 [ **專案**] 底下，選取 [ **MyDataObject** ] 專案。

1. 在 Debuggerside.vb 的屬性程式碼中，更新目標值， `System.String` 並將變更為 `MyDataObject.CustomDataObject` 。

   ```csharp
   Target = typeof(MyDataObject.CustomDataObject),
   ```

1. 在 MyFirstVisualizer 專案中，將方法的程式碼取代為 `Show` 下列程式碼。

   ```csharp
   var data = objectProvider.GetObject() as MyDataObject.CustomDataObject;

   // You can replace displayForm with your own custom Form or Control.  
   Form displayForm = new Form();
   displayForm.Text = data.MyData;
   windowService.ShowDialog(displayForm);
   ```

   上述程式碼會使用資料物件的屬性，以表單的標題顯示。

   接下來，更新主控台應用程式以使用自訂資料物件。

1. 在 [MyTestConsole] 專案底下的方案總管中，以滑鼠右鍵按一下 [ **參考** ] 或 [相依性 **]** 節點，並將專案參考加入至 `MyDataObject` 。

1. 在程式 .cs 中，以下列程式碼取代方法中的程式碼 `Main` 。

   ```csharp
   // String myString = "Hello, World";
   CustomDataObject customDataObject = new CustomDataObject();

   DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   ```

1.  ( .NET 主控台應用程式) 將的呼叫括 `TestShowVisualizer` 在 try-catch 語句中，因為不支援測試控管。

   ```csharp
   try
   {
         DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   }
   catch (Exception) {
   }
   ```

   主控台應用程式需要對視覺化檢視的執行時間參考。 您可以保留先前的程式碼來維護參考，而不是將其批註化。

1. 針對 .NET Framework 主控台應用程式，您可以 (按 **F5**) 執行測試控管，也可以依照 [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)中的指示進行。

   如果您使用測試控管來執行應用程式，應用程式會顯示 Windows 表單。

1. 若為 .NET 主控台應用程式，請將 `MyFirstVisualizer.dll` 和複製 `MyDataObject.dll` 到 how [To：安裝視覺化](../debugger/how-to-install-a-visualizer.md)程式中所述的資料夾。

1. 安裝視覺化檢視之後，請設定中斷點，執行主控台應用程式，並將滑鼠停留在上方 `customDataObject` 。 如果一切都已正確設定，您應該會看到放大鏡圖示 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")。

   :::image type="content" source="../debugger/media/vs-2019/visualizer-csharp-data-object.png" alt-text="視覺化檢視放大鏡圖示。":::

   當您從放大鏡選擇 [ **MyFirstVisualizer** ] 時，您會在標題中看到含有資料物件文字的表單。

   ![顯示 Windows 表單的視覺化](../debugger/media/vs-2019/visualizer-csharp-windows-form.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>使用視覺化檢視專案範本建立視覺化

到目前為止，本逐步解說已說明如何以手動方式建立視覺化檢視。 這是做為學習練習的做法。 既然您已經知道簡單的視覺化程式如何運作，有更簡單的方法可以建立一個：使用視覺化程式專案範本。

首先，您必須建立新的類別庫專案。

### <a name="to-create-a-new-class-library"></a>若要建立新的類別庫

1. 在 [檔案] 功能表上，選擇 [新增] > [專案]。

2. 在 [**新增 Project** ] 對話方塊的 [ **Visual c #**] 底下，選取 [ **.NET Framework**]。

3. 在中間窗格中，選擇 [ **類別庫**]。

4. 在 [ **名稱** ] 方塊中，為類別庫輸入適當的名稱，例如 MySecondVisualizer。

5. 按一下 [確定]  。

   現在，您可以在其中新增視覺化檢視專案：

### <a name="to-add-a-visualizer-item"></a>新增視覺化專案

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [MySecondVisualizer]。

2. 在快捷方式功能表上，選擇 [ **加入** ]，然後按一下 [ **新增專案**]。

3. 在 [ **加入新專案** ] 對話方塊的 [ **Visual c # 專案**] 底下，選取 **[偵錯工具視覺化**]。

4. 在 [ **名稱** ] 方塊中，輸入適當的名稱，例如 SecondVisualizer .cs。

5. 按一下 **[新增]** 。

   這就是這樣的。 查看 SecondVisualizer 的檔案，並查看範本為您新增的程式碼。 請繼續進行，並使用程式碼進行實驗。 既然您已經瞭解基本概念，就可以開始建立更複雜且有用的視覺化檢視。
::: moniker-end

## <a name="see-also"></a>另請參閱

- [視覺化架構](../debugger/visualizer-architecture.md)
- [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)
- [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)
