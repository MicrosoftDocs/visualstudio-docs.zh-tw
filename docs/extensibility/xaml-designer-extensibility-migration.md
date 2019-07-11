---
title: XAML 設計工具擴充性移轉
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 52bc8a6a0097d255891f4b6111a27bff85091bec
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67784478"
---
# <a name="xaml-designer-extensibility-migration"></a>XAML 設計工具擴充性移轉

從 Visual Studio 2019 的公開預覽版的版本 16.1，XAML 設計工具支援兩個不同的架構： 設計工具的隔離架構和較新的介面的隔離架構。 此架構轉換，才能支援.NET Framework 處理序中的目標執行階段無法裝載。 移至介面的隔離架構的協力廠商擴充性模型有重大變更。 本文章概述所做的變更。

**設計工具的隔離**WPF 設計工具用於.NET Framework 為目標的專案，並支援 *。 design.dll*延伸模組。 使用者程式碼、 控制項程式庫，以及協力廠商延伸模組會載入在外部處理序 (*XDesProc.exe*) 以及實際的設計工具程式碼和設計工具的面板。

**介面隔離**UWP 設計工具正在使用。 它也會在 WPF 設計工具的.NET Core 為目標的專案。 介面隔離，唯一的使用者程式碼和控制項程式庫中所載入不同的處理序時在設計工具和其面板載入 Visual Studio 處理序 (*DevEnv.exe*)。 用來執行使用者程式碼和控制項程式庫的執行階段是不同的.NET framework 用於實際的設計工具和協力廠商擴充性程式碼。

![extensibility-migration-architecture](media/xaml-designer-extensibility-migration-architecture.png)

此架構的轉換，因為不會再會載入協力廠商控制項程式庫相同的程序的第三方擴充功能。 不會再擴充功能可以對控制項程式庫的直接相依性，或直接存取執行階段物件。 先前撰寫的設計工具的隔離架構使用的延伸模組*Microsoft.Windows.Extensibility.dll* API 都必須移轉至新的方法來使用介面的隔離架構。 在實務上，現有的延伸模組必須針對新的擴充性 API 組件進行編譯。 存取執行階段控制類型透過[typeof](/dotnet/csharp/language-reference/keywords/typeof)或必須取代或移除，因為控制項程式庫現在會在不同的處理序中載入執行階段執行個體。

## <a name="new-extensibility-api-assemblies"></a>新的擴充性 API 組件

新的擴充性 API 組件是類似於現有的擴充性 API 組件，但遵循不同的命名配置，才能加以區隔。 同樣地，命名空間名稱會變更以反映新的組件名稱。

| 設計工具隔離 API 組件            | 介面隔離 API 組件                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>新的副檔名和探索

而不是使用 *。 design.dll*副檔名，延伸模組會使用所探索到的新介面 *。 designtools.dll*副檔名。 *。 design.dll*並 *。 designtools.dll*延伸模組可以存在於相同*設計*子資料夾。

雖然協力廠商控制項程式庫都實際的目標執行階段 （.NET Core 或 UWP） 針對編譯 *。 designtools.dll*副檔名一律應編譯成.NET Framework 組件。

## <a name="decouple-attribute-tables-from-runtime-types"></a>減少從執行階段類型的屬性資料表

介面隔離擴充性模型不允許為相依於實際控制項程式庫的延伸模組，因此，擴充功能時，無法從控制項程式庫參考類型。 例如， *MyLibrary.designtools.dll*上不應該有相依性*MyLibrary.dll*。

註冊類型會透過屬性資料表的中繼資料時，這類相依性是最常見的。 參考控制項程式庫的延伸模組程式碼類型直接透過[typeof](/dotnet/csharp/language-reference/keywords/typeof) ([GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) Visual Basic 中) 新的 Api 中使用字串型別名稱用來替代：

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Metadata;
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

[assembly: ProvideMetadata(typeof(AttributeTableProvider))]

public class AttributeTableProvider : IProvideAttributeTable
{
  public AttributeTable AttributeTable
  {
    get
    {
      AttributeTableBuilder builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Metadata
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

<Assembly: ProvideMetadata(GetType(AttributeTableProvider))>

Public Class AttributeTableProvider
    Implements IProvideAttributeTable

    Public ReadOnly Property AttributeTable As AttributeTable Implements IProvideAttributeTable.AttributeTable
        Get
            Dim builder As New AttributeTableBuilder
            builder.AddCustomAttributes("MyLibrary.MyControl", New DescriptionAttribute(Strings.MyControlDescription))
            builder.AddCustomAttributes("MyLibrary.MyControl", New FeatureAttribute(GetType(MyControlDefaultInitializer)))
            Return builder.CreateTable()
        End Get
    End Property
End Class
```

## <a name="feature-providers-and-model-api"></a>功能提供者和模型 API

功能提供者是在延伸模組組件中實作，而且 Visual Studio 處理序中載入。 `FeatureAttribute` 將會繼續參照功能提供者型別使用直接[typeof](/dotnet/csharp/language-reference/keywords/typeof)。

功能提供者現在會與實際的執行階段程式碼和控制項程式庫不同的處理序中載入，因為他們就不再能夠直接存取執行階段物件。 相反地，所有這類互動必須轉換成使用對應以模型為基礎的 Api。 模型 API 已更新，和存取權<xref:System.Type>或是<xref:System.Object>是無法再使用或已被取代`TypeIdentifier`和`TypeDefinition`。

`TypeIdentifier` 表示不具類型用來識別組件名稱的字串。 A`TypeIdenfifier`是可解析成`TypeDefinition`查詢類型有關的其他資訊。 `TypeDefinition` 無法快取執行個體，在 延伸模組程式碼。

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type != null && buttonType != type.IsSubclassOf(buttonType))
{
}
```

```vb
Dim type As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("MyLibrary.MyControl"))
Dim buttonType As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("System.Windows.Controls.Button"))
If type?.IsSubclassOf(buttonType) Then

End If
```

從介面的隔離擴充性 API 集合中移除 Api:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`

使用的 Api`TypeIdentifier`而不是<xref:System.Type>:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* `ViewItem.ItemType`
* `ModelEvent.EventType`
* `ModelEvent.IsEventOfType(Type type)`
* `ModeItem.IsItemOfType(Type type)`
* `ModelParent.CanParent(EditingContext context, ModelItem parent, Type childType)`
* `ModelParent.FindParent(EditingContext context, Type childType, ModelItem startingItem)`
* `ModelParent.FindParent(Type childType, GestureData gestureData)`
* `ModelProperty.IsPropertyOfType(Type type)`
* `ParentAdpater.CanParent(ModelItem parent, Type childType)`
* `ParentAdapter.RedirectParent(ModelItem parent, Type childType)`

使用的 Api`TypeIdentifier`而不是<xref:System.Type>與不再支援建構函式引數：

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

使用的 Api`TypeDefinition`而不是<xref:System.Type>:

* `ModelFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`

使用的 Api`ModelItem`而不是<xref:System.Object>:

* `ModelItemCollection.Insert(int index, object value)`
* `ModelItemCollection.Remove(object value)`
* `ModelItemDictionary.Add(object key, object value)`
* `ModelItemDictionary.ContainsKey(object key)`
* `ModelItemDictionary.Remove(object key)`
* `ModelItemDictionary.TryGetValue(object key, out ModelItem value)`

已知的基本型別想`Int32`， `String`，或`Thickness`可以傳遞至模型 API，為.NET Framework 的執行個體，並將轉換至目標執行階段處理序中對應的物件。 例如：

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

public class MyControlDefaultInitializer : DefaultInitializer
{
  public override void InitializeDefaults(ModelItem item)
  {
    item.Properties["Width"].SetValue(800d);
    base.InitializeDefaults(item);
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

Public Class MyControlDefaultInitializer
    Inherits DefaultInitializer

    Public Overrides Sub InitializeDefaults(item As ModelItem)
        item.Properties!Width.SetValue(800.0)
        MyBase.InitializeDefaults(item)
    End Sub
End Class
```

## <a name="limited-support-for-designdll-extensions"></a>有限支援。 design.dll 延伸模組

如果有的話 *。 designtools.dll*延伸模組已探索到的控制項程式庫，就會載入第一個和探索 *。 design.dll*延伸模組會略過。

如果沒有 *。 designtools.dll*擴充均存在，但 *。 design.dll*找到擴充功能、 XAML 語言服務會嘗試載入此組件來擷取屬性的資料表資訊，以支援基本編輯器與屬性偵測器案例。 這項機制會受限於範圍中。 它不允許載入設計工具的隔離執行功能提供者的延伸模組，但可能會提供現有 WPF 控制項程式庫的基本支援。
