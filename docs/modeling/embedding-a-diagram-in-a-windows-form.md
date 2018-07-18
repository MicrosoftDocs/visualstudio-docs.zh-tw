---
title: 在 Windows Form 中內嵌圖表
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: db011f9842d00b6a39be3f1e9f4d4d7a090f2581
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950539"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>在 Windows Form 中內嵌圖表
DSL 圖表嵌入 Windows 控制項，它會出現在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]視窗。

## <a name="embedding-a-diagram"></a>內嵌圖表

#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>若要將內嵌 Windows 控制項的 DSL 圖表

1.  加入新**使用者控制項**DslPackage 專案的檔案。

2.  將面板控制項新增至使用者控制項。 此面板會包含 DSL 圖表。

     將您需要其他控制項。

     設定控制項的錨點屬性。

3.  在 方案總管 中，以滑鼠右鍵按一下 使用者控制項檔案，然後按一下**檢視程式碼**。 新增此建構函式和變數的程式碼：

    ```csharp

    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;

    ```

4.  將新檔案加入至 DslPackage 專案中，使用下列內容：

    ```
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

5.  若要測試 DSL，請按 f5 鍵，開啟範例模型檔案。 圖表會顯示在控制項內。 [工具箱] 和其他功能可以正常運作。

#### <a name="updating-the-form-using-store-events"></a>更新使用儲存事件表單

1.  在表單設計工具中，加入**ListBox**名為`listBox1`。 這會在模型中顯示之項目的清單。 它將會保留在模型使用 synchronism*儲存事件*。 如需詳細資訊，請參閱[事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

2.  在自訂程式碼檔案中，覆寫進一步 DocView 類別的方法：

    ```

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

3.  在使用者控制項背後的程式碼，插入方法，以接聽加入和移除的項目：

    ```

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

4.  若要測試 DSL，按 f5 鍵在實驗執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，開啟範例模型檔案。

     請注意，清單方塊會顯示在模型中，元素的清單，並確認它正確之後任何的新增或刪除，以及復原與取消復原之後。

## <a name="see-also"></a>另請參閱

- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
