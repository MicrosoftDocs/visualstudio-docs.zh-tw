---
title: 覆寫及擴充產生的類別
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9aa4f39fb54617ae1dbf048a1e13f009c8df5185
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814233"
---
# <a name="override-and-extend-the-generated-classes"></a>覆寫及擴充產生的類別

您的 DSL 定義是，您可以在其建置一組強大的工具以特定領域語言為基礎的平台。 許多擴充功能和採用可覆寫及擴充從 DSL 定義產生的類別。 這些類別包括不只是您在 DSL 定義圖表中，明確定義網域類別，但其他類別，定義工具箱、 總管、 序列化和等等。

## <a name="extensibility-mechanisms"></a>擴充性機制

提供數種機制，可讓您擴充產生的程式碼。

### <a name="override-methods-in-a-partial-class"></a>覆寫中的部分類別方法

部分類別定義可讓多個位置中定義的類別。 這可讓您區隔產生的程式碼，從您自己撰寫的程式碼。 在您以手動方式撰寫的程式碼中，您可以覆寫產生的程式碼所繼承的類別。

例如，如果在您的 DSL 定義中，您定義網域類別，名為`Book`，您可以撰寫自訂程式碼，將覆寫方法：

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
> 若要覆寫產生的類別中的方法，一律從產生的檔案分隔的檔案中撰寫程式碼。 一般而言，該檔案包含在名為 CustomCode 資料夾中。 如果您變更產生的程式碼時，它們將會遺失的情況，當您重新產生的 DSL 定義中的程式碼。

若要探索您可以覆寫哪些方法，請輸入**覆寫**在類別中後, 接空格。 IntelliSense 工具提示會告訴您哪些方法可以覆寫。

### <a name="double-derived-classes"></a>雙衍生類別

大部分的方法中產生的類別被繼承自一組固定的模型命名空間中的類別。 不過，某些方法會定義產生的程式碼中。 一般情況下，這表示，您無法覆寫它們;您無法覆寫一個部分類別中的相同類別的另一個部分定義中所定義的方法。

不過，您可以設定覆寫這些方法**產生雙衍生**領域類別的旗標。 這會導致兩個類別，來產生，正在抽象的基底類別的另一個。 所有的方法和屬性定義的基底類別，而只有建構函式是在衍生類別中。

例如，在範例 Library.dsl，`CirculationBook`網域類別具有`Generates``Double Derived`屬性設定為`true`。 產生的程式碼，該網域類別包含兩個類別：

- `CirculationBookBase`其為抽象，而且其中包含所有的方法和屬性。

- `CirculationBook`其係衍生自`CirculationBookBase`。 它是空的除了其建構函式。

若要覆寫任何方法，您建立衍生類別的部分定義這類`CirculationBook`。 您可以覆寫產生的方法及繼承自模型化架構的方法。

您可以使用這個方法用於所有類型的項目，包括模型項目、 關聯性、 圖形、 圖表和連接器。 您也可以覆寫其他產生的類別的方法。 某些產生例如 ToolboxHelper 永遠是雙衍生的類別。

### <a name="custom-constructors"></a>自訂建構函式

您無法覆寫建構函式。 即使在雙衍生的類別，建構函式必須在衍生類別中。

如果您想要提供您自己的建構函式，您可以藉由設定`Has Custom Constructor`DSL 定義中的領域類別。 當您按一下 **轉換所有範本**，產生的程式碼將不會包含該類別的建構函式。 它會包含遺漏的建構函式呼叫。 當您建置方案時，這會導致錯誤報告。 按兩下 錯誤報表，以查看產生的程式碼，說明您應該提供中的註解。

不同於所產生的檔案，檔案中撰寫的部分類別定義，並提供建構函式。

### <a name="flagged-extension-points"></a>標有旗標的擴充點

標有旗標的擴充點是在 DSL 定義中，您可以在此對話方塊中設定的屬性或核取方塊以指出您將提供的自訂方法的位置。 自訂的建構函式是其中一個範例。 其他範例包括設定`Kind`Calculated 或自訂儲存體設定的網域屬性**Is Custom**連接產生器中的旗標。

在每個案例中，當您設定旗標，並重新產生程式碼，就會發生建置錯誤。 按兩下該錯誤，請參閱說明您必須提供註解。

### <a name="rules"></a>規則

交易管理員可讓您定義規則，以在其中指定已發生的事件，例如在屬性中變更交易結束之前執行。 規則通常用來維護 synchronism 存放區中的不同項目之間。 例如，規則用來確定此圖表會顯示模型的目前狀態。

規則會定義以每個類別為基礎，如此您就不必在程式碼，它會註冊每個物件的規則。 如需詳細資訊，請參閱 <<c0> [ 規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。

### <a name="store-events"></a>存放區事件

模型存放區提供事件的機制，您可以用來接聽特定類型的變更在存放區，包括新增和刪除的項目，屬性值變更等等。 事件處理常式會呼叫結尾的變更已完成的交易。 一般而言，這些事件用來更新外部存放區的資源。

### <a name="net-events"></a>.NET 事件

您可以在圖形上的某些事件訂閱。 例如，您可以接聽的圖形上的滑鼠點選。 您不必撰寫程式碼，每個物件的事件訂閱。 此程式碼可以寫入 InitializeInstanceResources() 覆寫中。

某些事件會產生 ShapeFields，用來繪製圖形上的裝飾項目。 如需範例，請參閱[如何：攔截圖案或 Decorator 上](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)。

通常，這些事件不會發生於在交易內。 如果您想要在存放區中進行變更，您應該建立交易。