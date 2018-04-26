---
title: 覆寫及擴充產生的類別
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ff0f020f2ab7558df6cc6f7865500a9910718145
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="overriding-and-extending-the-generated-classes"></a>覆寫及擴充產生的類別
DSL 定義是您可以在其建置一組強大的工具為基礎的網域特定定義域語言的平台。 許多擴充功能和地可覆寫及擴充所產生的 DSL 定義的類別。 這些類別包括不只是您在 DSL 定義圖表中，明確定義的網域類別，但其他類別，定義工具箱、 總管、 序列化和等等。

## <a name="extensibility-mechanisms"></a>擴充性機制
 提供數種機制，可讓您擴充所產生程式碼。

### <a name="overriding-methods-in-a-partial-class"></a>在部分類別中覆寫方法
 部分類別定義可讓多個位置中定義的類別。 這可讓您自行撰寫的程式碼分隔產生的程式碼。 在您手動撰寫的程式碼中，您可以覆寫所產生的程式碼所繼承的類別。

 例如，如果您在 DSL 定義中定義名為的網域類別`Book`，您可以撰寫自訂程式碼，將覆寫方法：

 `public partial class Book`

 `{`

 `protected override void OnDeleting()`

 `{`

 `MessageBox.Show("Deleting book " + this.Title);`

 `base.OnDeleting();`

 `} }`

> [!NOTE]
>  覆寫在產生的類別中的方法，一律產生的檔案分開的檔案中撰寫程式碼。 一般而言，檔案包含在名為 CustomCode 資料夾中。 如果您要產生的程式碼進行變更，它們將會遺失的情況，當您重新產生的 DSL 定義的程式碼。

 若要找出您可以覆寫的方法，請輸入**覆寫**在類別中後, 接空格。 IntelliSense 的工具提示會告知您哪種方法可以覆寫。

### <a name="double-derived-classes"></a>雙衍生類別
 大部分的產生類別中的方法是由一組固定的模型命名空間中類別繼承。 不過，某些方法會定義產生的程式碼中。 通常，這表示，您無法覆寫它們。您無法覆寫某一個部分類別中相同類別的另一個部分定義中所定義的方法。

 不過，您可以設定覆寫這些方法**會產生兩個衍生**網域類別的旗標。 產生此原因兩個類別，一個被其他項目的抽象基底類別。 所有方法和屬性定義在基底類別中，而且建構函式是在衍生類別中。

 例如，在範例 Library.dsl，`CirculationBook`網域類別具有`Generates``Double Derived`屬性設定為`true`。 該網域類別產生的程式碼包含兩個類別：

-   `CirculationBookBase`這是抽象，且會包含所有方法和屬性。

-   `CirculationBook`其衍生自`CirculationBookBase`。 它是空的除了其建構函式。

 若要覆寫任何方法，您建立衍生類別的部分定義這類`CirculationBook`。 您可以覆寫所產生的方法及繼承自模型架構的方法。

 您可以使用這個方法與所有類型的項目，包括模型項目、 關聯性、 圖形、 圖表和連接器。 您也可以覆寫方法的其他產生的類別。 某些產生例如 ToolboxHelper 一律是雙衍生的類別。

### <a name="custom-constructors"></a>自訂建構函式
 您無法覆寫建構函式。 即使在雙衍生的類別，建構函式必須在衍生類別中。

 如果您想要提供您自己的建構函式，您可以藉由設定`Has Custom Constructor`DSL 定義中的網域類別。 當您按一下**轉換所有範本**，產生的程式碼將不會包含該類別的建構函式。 它會包含遺漏的建構函式呼叫。 當您建置方案時，這會導致錯誤報告。 按兩下錯誤報表，以查看說明您應該提供產生的程式碼中的註解。

 在產生的檔案，不同的檔案中撰寫的部分類別定義，並提供建構函式。

### <a name="flagged-extension-points"></a>加上旗標的擴充點
 加上旗標的擴充點是 DSL 定義，您可以設定屬性或核取方塊，以表示您會提供自訂方法中的位置。 自訂建構函式是其中一個範例。 其他範例包括設定`Kind`計算或自訂儲存體設定的網域屬性**是自訂**連接產生器中的旗標。

 在各案例中，當您設定旗標，並重新產生程式碼，就會發生建置錯誤。 按兩下錯誤，以查看說明您必須提供的註解。

### <a name="rules"></a>規則
 交易管理員可讓您定義中指定之已發生的事件，例如在屬性中的變更在交易結束之前執行的規則。 規則通常用來維護 synchronism 存放區中的不同項目之間。 例如，規則可用來確定此圖表會顯示模型的目前狀態。

 規則定義以每個類別為基礎，如此您不需要有程式碼，它會註冊每個物件的規則。 如需詳細資訊，請參閱[規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。

### <a name="store-events"></a>儲存事件
 模型存放區提供事件的機制，您可以用來接聽特定類型的變更在存放區，包括新增和刪除的項目，變更內容值等等。 變更已完成的交易結束之後呼叫的事件處理常式。 一般而言，這些事件可用來更新外部存放區資源。

### <a name="net-events"></a>.NET 事件
 您可以在圖形上的某些事件訂閱。 例如，您可以接聽圖形上的滑鼠。 您必須撰寫程式碼，以訂閱的每個物件事件。 此程式碼可以採用的 InitializeInstanceResources() 覆寫。

 ShapeFields，用來在圖形上繪製裝飾項目上，會產生某些事件。 如需範例，請參閱[如何： 攔截按一下圖形或 Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)。

 通常，這些事件不會發生於在交易內。 如果您想要在存放區中進行變更，您應該建立交易。