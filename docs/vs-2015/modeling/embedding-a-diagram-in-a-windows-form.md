---
title: Windows Form 中內嵌圖表 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 04ecf5bd7bfc91e03f48e624d208a5b4f29b10b7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292522"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>在 Windows Form 中內嵌圖表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以嵌入 Windows 控制項，就會出現在 DSL 圖表[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]視窗。  
  
## <a name="embedding-a-diagram"></a>內嵌圖表  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>若要將內嵌 Windows 控制項的 DSL 圖表  
  
1.  加入新**使用者控制項**DslPackage 專案的檔案。  
  
2.  將面板控制項新增至使用者控制項。 此面板會包含 DSL 圖表。  
  
     新增您需要其他控制項。  
  
     設定控制項的錨點屬性。  
  
3.  在 方案總管 中，以滑鼠右鍵按一下 使用者控制項檔案，然後按一下 **檢視程式碼**。 加入程式碼的這個建構函式和變數：  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4.  將新檔案新增至 DslPackage 專案中，使用下列內容：  
  
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
  
5.  若要測試 DSL，按下 f5 鍵，並開啟範例模型檔案。 在控制項內顯示圖表。 [工具箱] 和其他功能可以正常運作。  
  
#### <a name="updating-the-form-using-store-events"></a>更新使用市集事件表單  
  
1.  在表單設計工具中，加入**ListBox**名為`listBox1`。 這會在模型中顯示的項目清單。 它將會保留在模型使用 synchronism*儲存事件*。 如需詳細資訊，請參閱 <<c0> [ 事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
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
  
3.  在使用者控制項背後的程式碼，插入方法，以接聽新增和移除的項目：  
  
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
  
4.  若要測試 DSL，請按 F5 在實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，開啟範例模型檔案。  
  
     請注意，清單方塊會顯示在模型中，項目清單，並確認它正確之後任何新增或刪除作業，以及復原與取消復原之後。  
  
## <a name="see-also"></a>另請參閱  
 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)

