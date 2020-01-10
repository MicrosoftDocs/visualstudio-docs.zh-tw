---
title: 覆寫及擴充產生的類別
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3374f67f4fba11543e3dbbca47fef621dd2e714
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595887"
---
# <a name="override-and-extend-the-generated-classes"></a>覆寫及擴充產生的類別

您的 DSL 定義是一種平臺，可讓您建立一組功能強大的工具，並以特定領域語言為基礎。 藉由覆寫和擴充從 DSL 定義產生的類別，可以建立許多擴充功能和採用原音。 這些類別不僅包括您已在 DSL 定義圖中明確定義的網域類別，也包含定義 [工具箱]、[explorer]、[序列化] 等等的其他類別。

## <a name="extensibility-mechanisms"></a>擴充性機制

提供了數種機制，可讓您擴充所產生的程式碼。

### <a name="override-methods-in-a-partial-class"></a>在部分類別中覆寫方法

部分類別定義可讓您在一個以上的位置定義類別。 這可讓您將所產生的程式碼與您自行撰寫的程式碼分開。 在您手動撰寫的程式碼中，您可以覆寫產生的程式碼所繼承的類別。

例如，如果您在 DSL 定義中定義名為 `Book`的網域類別，您可以撰寫自訂程式碼來新增覆寫方法：

```csharp
public partial class Book
{
   protected override void OnDeleting()
   {
      MessageBox.Show("Deleting book " + this.Title);
      base.OnDeleting();
   }
}
```

> [!NOTE]
> 若要覆寫所產生類別中的方法，請一律將您的程式碼寫入與所產生檔案分開的檔案中。 一般來說，檔案會包含在名為 CustomCode 的資料夾中。 如果您對產生的程式碼進行變更，當您從 DSL 定義重新產生程式碼時，將會遺失它們。

若要探索您可以覆寫的方法，請在類別中輸入**override** ，後面加上空格。 IntelliSense 工具提示會告訴您可以覆寫的方法。

### <a name="double-derived-classes"></a>雙重衍生類別

產生之類別中的大部分方法都是從模型命名空間中的一組固定類別繼承而來。 不過，某些方法會在產生的程式碼中定義。 一般來說，這表示您無法覆寫它們;您無法在一個部分類別中覆寫相同類別的另一個部分定義中所定義的方法。

不過，您可以藉由設定網域類別的 [**產生雙重衍生**] 旗標來覆寫這些方法。 這會產生兩個類別，其中一個是另一個的抽象基類。 所有方法和屬性定義都在基類中，而且只有該函式是在衍生類別中。

例如，在範例程式庫中，`CirculationBook` 網域類別的 `Generates``Double Derived` 屬性設定為 `true`。 針對該網域類別所產生的程式碼包含兩個類別：

- `CirculationBookBase`，這是一個抽象的，其中包含所有方法和屬性。

- `CirculationBook`，衍生自 `CirculationBookBase`。 它是空的，但它的函式除外。

若要覆寫任何方法，您可以建立衍生類別的部分定義，例如 `CirculationBook`。 您可以覆寫產生的方法和繼承自模型架構的方法。

您可以使用此方法搭配所有類型的元素，包括模型專案、關聯性、圖形、圖表和連接器。 您也可以覆寫其他產生之類別的方法。 某些產生的類別（例如 ToolboxHelper）一律會是雙重衍生的。

### <a name="custom-constructors"></a>自訂構造函式

您無法覆寫函式。 即使在雙重衍生的類別中，此函式也必須位於衍生類別中。

如果您想要提供自己的函式，可以藉由在 DSL 定義中設定網域類別的 `Has Custom Constructor` 來執行這項操作。 當您按一下 [**轉換所有範本**] 時，產生的程式碼將不會包含該類別的函式。 它將包含對遺漏的函式的呼叫。 當您建立方案時，這會導致錯誤報表。 按兩下錯誤報表，以在產生的程式碼中看到批註，說明您應該提供的內容。

在檔案中撰寫與所產生檔案不同的部分類別定義，並提供此函式。

### <a name="flagged-extension-points"></a>加上旗標的擴充點

有旗標的擴充點是 DSL 定義中的一個位置，您可以在其中設定屬性或核取方塊，以指出您將提供自訂的方法。 自訂的函式是其中一個範例。 其他範例包括將定義域屬性的 `Kind` 設定為計算或自訂儲存體，或在連接產生器中設定**Is Custom**旗標。

在每個案例中，當您設定旗標並重新產生程式碼時，將會產生組建錯誤。 按兩下錯誤以查看說明您必須提供之內容的批註。

### <a name="rules"></a>規則

交易管理員可讓您定義規則，在發生指定事件的交易結束之前執行，例如屬性的變更。 規則通常用來維護存放區中不同元素之間的 synchronism。 例如，規則是用來確保圖表會顯示模型的目前狀態。

規則是以每個類別為基礎來定義，因此您不需要有程式碼為每個物件註冊規則。 如需詳細資訊，請參閱[規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。

### <a name="store-events"></a>儲存事件

模型存放區會提供事件機制，讓您用來接聽存放區中特定類型的變更，包括新增和刪除專案、變更屬性值等等。 事件處理常式會在進行變更的交易關閉後呼叫。 一般而言，這些事件是用來更新存放區以外的資源。

### <a name="net-events"></a>.NET 事件

您可以訂閱一些圖形上的事件。 例如，您可以在圖形上接聽滑鼠按鍵動作。 您必須撰寫程式碼，以訂閱每個物件的事件。 這段程式碼可使用 InitializeInstanceResources （）的覆寫來撰寫。

某些事件會在在 mapcontrol.shapefields 上產生，用來繪製圖形上的裝飾專案。 如需範例，請參閱[如何：攔截圖形或](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)裝飾專案的點擊。

這些事件通常不會發生在交易內。 如果您想要在存放區中進行變更，您應該建立交易。
