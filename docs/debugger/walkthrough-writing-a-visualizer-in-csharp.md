---
title: "逐步解說： 在 C# 中撰寫視覺化檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6e161b3c914d0a87a720f1217b52a571b85f5ff9
ms.sourcegitcommit: 03a74d29a1e0584ff4808ce6c9e812b51e774905
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2018
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>逐步解說：在 C# 中撰寫視覺化檢視 #
本逐步解說示範如何使用 C# 撰寫簡單的視覺化檢視。 您將在本逐步解說中建立的視覺化檢視會顯示使用 Windows form 訊息方塊字串內容。 這個簡易字串視覺化檢視不是特別適用於本身，但它會顯示建立更有用的視覺化檢視其他資料類型時，必須遵循的基本步驟。  
  
> [!NOTE]
>  根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更您的設定，請移至**工具**功能表，然後選擇 **匯入和匯出設定**。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
 視覺化檢視程式碼必須放置在 DLL 中，以偵錯工具會讀取。 因此，第一個步驟是為 DLL 建立類別庫專案。  

## <a name="create-a-visualizer-manually"></a>手動建立視覺化檢視

請遵循下建立視覺化檢視的工作。
  
#### <a name="to-create-a-class-library-project"></a>若要建立類別庫專案  
  
1.  在**檔案**功能表上，選擇**新增 > 專案**。  
  
2.  在**新專案**對話方塊的  **Visual C#**，選取**.NET 標準**。  
  
3.  在中間窗格中，選擇 **類別庫**。  
  
4.  在**名稱**方塊中，輸入適當的名稱，為該類別庫，例如 MyFirstVisualizer。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
 建立類別庫之後，您必須加入 Microsoft.VisualStudio.DebuggerVisualizers.DLL 的參考，好讓您可以使用定義的類別那里。 將參考加入之前，不過，您必須重新命名一些類別，才有意義的名稱。  
  
#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>若要將 Class1.cs 重新命名和加入 Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下 Class1.cs，然後選擇 [**重新命名**快顯功能表。  
  
2.  將名稱從 Class1.cs 變更為有意義，例如 debuggerside.cs 中的項目。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]自動變更的類別宣告在 debuggerside.cs 中，以符合新的檔案名稱。  
  
3.  在**方案總管 中**，以滑鼠右鍵按一下**參考**選擇**加入參考**快顯功能表。  
  
4.  在**加入參考**對話方塊**.NET**索引標籤上，選擇 Microsoft.VisualStudio.DebuggerVisualizers.DLL。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
6.  在 DebuggerSide.cs 中，將下列陳述式加入至 `using` 陳述式：  
  
    ```csharp  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 現在您已準備好要建立的偵錯工具端程式碼。 這是在偵錯工具內執行的程式碼，用以顯示您要視覺化的資訊。 首先，您必須變更的宣告`DebuggerSide`物件，以便繼承自基底類別`DialogDebuggerVisualizer`。  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>若要繼承自 DialogDebuggerVisualizer  
  
1.  在 debuggerside.cs 中，請移至下列程式碼行：  
  
    ```csharp  
    public class DebuggerSide  
    ```  
  
2.  將程式碼變更：  
  
    ```csharp  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer`有一個抽象方法 (`Show`)，您必須覆寫。  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>若要覆寫 DialogDebuggerVisualizer.Show 方法  
  
-   在`public class DebuggerSide`，加入下列**方法：**  
  
    ```csharp  
    protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 `Show`方法包含實際建立視覺化檢視對話方塊或其他使用者介面，並顯示已從 偵錯工具傳遞至視覺化檢視的資訊的程式碼。 您必須加入該程式碼，以建立對話方塊並顯示資訊。 在本逐步解說中，將您使用 Windows form 訊息方塊。 首先，您必須加入參考和`using`System.Windows.Forms 陳述式。  
  
#### <a name="to-add-systemwindowsforms"></a>若要加入 System.Windows.Forms  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下**參考**選擇**加入參考**快顯功能表。  
  
2.  在**加入參考**對話方塊**.NET**索引標籤上，選擇 System.Windows.Forms.DLL。  
  
3.  按一下 [確定 **Deploying Office Solutions**]。  
  
4.  在 DebuggerSide.cs 中，將下列陳述式加入至 `using` 陳述式：  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
 現在，您會加入一些程式碼來建立並顯示視覺化檢視的使用者介面。 因為這是您的第一個視覺化檢視，我們將簡化使用者介面，並使用訊息方塊。  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>在對話方塊中顯示視覺化檢視輸出  
  
1.  在 `Show` 方法中，加入下列程式碼行：  
  
    ```csharp  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     這個程式碼範例不包括錯誤處理。 您應該包含在真實的視覺化檢視或任何其他種類的應用程式中處理的錯誤。  
  
2.  在**建置**功能表上，選擇**建置 MyFirstVisualizer**。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。  
  
 這是偵錯工具端程式碼的結尾。 不過這會產生一個步驟，;之屬性的類別集合的告知偵錯項目端構成視覺化檢視。  
  
#### <a name="to-add-the-debuggee-side-code"></a>若要加入的偵錯項目端程式碼  
  
1.  之後，將下列屬性程式碼加入至 debuggerside.cs 中，`using`陳述式之前`namespace MyFirstVisualizer`:  
  
    ```csharp  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target = typeof(System.String),  
    Description = "My First Visualizer")]  
    ```  
  
2.  在**建置**功能表上，選擇**建置 MyFirstVisualizer**。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。  
  
 這時，您的第一個視覺化檢視已完成。 如果您正確遵循這些步驟的話，應該能夠建置視覺化檢視，並將它安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。 但是，在將視覺化檢視安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之前，應該先進行測試以確定它能正確執行。 現在，您將建立 Test Harness 來執行這個視覺化檢視，而不將它安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>若要加入測試方法以顯示視覺化檢視  
  
1.  將下列方法加入至 `public DebuggerSide` 類別：  
  
    ```csharp  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  在**建置**功能表上，選擇**建置 MyFirstVisualizer**。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。  
  
 接下來，您必須建立可執行的專案，以呼叫視覺化檢視的 DLL。 為了簡單起見，我們將使用的主控台應用程式專案。  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>若要將主控台應用程式專案加入至方案  
  
1.  在**檔案**功能表上，選擇**新增**，然後按一下 **新專案**。  
  
2.  在**加入新的專案**對話方塊中，於**範本**方塊中，選擇**主控台應用程式**。  
  
3.  在**名稱**方塊中，輸入有意義的名稱，為主控台應用程式，例如`MyTestConsole`。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
 此時，你必須加入必要的參考，如此 MyTestConsole 才能呼叫 MyFirstVisualizer。  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>若要將必要參考加入至 MyTestConsole  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下**MyTestConsole**選擇**加入參考**快顯功能表。  
  
2.  在**加入參考**對話方塊中， **.NET**索引標籤上，選擇 Microsoft.VisualStudio.DebuggerVisualizers.DLL。  
  
3.  按一下 [確定 **Deploying Office Solutions**]。  
  
4.  以滑鼠右鍵按一下**MyTestConsole**選擇**加入參考**一次。  
  
5.  在**加入參考**對話方塊中，按一下 **專案**索引標籤，然後按一下 MyFirstVisualizer。  
  
6.  按一下 [確定 **Deploying Office Solutions**]。  
  
 現在，您就可以加入程式碼來完成測試載入器。  
  
#### <a name="to-add-code-to-mytestconsole"></a>若要將程式碼加入至 MyTestConsole  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下 Program.cs，然後選擇 [**重新命名**快顯功能表。  
  
2.  編輯變得更有意義，例如 TestConsole.cs Program.cs 的名稱。  
  
     **請注意** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] TestConsole.cs 以符合新的檔案名稱中的類別宣告會自動變更。  
  
3.  在 TestConsole.cs，加入下列程式碼`using`陳述式：  
  
    ```csharp  
    using MyFirstVisualizer;  
    ```  
  
4.  在 `Main` 方法中，加入下列程式碼：  
  
    ```csharp  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 現在，您就準備好要測試第一個視覺化檢視。  
  
#### <a name="to-test-the-visualizer"></a>若要測試視覺化檢視  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下**MyTestConsole**選擇**設定為啟始專案**快顯功能表。  
  
2.  在**偵錯**功能表上，選擇**啟動**。  
  
     主控台應用程式啟動並顯示視覺化檢視，並顯示字串"Hello，World"。  
  
 恭喜您！ 您已完成建置和測試第一個視覺化檢視。  
  
 如果您想在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用視覺化檢視，而不只是從測試控管中進行呼叫，就必須安裝該視覺化檢視。 如需詳細資訊，請參閱[如何： 安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)。  
  
## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>建立使用視覺化檢視項目範本的視覺化檢視  
 目前為止，本逐步解說示範了如何以手動方式建立視覺化檢視。 這項作業完成，做為學習練習。 您現在知道簡易的視覺化檢視的運作方式，是建立一個更簡單的方法： 使用視覺化檢視項目範本。  
  
 首先，您必須建立新的類別庫專案。  
  
#### <a name="to-create-a-new-class-library"></a>若要建立新的類別庫  
  
1.  在**檔案**功能表上，選擇**新增 > 專案**。  
  
2.  在**新專案**對話方塊的  **Visual C#**，選取**.NET 標準**。  
  
3.  在中間窗格中，選擇 **類別庫**。   
  
4.  在**名稱**方塊中，輸入適當的類別庫，例如 MySecondVisualizer 的名稱。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
 現在，您可以將視覺化檢視項目：  
  
#### <a name="to-add-a-visualizer-item"></a>若要加入的視覺化檢視項目  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下 MySecondVisualizer。  
  
2.  在捷徑功能表上選擇 **新增**，然後按一下 **新項目**。  
  
3.  在**加入新項目**對話方塊的  **Visual C# 項目**，選取**偵錯工具視覺化檢視**。  
  
4.  在**名稱**方塊中，輸入適當的名稱，例如 SecondVisualizer.cs。  
  
5.  按一下 [加入] 。  
  
 這是所有步驟。 查看 SecondVisualizer.cs 的檔案，並檢視範本新增為您的程式碼。 請繼續並實驗程式碼。 現在，您知道的基本概念，您會在您建立您自己的更複雜且實用的視覺化檢視。  
  
## <a name="see-also"></a>請參閱  
 [視覺化檢視架構](../debugger/visualizer-architecture.md)   
 [如何： 安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)   
 [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)
