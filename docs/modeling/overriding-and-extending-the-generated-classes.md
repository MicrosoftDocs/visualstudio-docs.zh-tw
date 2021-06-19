---
title: 覆寫及擴充產生的類別
description: 瞭解 DSL 定義是一個平臺，您可以在其中建立一組功能強大的工具，這些工具是以網域特定語言為基礎。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 07c44e7ff7a603f339ec268b06bd78cc84cd6be2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390941"
---
# <a name="override-and-extend-the-generated-classes"></a>覆寫及擴充產生的類別

您的 DSL 定義是一個平臺，您可以在其中建立一組功能強大的工具，這些工具是以網域特定語言為基礎。 您可以覆寫和擴充從 DSL 定義產生的類別，來建立許多擴充功能和採用原音。 這些類別不僅包括您在 DSL 定義圖中明確定義的網域類別，還包括其他定義 [工具箱]、[explorer]、[序列化] 等等的類別。

## <a name="extensibility-mechanisms"></a>擴充性機制

提供數種機制，可讓您擴充產生的程式碼。

### <a name="override-methods-in-a-partial-class"></a>覆寫部分類別中的方法

部分類別定義可讓您在一個以上的位置定義類別。 這可讓您將產生的程式碼與您自行撰寫的程式碼分開。 在手動撰寫的程式碼中，您可以覆寫產生的程式碼所繼承的類別。

例如，在 DSL 定義中，您可以定義名為的網域類別 `Book` ，您可以撰寫自訂程式碼來新增覆寫方法：

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
> 若要覆寫所產生類別中的方法，請一律將您的程式碼寫入與產生的檔案分開的檔案中。 一般而言，檔案會包含在名為 CustomCode 的資料夾中。 如果您對產生的程式碼進行變更，當您從 DSL 定義重新產生程式碼時，將會遺失這些程式碼。

若要探索您可以覆寫的方法，請在類別中輸入覆 **寫** ，後面接著空格。 IntelliSense 工具提示會告訴您哪些方法可以覆寫。

### <a name="double-derived-classes"></a>Double-Derived 類別

在產生的類別中，大部分的方法都是繼承自模型命名空間中一組固定的類別。 不過，某些方法是在產生的程式碼中定義。 一般來說，這表示您無法覆寫它們;您無法在一個部分類別中覆寫在相同類別的另一個部分定義中所定義的方法。

不過，您可以藉由設定網域類別的 [ **產生雙重衍生** ] 旗標來覆寫這些方法。 這會產生兩個類別，一個是另一個類別的抽象基類。 所有方法和屬性定義都在基類中，而且只有在衍生類別中的函式。

例如，在範例程式庫中， `CirculationBook` 網域類別的 `Generates``Double Derived` 屬性設定為 `true` 。 針對該網域類別產生的程式碼包含兩個類別：

- `CirculationBookBase`，它是抽象的，其中包含所有方法和屬性。

- `CirculationBook`，衍生自 `CirculationBookBase` 。 它是空的，但它的函式除外。

若要覆寫任何方法，您可以建立衍生類別的部分定義，例如 `CirculationBook` 。 您可以覆寫產生的方法，以及繼承自模型架構的方法。

您可以使用這個方法搭配所有類型的元素，包括模型專案、關聯性、圖形、圖表和連接器。 您也可以覆寫其他所產生類別的方法。 某些產生的類別（例如 ToolboxHelper）一律會被雙重衍生。

### <a name="custom-constructors"></a>自訂函式

您無法覆寫函式。 即使是在雙衍生類別中，此函式也必須在衍生類別中。

如果您想要提供自己的函式，您可以 `Has Custom Constructor` 在 DSL 定義中設定網域類別來完成這項作業。 當您按一下 [ **轉換所有範本**] 時，產生的程式碼將不會包含該類別的函式。 它會包含遺漏的函式的呼叫。 當您建立方案時，這會導致錯誤報表。 按兩下錯誤報表，即可在產生的程式碼中查看批註，以說明您應該提供的內容。

在與產生的檔案不同的檔案中撰寫部分類別定義，並提供此函式。

### <a name="flagged-extension-points"></a>標記的擴充點

加上旗標的延伸點是 DSL 定義中的一個位置，您可以在其中設定屬性或核取方塊，以指出您將提供自訂方法。 自訂的函式就是其中一個範例。 其他範例包括將 `Kind` 定義域屬性的設定為匯出或自訂的儲存體，或在連接產生器中設定 **為自訂** 旗標。

在每個案例中，當您設定旗標並重新產生程式碼時，將會產生組建錯誤。 按兩下錯誤以查看批註，說明您必須提供的內容。

### <a name="rules"></a>規則

交易管理員可讓您定義在發生指定事件的交易結束之前執行的規則，例如屬性的變更。 規則通常用來在存放區中的不同元素之間維護 synchronism。 例如，您可以使用規則來確保圖表會顯示模型的目前狀態。

規則是以每個類別為基礎來定義，因此您不需要擁有可為每個物件註冊規則的程式碼。 如需詳細資訊，請參閱 [規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。

### <a name="store-events"></a>儲存事件

模型存放區提供的事件機制可用來接聽存放區中特定類型的變更，包括新增和刪除專案、屬性值的變更等等。 在進行變更的交易關閉之後，會呼叫事件處理常式。 一般而言，這些事件會用來更新存放區外部的資源。

### <a name="net-events"></a>.NET 事件

您可以訂閱圖形上的某些事件。 例如，您可以聆聽圖形上的滑鼠點擊。 您必須撰寫程式碼來訂閱每個物件的事件。 這段程式碼可以用 InitializeInstanceResources () 的覆寫來撰寫。

某些事件是在 ShapeFields 上產生的，用來在圖形上繪製裝飾專案。 如需範例，請參閱 [如何：攔截圖形或裝飾專案的點擊](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)。

這些事件通常不會發生在交易內。 如果您想要在存放區中進行變更，您應該建立交易。
