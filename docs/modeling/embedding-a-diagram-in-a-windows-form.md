---
title: 在 Windows Form 中內嵌圖表
description: 瞭解如何將 DSL 圖表內嵌在 Windows 控制項中，這會出現在 Visual Studio 視窗中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4db60267b835882a69a08c990af644b902697bad
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388980"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>在 Windows Form 中內嵌圖表

您可以將 DSL 圖表內嵌在 Windows 控制項中，它會出現在 Visual Studio 視窗中。

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>在 Windows 控制項中內嵌 DSL 圖表

1. 將新的 **使用者控制項** 檔加入至 DslPackage 專案。

2. 將面板控制項新增至使用者控制項。 此面板會包含 DSL 圖表。

     加入您需要的其他控制項。

     設定控制項的錨點屬性。

3. 在方案總管中，以滑鼠右鍵按一下使用者控制項檔案，然後按一下 [ **視圖程式碼**]。 將此函式和變數新增至程式碼：

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. 將新檔案新增至 DslPackage 專案，其中包含下列內容：

    ```csharp
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }
    ```

5. 若要測試 DSL，請按 **F5** 並開啟範例模型檔案。 此圖表會出現在控制項內。 [工具箱] 和其他功能正常運作。

## <a name="update-the-form-using-store-events"></a>使用 store 事件更新表單

1. 在表單設計工具中，加入名為的 **ListBox** `listBox1` 。 這會顯示模型中的元素清單。 它會使用 *存放區事件* 與模型進行同步處理。 如需詳細資訊，請參閱 [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

2. 在自訂程式碼檔案中，覆寫 DocView 類別的其他方法：

    ```csharp
    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }
    ```

3. 在使用者控制項背後的程式碼中，插入方法來接聽新增和移除的元素：

    ```csharp
    public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }
    ```

4. 若要測試 DSL，請按 **F5** ，在 Visual Studio 的實驗實例中，開啟範例模型檔案。

     請注意，清單方塊會顯示模型中的專案清單，並且在任何新增或刪除之後，以及復原和重做之後都是正確的。

## <a name="see-also"></a>另請參閱

- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
