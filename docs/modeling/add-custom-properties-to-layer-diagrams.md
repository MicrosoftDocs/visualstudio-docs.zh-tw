---
title: 將自訂屬性新增至相依性圖表
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3623a0c2380188cbb16f6186bddc3f3f2f0c3bd7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590588"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>將自訂屬性新增至相依性圖表

當您撰寫相依性圖表的延伸模組程式碼時，可以使用相依性圖表上的任何元素來儲存值。 當分層圖儲存並重新開啟時，值會保存下來。 您也可以將這些屬性顯示在 [**屬性**] 視窗中，讓使用者可以查看和編輯這些屬性。 例如，您可以讓使用者為每個圖層指定規則運算式，並且撰寫驗證程式碼驗證每個圖層中類別的名稱符合使用者指定的模式。

## <a name="non-visible-properties"></a>非可見屬性

如果您只想要讓程式碼將值附加至相依性圖表中的任何元素，則不需要定義 MEF 元件。 在 [ILayerElement](/previous-versions/ff644511(v=vs.140)) 中, 有一個名為`Properties`的字典。 只要將可封送處理的值加入至任何圖層項目的字典中即可。 這些物件將會儲存為相依性圖表的一部分。

## <a name="editable-properties"></a>可編輯屬性

**初始準備**

> [!IMPORTANT]
> 若要顯示內容，請在您想要讓圖層屬性顯示的每部電腦上進行下列變更：
>
> 1. 使用 [以**系統管理員身分執行**] 來執行 [記事本]。 開啟 *%ProgramFiles%\Microsoft Visual Studio [version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*。
> 2. 在**Content**元素中，新增：
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. 在 [Visual Studio 應用程式開始] 功能表的 [ **Visual Studio Tools** ] 區段下，開啟 [**開發人員命令提示字元**]。 輸入：
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. 重新啟動 Visual Studio。

**請確定您的程式碼位於 VSIX 專案中**

如果您的屬性是命令、手勢或驗證專案的一部分，則不需要加入任何內容。 自訂屬性的程式碼應該在定義為 MEF 元件的 Visual Studio 擴充性專案中定義。 如需詳細資訊，請參閱[將命令和軌跡加入至](../modeling/add-commands-and-gestures-to-layer-diagrams.md)相依性圖表或[將自訂架構驗證加入至](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)相依性圖表。

**定義自訂屬性**

若要建立自訂屬性，請依照下述定義類別：

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

您可以在[ILayerElement](/previous-versions/ff644511(v=vs.140))或其任何衍生類別上定義屬性，包括：

- `ILayerModel` - 模型

- `ILayer` - 每個圖層

- `ILayerDependencyLink` - 圖層之間的連結

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>範例

下列程式碼是典型自訂屬性描述元。 它會在圖層模型上定義布林值屬性 (`ILayerModel`)，而圖層模型可讓使用者提供自訂驗證方法的值。

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>請參閱

- [擴充相依性圖表](../modeling/extend-layer-diagrams.md)
