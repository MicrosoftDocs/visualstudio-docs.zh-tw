---
title: XAML 設計工具擴充性遷移
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 9f5085c7a655f186c3c8a4a6eecada8b440650cd
ms.sourcegitcommit: 528178a304e66c0cb7ab98b493fe3c409f87493a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273224"
---
# <a name="xaml-designer-extensibility-migration"></a>XAML 設計工具擴充性遷移

在 Visual Studio 2019 中，XAML 設計工具支援兩種不同的架構：設計工具隔離架構和最新的表面隔離架構。 需要此架構轉換，才能支援無法在 .NET Framework 進程中裝載的目標執行時間。 移至介面隔離架構會引進協力廠商擴充性模型的突破性變更。 本文概述從16.3 版開始，Visual Studio 2019 中提供的這些變更。

WPF 設計工具會針對以 .NET Framework 為目標並支援 *. 設計 .dll*副檔名的專案使用**設計工具隔離**。 使用者程式碼、控制項程式庫和協力廠商擴充功能會在外部進程（*xdesproc.exe*）中載入，以及實際的設計工具程式碼和設計工具面板。

UWP 設計工具會使用**介面隔離**。 WPF 設計工具也會針對以 .NET Core 為目標的專案使用它。 在介面隔離中，只有使用者程式碼和控制項程式庫會載入個別的進程中，而設計工具和其面板則會載入 Visual Studio 進程（*DevEnv .exe*）中。 用於執行使用者程式碼和控制項程式庫的執行時間與實際設計工具和協力廠商擴充性程式碼的 .NET Framework 所使用的執行時間不同。

![extensibility-migration-architecture](media/xaml-designer-extensibility-migration-architecture.png)

因為此架構轉換，所以不會再將協力廠商擴充功能載入與協力廠商控制項程式庫相同的程式中。 延伸模組不再具有控制項程式庫的直接相依性，也無法直接存取執行時間物件。 先前針對*使用的設計*工具隔離架構所撰寫的延伸模組，必須遷移至新的方法，才能使用介面隔離架構。 在實務上，現有的延伸模組必須針對新的擴充性 API 元件進行編譯。 必須取代或移除透過[typeof](/dotnet/csharp/language-reference/keywords/typeof)或執行時間實例存取執行時間控制項類型的作業，因為現在已在不同的進程中載入控制項程式庫。

## <a name="new-extensibility-api-assemblies"></a>新的擴充性 API 元件

新的擴充性 API 元件與現有的擴充性 API 元件相似，但會遵循不同的命名配置來區別它們。 同樣地，命名空間名稱已經變更，以反映新的元件名稱。

| 設計工具隔離 API 元件            | Surface 隔離 API 元件                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>新的副檔名和探索

不使用 *. 設計 .dll*副檔名，會使用*designtools*檔案副檔名來探索新的介面擴充。 *.* *designtools 和 .dll*副檔名可以存在於相同的*設計*子資料夾中。

雖然會針對實際的目標執行時間（.NET Core 或 UWP）編譯協力廠商控制項程式庫，但*designtools*副檔名應一律編譯為 .NET Framework 元件。

## <a name="decouple-attribute-tables-from-run-time-types"></a>將屬性資料表與執行時間類型分離

表面隔離擴充性模型不允許延伸模組依賴實際的控制項程式庫，因此擴充功能無法參考控制項程式庫中的類型。 例如， *MyLibrary. designtools*不應該有*MyLibrary*的相依性。

當透過屬性資料表註冊類型的中繼資料時，這種相依性是最常見的。 直接透過[typeof](/dotnet/csharp/language-reference/keywords/typeof)或[GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator)參考控制項程式庫類型的擴充程式碼，會使用以字串為基礎的類型名稱來取代新的 api：

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
      var builder = new AttributeTableBuilder();
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

功能提供者會實作為擴充元件，並在 Visual Studio 程式中載入。 `FeatureAttribute`將繼續直接使用[typeof](/dotnet/csharp/language-reference/keywords/typeof)參考功能提供者類型。

目前支援下列功能提供者：

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`
* `DesignModeValueProvider`支援透過`InvalidateProperty`或在設計工具`TranslatePropertyValue`中修改時所呼叫的限制。 在執行時間程式碼中修改時，不會呼叫它。

因為功能提供者現在已載入與實際執行時間程式碼和控制項程式庫不同的進程中，所以它們無法再直接存取執行時間物件。 相反地，所有這類互動都必須轉換成使用對應的模型型 Api。 模型 API 已更新，而且<xref:System.Type>存取或<xref:System.Object>已無法再使用或已被`TypeIdentifier`和`TypeDefinition`取代。

`TypeIdentifier`表示不含元件名稱來識別類型的字串。 可以解析為，以查詢類型的其他資訊。 `TypeDefinition` `TypeIdenfifier` `TypeDefinition`無法在延伸模組程式碼中快取實例。

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type?.IsSubclassOf(buttonType) == true)
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

從 surface 隔離擴充性 API 集合中移除的 Api：

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`
* `AssemblyReferences.GetTypes(Type baseType)`

使用`TypeIdentifier` 的<xref:System.Type>api，而不是：

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* `ModelFactory.ResolveType(EditingContext context, Type)`已變更為`MetadataFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* `ModelService.ResolveType(TypeIdentifier typeIdentifier)`已變更為`MetadataService.ResolveType(TypeIdentifier typeIdentifier)`
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

使用`TypeIdentifier` 的<xref:System.Type> api （而不是和）不再支援函式引數：

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

使用`TypeDefinition` 的<xref:System.Type>api，而不是：

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
* `PropertyEntry.PropertyType`

使用`AssemblyIdentifier` 的`<xref:System.Reflection.AssemblyName?displayProperty=fullName>`api，而不是：

* `AssemblyReferences.ReferencedAssemblies`
* `AssemblyReferences.LocalAssemblyName`已變更為`AssemblyReferences.LocalAssemblyIdentifier`

此外， `ModelItem`之類`SetValue`的 api 只支援基本類型的實例，或可針對目標執行時間轉換的內建 .NET Framework 類型。 目前支援下列類型：

* 基本 .NET Framework 類型： `Boolean`、 `Byte` `DateTime` `Double` 、`SByte` 、、、 、、`Enum`、、、、 `Guid` `Int16` `Int32` `Char` `Int64` `Nullable`, `Single`, `String`, `Type`, `UInt16`, `UInt32`, `UInt64`,`Uri`
* 已知的 WPF .NET Framework 類型（和衍生類型） `Brush`： `Color`、 `CompositeTransform`、 `CornerRadius` `EasingMode` `EllipseGeometry` `Duration` `EasingFunctionBase` 、、`GeneralTransform`、、 `FontFamily` 、、、、`Geometry`, `GradientStopCollection`, `GradientStop`, `GridLength`, `ImageSource`, `InlineCollection`, `Inline`, `KeySpline`, `Material`, `Matrix`, `PathFigureCollection`, `PathFigure`, `PathSegmentCollection`, `PathSegment`, `Path`, `PointCollection`, `Point`, `PropertyPath`, `Rect`, `RepeatBehavior`, `Setter`, `Size`, `StaticResource`, `TextAlignment`, `TextDecorationCollection`, `ThemeResourceExtension`, `Thickness`, `TimeSpan`, `Transform3D`,`TransformCollection`

例如：

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

如需更多程式碼範例，請在[xaml 設計工具-](https://github.com/microsoft/xaml-designer-extensibility-samples)擴充性範例存放庫中找到。

## <a name="limited-support-for-designdll-extensions"></a>對. 設計 .dll 延伸模組的支援有限

如果針對控制項程式庫探索到任何*designtools .dll*副檔名，則會先載入它，然後再探索。會略過*設計 .dll*副檔名。

如果找不到*designtools*副檔名，但找到 *. design .DLL*副檔名，XAML 語言服務會嘗試載入此元件，以解壓縮屬性工作表資訊，以支援基本編輯器和屬性偵測器案例。 這項機制在範圍內受到限制。 它不允許載入設計工具隔離延伸模組來執行功能提供者，但可能會提供現有 WPF 控制項程式庫的基本支援。
