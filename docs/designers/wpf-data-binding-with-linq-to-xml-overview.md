---
title: WPF 資料繫結與 LINQ to XML 概觀
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 3bf80845-891b-41de-a71b-4080b5bd3ea6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da32989ebabb4ef6507f45c652755514f4963ef6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984778"
---
# <a name="wpf-data-binding-with-linq-to-xml-overview"></a>WPF 資料繫結與 LINQ to XML 概觀

這個主題說明 <xref:System.Xml.Linq> 命名空間中的動態資料繫結功能。 這些功能在 Windows Presentation Foundation (WPF) 應用程式中可以當作使用者介面 (UI) 項目的資料來源使用。 這個案例是以 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> 和 <xref:System.Xml.Linq.XElement?displayProperty=fullName> 的「動態屬性」為基礎。

## <a name="xaml-and-linq-to-xml"></a>XAML 和 LINQ to XML

可延伸應用程式標記語言 (XAML) 是由 Microsoft 建立的 XML 語言，用以支援 .NET Framework 3.0 技術。 它在 WPF 中用於表示使用者介面項目與相關功能，例如，事件和資料繫結。 在 Windows Workflow Foundation 中，XAML 可用來表示程式結構，例如程式控制 (「工作流程」)。 XAML 可讓技術的宣告性部分與定義程式更個人化行為的相關程序性程式碼分開。

XAML 和 LINQ to XML 有兩種廣泛的方式可以互動：

- XAML 檔案是語式正確 (Well-Formed) 的 XML，因此可以透過 XML 技術 (例如，LINQ to XML) 進行查詢與管理。

- 由於 LINQ to XML 查詢代表資料的來源，這些查詢可以當做 WPF UI 項目之資料繫結的資料來源使用。

此文件描述第二個案例。

## <a name="data-binding-in-the-windows-presentation-foundation"></a>Windows Presentation Foundation 中的資料繫結

WPF 資料繫結可讓 UI 項目將其屬性中的一個屬性與資料來源產生關聯。 其中一個簡單的範例為 <xref:System.Windows.Controls.Label>，其文字表示使用者定義物件中公用屬性的值。 WPF 資料繫結依賴下列元件：

|元件|說明|
|---------------|-----------------|
|繫結目標|與資料來源相關聯的 UI 項目。 WPF 中的 Visual 項目衍生自 <xref:System.Windows.UIElement> 類別。|
|目標屬性|反映資料繫結來源值的繫結目標「相依性屬性」。 相依性屬性是由 <xref:System.Windows.DependencyObject> 類別 (可衍生 <xref:System.Windows.UIElement>) 直接支援。|
|繫結來源|一或多個值的來源物件，這些值會提供給 UI 項目進行顯示。 WPF 會自動支援下列類型做為繫結來源：CLR 物件、ADO.NET 資料物件、XML 資料 (來自 XPath 或 LINQ to XML 查詢)，或其他 <xref:System.Windows.DependencyObject>。|
|來源路徑|繫結來源的屬性，可解析要繫結的值或值集合。|

相依性屬性為 WPF 專屬的概念，代表 UI 項目動態計算的屬性。 例如，相依性屬性通常具有父項目提供的預設值或值。 這些特殊的屬性是由 <xref:System.Windows.DependencyProperty> 類別 (而非具有標準屬性的欄位) 的執行個體所支援。 如需詳細資訊，請參閱[相依性屬性概觀](/dotnet/framework/wpf/advanced/dependency-properties-overview)。

### <a name="dynamic-data-binding-in-wpf"></a>WPF 中的動態資料繫結

根據預設，只有在初始化目標 UI 項目後，才會發生資料繫結。 這稱為「單次」繫結。 就大部分的用途而言，這還不足夠；資料繫結解決方案通常需要在執行階段，使用下列其中一項，動態傳播這些變更：

- 「單向」繫結會促使自動傳播對一端所做的變更。 最常見的情況下，對來源的變更會反映到目標中，但是反向有時候很有用。

- 在「雙向」繫結中，對來源所做的變更會自動傳播到目標，而對目標所做的變更也會自動傳播到來源。

若要讓單向或雙向繫結發生，來源必須實作變更通知機制，例如，藉由針對支援的每個屬性實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面或使用 *PropertyNameChanged* 模式。

如需有關 WPF 中資料繫結的詳細資訊，請參閱[資料繫結 (WPF)](/dotnet/framework/wpf/data/data-binding-wpf)。

## <a name="dynamic-properties-in-linq-to-xml-classes"></a>LINQ to XML 類別中的動態屬性

多數的 LINQ to XML 類別不會限定為適當的 WPF 動態資料來源。 某些最實用的資訊僅能透過方法而非屬性取得，而且這些類別中的屬性不會實作變更通知。 為了支援 WPF 資料繫結，LINQ to XML 會公開一組「動態屬性」。

這些動態屬性是特殊的執行階段屬性，會在 <xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XElement> 類別中，複製現有方法和屬性的功能。 這些屬性會單獨加入到這些類別中，讓它們當做 WPF 的動態資料來源使用。 為符合這個需求，全部這些動態屬性都要實作變更通知。 下一節 [LINQ to XML 動態屬性](../designers/linq-to-xml-dynamic-properties.md)中會提供這些動態屬性的詳細參考。

> [!NOTE]
> 在 <xref:System.Xml.Linq> 命名空間各種類別中找到的多數標準公用屬性都可以用於一次資料繫結。 不過請記住，在此配置下，不會自動更新來源或目標。

### <a name="accessing-dynamic-properties"></a>存取動態屬性

<xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XElement> 類別中的動態屬性無法像標準屬性般存取。 例如，在 CLR 相容的語言 (例如 C#) 中，這些屬性無法：

- 直接在編譯階段存取。 編譯器和 Visual Studio IntelliSense 看不到動態屬性。

- 在執行階段，使用 .NET 反映尋找或存取。 即使是在執行階段，它們都不是基本 CLR 偵測的屬性。

在 C# 中，動態屬性僅能在執行階段，透過 <xref:System.ComponentModel> 命名空間提供的功能存取。

但是，相較之下，在 XML 原始檔中，動態屬性可以透過下列格式的直接附註存取：

```xml
<object>.<dynamic-property>
```

這兩種類別的動態屬性會解析可直接使用的值，或解析必須隨索引提供的索引子 (Indexer)，才能取得所產生的值或值集合。 後者的語法採用的格式為：

```xml
<object>.<dynamic-property>[<index-value>]
```

如需詳細資訊，請參閱 [LINQ to XML 動態屬性](../designers/linq-to-xml-dynamic-properties.md)。

若要實作 WPF 動態繫結，動態屬性將搭配 <xref:System.Windows.Data> 命名空間 (特別是 <xref:System.Windows.Data.Binding> 類別) 所提供的功能使用。

## <a name="see-also"></a>另請參閱

- [WPF 資料繫結與 LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [LINQ to XML 動態屬性](../designers/linq-to-xml-dynamic-properties.md)
- [WPF 中的 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [資料繫結 (WPF)](/dotnet/framework/wpf/data/data-binding-wpf)
- [使用工作流程標記](http://go.microsoft.com/fwlink/?LinkId=98685)
