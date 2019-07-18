---
title: 建立 Windows Form 架構特定領域語言 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 452318ff-8ecf-46d0-8ca0-4013d0cdafaf
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b93518a6ca5fa6464bf8f2e72f11cfa90b4dd4dd
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825597"
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>建立 Windows Form 架構之網域指定的語言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Windows Form 顯示定義域專屬語言 (DSL) 模型，而不是使用 DSL 圖表的狀態。 本主題將逐步引導您繫結至 DSL 的 Windows Form，並透過[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Visualization and Modeling SDK。  

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
DSL 執行個體，顯示 Windows Form 使用者介面和 [模型總管] 中。  

## <a name="creating-a-windows-forms-dsl"></a>建立 Windows Form DSL  
 **最小 WinForm 設計工具**DSL 」 範本會建立最少的 DSL，您可以修改以符合您自己的需求。  

#### <a name="to-create-a-minimal-winforms-dsl"></a>若要建立的最小的 WinForms DSL  

1. 建立從 DSL**最小 WinForm 設計工具**範本。  

    在本逐步解說中，會假設下列名稱：  

   |                       |                 |
   |-----------------------|-----------------|
   | 方案和 DSL 的名稱 |     FarmApp     |
   |       命名空間       | Company.FarmApp |

2. 第一個範本提供的範例實驗：  

   1. 轉換所有範本。  

   2. 建置並執行範例 (**CTRL + F5**)。  

   3. 在 Visual Studio 的實驗性執行個體，開啟`Sample`偵錯的專案中的檔案。  

        請注意，它會顯示 Windows Form 控制項中。  

        您也可以查看 [總管] 中顯示的模型項的目。  

        加入一些項目，無論是在表單 或 總管 中，並請注意，它們會出現在其他的顯示。  

   在主要執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，請注意下列有關 DSL 方案的重點：  

- `DslDefinition.dsl` 不包含任何圖表項目。 這是因為您不會使用 DSL 圖表來檢視此 DSL 的執行個體模型。 相反地，您會將 Windows 表單繫結至模型，並在表單上的項目會顯示模型。  

- 除了`Dsl`並`DslPackage`專案的方案包含名為的第三個專案`UI.` **UI**專案包含 Windows Forms 控制項的定義。 `DslPackage` 取決於`UI`，並`UI`取決於`Dsl`。  

- 在 `DslPackage`專案中，`UI\DocView.cs`包含顯示 Windows Form 控制項中所定義的程式碼`UI`專案。  

- `UI`專案包含表單控制項繫結至 DSL 的工作範例。 不過，它將無法運作時變更 DSL 定義中。 `UI`專案包含：  

  - 名為 Windows Form 類別`ModelViewControl`。  

  - 名為的檔案`DataBinding.cs`，其中包含的其他部分定義`ModelViewControl`。 若要查看其內容，在**方案總管**，開啟檔案的捷徑功能表，然後選擇**檢視程式碼**。  

### <a name="about-the-ui-project"></a>關於在 UI 專案  
 當您更新 DSL 定義檔案，以定義您自己的 DSL 時，您必須更新中的控制項`UI`專案以顯示您的 DSL。 不同於`Dsl`並`DslPackage`專案，此範例`UI`專案不從產生`DslDefinitionl.dsl`。 您可以加入產生程式碼，如果您想，雖然這不涵蓋在本逐步解說.tt 檔案。  

## <a name="updating-the-dsl-definition"></a>更新 DSL 定義  
 下列 DSL 定義會在本逐步解說。  

 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")  

#### <a name="to-update-the-dsl-definition"></a>若要更新 DSL 定義  

1. 在 DSL 設計工具中開啟 DslDefinition.dsl。  

2. 刪除**ExampleElement**  

3. 重新命名**ExampleModel**領域類別`Farm`。  

     為它提供額外的網域屬性，名為`Size`型別的**Int32**，以及`IsOrganic`型別的**布林**。  

    > [!NOTE]
    > 如果您刪除根網域類別，然後再建立新的根目錄，您必須重設的編輯器的根類別屬性。 在  **DSL Explorer**，選取**編輯器**。 然後在 [屬性] 視窗中，將**根類別**至`Farm`。  

4. 使用**具名網域類別**工具來建立下列網域類別：  

    - `Field` – 讓這名為其他網域屬性`Size`。  

    - `Animal` – 在 [屬性] 視窗中，設定**繼承修飾詞**要**抽象**。  

5. 使用**網域類別**工具來建立下列類別：  

    - `Sheep`  

    - `Goat`  

6. 使用**繼承**工具，能使`Goat`並`Sheep`繼承自`Animal`。  

7. 使用**嵌入**工具來內嵌`Field`並`Animal`下`Farm`。  

8. 建議您不妨整理圖表。 若要減少重複的項目數目，使用**此處將樹狀子目錄**分葉項目捷徑功能表上的命令。  

9. **轉換所有範本** 工具列中的 方案總管 中。  

10. 建置**Dsl**專案。  

    > [!NOTE]
    > 在這個階段，而且未發生錯誤無法建置其他專案。 不過，我們想要建置 Dsl 專案，使其組件可供使用，資料來源精靈。  

## <a name="updating-the-ui-project"></a>更新 UI 專案  
 現在您可以建立新的使用者控制項，將會顯示儲存在 DSL 模型中的資訊。 若要連接至模型的使用者控制項的最簡單方式是透過資料繫結。 資料繫結名稱為配接器類型**ModelingBindingSource**專為連接到非 VMSDK 介面的 Dsl。  

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>若要定義 DSL 模型做為資料來源  

1. 在 **資料**功能表上，選擇**顯示資料來源**。  

     [資料來源]  視窗隨即開啟。  

     選擇**加入新的資料來源**。 [資料來源組態精靈]  隨即開啟。  

2. 選擇**物件**，**下一步**。  

     依序展開**Dsl**， **Company.FarmApp**，然後選取**伺服陣列**，這是您的模型的根類別。 選擇 [完成]  。  

     在 方案總管**UI**專案現在會包含**Properties\DataSources\Farm.datasource**  

     屬性和關聯性的模型類別會出現在 [資料來源] 視窗。  

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")  

#### <a name="to-connect-your-model-to-a-form"></a>您的模型連接至表單  

1. 在  **UI**專案中，刪除所有現有的.cs 檔案。  

2. 加入新**使用者控制項**檔案名`FarmControl`要**UI**專案。  

3. 在 **資料來源**視窗中的，在下拉式清單功能表**伺服陣列**，選擇**詳細資料**。  

    保留其他屬性的預設設定。  

4. 在 [設計] 檢視中開啟 FarmControl.cs。  

    拖曳**伺服陣列**從 FarmControl 資料來源 視窗。  

    一組控制項隨即出現，其中每一個屬性。 關聯性屬性不會產生的控制項。  

5. 刪除**farmBindingNavigator**。 這也會自動產生在`FarmControl`設計工具中，但它並不適用於此應用程式。  

6. 使用工具箱 中建立兩個執行個體**DataGridView**，並將它們命名`AnimalGridView`和`FieldGridView`。  

   > [!NOTE]
   > 是的動物 」 和 「 欄位項目從資料來源視窗拖曳至控制項的替代步驟。 此動作會自動建立資料格和格線檢視與資料來源之間的繫結。 不過，此繫結運作不正常的 Dsl。 因此最好是建立資料格和繫結以手動方式。  

7. 如果 [工具箱] 中不含**ModelingBindingSource**工具，請將它加入。 在捷徑功能表上**資料**索引標籤上，選擇**選擇項目**。 在 [**選擇工具箱項目**對話方塊中，選取**ModelingBindingSource**從 **.NET Framework] 索引標籤**。  

8. 使用 [工具箱] 中建立兩個執行個體**ModelingBindingSource**，並將它們命名`AnimalBinding`和`FieldBinding`。  

9. 設定**DataSource**每個屬性**ModelingBindingSource**來**farmBindingSource**。  

     設定**DataMember**屬性設**動物**或是**欄位**。  

10. 設定**資料來源**的屬性`AnimalGridView`要`AnimalBinding`，以及`FieldGridView`至`FieldBinding`。  

11. 調整您的體驗的伺服器陣列控制項的版面配置。  

    **ModelingBindingSource**是配接器執行專屬 Dsl 的數個功能：  

- 它會更新包裝在 VMSDK 存放區交易中。  

   例如，當使用者刪除資料列的資料檢視方格中，規則的繫結將會導致交易例外狀況。  

- 它可確保，當使用者選取一個資料列，[屬性] 視窗會顯示對應的模型項目，而不是資料方格資料列的屬性。  

  ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")  
  結構描述資料來源和檢視之間的連結。  

#### <a name="to-complete-the-bindings-to-the-dsl"></a>若要完成的 dsl 的繫結  

1. 不同的程式碼檔案中加入下列程式碼**UI**專案：  

    ```csharp  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  

    namespace Company.FarmApp  
    {  
      partial class FarmControl  
      {  
        public IContainer Components { get { return components; } }  

        /// <summary>Binds the WinForms data source to the DSL model.  
        /// </summary>  
        /// <param name="nodelRoot">The root element of the model.</param>  
        public void DataBind(ModelElement modelRoot)  
        {  
          WinFormsDataBindingHelper.PreInitializeDataSources(this);  
          this.farmBindingSource.DataSource = modelRoot;  
          WinFormsDataBindingHelper.InitializeDataSources(this);  
        }  
      }  
    }  
    ```  

2. 在  **DslPackage**專案中，編輯**DslPackage\DocView.tt**更新下列變數定義：  

    ```csharp  
    string viewControlTypeName = "FarmControl";  
    ```  

## <a name="testing-the-dsl"></a>測試 DSL  
 DSL 方案現在可以建置並執行，不過您可能想要新增其他的增強功能更新版本。  

#### <a name="to-test-the-dsl"></a>若要測試 DSL  

1. 建置並執行方案。  

2. 在 Visual Studio 的實驗性執行個體，開啟**範例**檔案。  

3. 在**FarmApp 總管**，開啟捷徑功能表上**伺服陣列**根節點，然後選擇**加入新的 Goat**。  

     `Goat1` 會出現在**動物**檢視。  

    > [!WARNING]
    > 您必須使用的捷徑功能表上**伺服陣列**節點，不**動物**節點。  

4. 選取 **伺服陣列**根節點，並檢視其屬性。  

     在 [表單] 檢視中，變更**名稱**或是**大小**伺服器陣列。  

     當您離開在表單中，對應的屬性變更，在 [屬性] 視窗中的每個欄位。  

## <a name="enhancing-the-dsl"></a>增強的 DSL  

#### <a name="to-make-the-properties-update-immediately"></a>若要進行立即更新的屬性  

1. 在 FarmControl.cs [設計] 檢視中，選取簡單的欄位，例如名稱、 大小或 IsOrganic。  

2. 在 [屬性] 視窗中，依序展開**DataBindings** ，然後開啟 **（進階）** 。  

     在 [**格式化與進階繫結**] 對話方塊底下**資料來源更新模式**，選擇**OnPropertyChanged**。  

3. 建置並執行方案。  

     請確認當您變更欄位，也就是伺服器陣列模型變更立即的對應屬性的內容。  

#### <a name="to-provide-add-buttons"></a>若要提供新增按鈕  

1. 在 FarmControl.cs 設計 檢視中，使用工具箱 中建立的表單上的按鈕。  

    編輯名稱與文字的按鈕，例如以`New Sheep`。  

2. 開啟 [] 按鈕背後的程式碼 （例如藉由按兩下）。  

    編輯，如下所示：  

   ```csharp  
   private void NewSheepButton_Click(object sender, EventArgs e)  
   {  
     using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
     {  
       elementOperations.MergeElementGroup(farm,  
         new ElementGroup(new Sheep(farm.Partition)));  
       t.Commit();  
     }  
   }  

   // The following code is shared with other add buttons:  
   private ElementOperations operationsCache = null;  
   private ElementOperations elementOperations  
   {  
     get  
     {  
       if (operationsCache == null)  
       {  
         operationsCache = new ElementOperations(farm.Store, farm.Partition);  
       }  
       return operationsCache;  
     }  
   }  
   private Farm farm  
   {  
     get { return this.farmBindingSource.DataSource as Farm; }  
   }  

   ```  

    您也必須插入下列指示詞：  

   ```csharp  

   using Microsoft.VisualStudio.Modeling;  

   ```  

3. 將類似的按鈕加入山羊和欄位。  

4. 建置並執行方案。  

5. 確認 [新增] 按鈕將項目。 在這兩個 FarmApp 總管，然後在適當的資料格檢視中，應該會出現新的項目。  

    您應該能夠編輯的資料格檢視中的項目名稱。 您也可以從那裡刪除它。  

   ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  

### <a name="about-the-code-to-add-an-element"></a>關於程式碼中新增項目  
 新的項目按鈕，如下列替代程式碼則稍微簡單一些。  

```csharp  
private void NewSheepButton_Click(object sender, EventArgs e)  
{  
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
  {  
    farm.Animals.Add(new Sheep(farm.Partition)); ;  
    t.Commit();  
  }  
}  

```  

 不過，此程式碼不會設定新的項目的預設名稱。 它不會執行任何您可能已經定義中的自訂的合併**項目合併指示詞**的 DSL，並不會執行任何可能已定義的自訂合併程式碼。  

 因此我們建議您改用<xref:Microsoft.VisualStudio.Modeling.ElementOperations>來建立新的項目。 如需詳細資訊，請參閱 <<c0> [ 自訂項目的建立和移動](../modeling/customizing-element-creation-and-movement.md)。  

## <a name="see-also"></a>另請參閱  
 [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)   
 [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
