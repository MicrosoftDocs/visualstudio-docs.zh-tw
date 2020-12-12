---
title: 透過模型開發測試
description: 瞭解如何使用需求和架構模型來協助組織系統及其元件的測試。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tests and requirements
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f49b52bece0c1dddc65da919d266c4f21b1bf69
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361829"
---
# <a name="develop-tests-from-a-model"></a>透過模型開發測試
您可以使用需求和架構模型來協助您組織整理系統及其元件的測試。 這種做法可協助您確保測試對於使用者和其他專案關係人來說非常重要的需求，並可協助您在需求變更時快速地更新測試。 如果您使用 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)]，則也可以維護模型與測試之間的連結。

 若要查看 Visual Studio 支援這些功能的版本，請參閱 [架構和模型工具的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="system-and-subsystem-testing"></a>系統和子系統測試
 *系統測試（* 也稱為 *接受度測試*）表示測試是否符合使用者的需求。 這類測試關注系統的外部可見行為，而非內部設計。

 擴充或重新設計系統時，系統測試極為重要。 它們可協助您在變更程式碼時避免造成錯誤。

 規劃對系統進行任何變更或擴充時，最好是從在現有系統上執行的一組系統測試開始進行。 然後，您可以擴充或調整測試來測試新的需求、變更程式碼，以及重新執行一組完整的測試。

 開發新的系統時，您可以在開發開始時立即開始建立測試。 在開發每個功能之前定義測試，即可透過極特定的方式擷取需求討論。

 子系統測試會將相同的準則套用到系統的主要元件。 每個元件都會與其他元件分開進行測試。 子系統測試著重在元件使用者介面或 API 上可見的行為。

## <a name="deriving-system-tests-from-a-requirements-model"></a>從需求模型衍生系統測試
 您可以建立和維護系統測試與需求模型之間的關聯性。 若要建立此關聯性，請撰寫與需求模型主要項目對應的測試。 Visual Studio 透過讓您建立測試與模型各部分之間的連結，以協助您維護該關聯性。 如需需求模型的詳細資訊，請參閱 [模型使用者需求](../modeling/model-user-requirements.md)。

### <a name="write-tests-for-each-use-case"></a>撰寫每個使用案例的測試
 如果您使用 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)]，則可以為需求模型中所定義的每個使用案例建立一組測試。 例如，如果您有「點餐」(Order a Meal) 使用案例 (其中包括「建立訂單」(Create Order) 和「新增訂單項目」(Add Item to Order)，則可以建立這些使用案例整體和更特定部分的測試。

 這些方針可能十分有用：

- 針對主要路徑和例外結果，每個使用案例都應該有數個測試。

- 描述需求模型中的使用案例時，定義其後置條件 (即達成的目標) 比詳述使用者遵循以達成目標的程序更為重要。 例如，「點餐」(Order a Meal) 的後置條件可能是餐廳正在準備客人的餐點，並且客人已付費。 後置條件是您的測試應該驗證的條件。

- 不同的測試是以後置條件的不同子句為基礎。 例如，建立不同的測試來通知餐廳有此訂單，以及取得客人的付款。 這項區隔具有下列優點：

  - 不同層面的需求變更經常會獨立發生。 透過此方式，將測試分成不同的層面，即可在需求變更時輕鬆地更新測試。

  - 如果開發計劃先實作使用案例的其中一個層面，再實作另一個層面，則可以在進行開發時個別啟用測試。

- 設計測試時，請分開選擇測試資料與判斷是否達到後置條件的程式碼或指令碼。 例如，簡單算術函式的測試可能是：輸入 4；驗證輸出是 2。 而是將指令碼設計為：選擇輸入；將輸出乘上它自己，並驗證結果是原始輸入。 這個樣式可讓您有不同的測試輸入，而不變更測試的主體。

#### <a name="linking-tests-to-use-cases"></a>將測試連結至使用案例
 如果您使用 [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] 來設計和執行測試，則可以根據需求、使用案例或使用者案例工作專案來組織您的測試。 您可以將這些工作項目連結至模型中的使用案例。 這可讓您快速追蹤測試的需求變更，並協助您追蹤每個使用案例的進度。

###### <a name="to-link-tests-to-a-use-case"></a>將測試連結至使用案例

1. 在 [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] 中，建立需求，並以它為測試套件的基礎。

    您所建立的需求是 [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)] 中的工作項目。 這可能是使用者案例、需求或使用案例工作專案，視您的專案搭配 Team Foundation 使用的流程範本而定。 如需詳細資訊，請參閱 [關於 agile 工具和 agile 專案管理](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)。

2. 將需求工作項目連結至模型中的一個或多個使用案例。

    在使用案例圖中，以滑鼠右鍵按一下使用案例，然後按一下 [ **連結至工作專案**]。

3. 加入測試套件 (驗證使用案例的測試案例)。

   通常，每個使用者劇本或需求工作項目都會連結至模型中的數個使用案例，而且每個使用案例都會連結至數個使用者劇本或需求。 原因是每個使用者劇本或需求都涵蓋一組開發數個使用案例的工作。 例如，在專案的早期反覆項目中，您可能會開發基本使用者劇本，在其中，客戶可以選擇目錄中的項目並傳送它們。 在後期反覆項目中，劇本可能是使用者在完成訂單時付款，供應商則會在交貨之後收到金額。  每個劇本都會在「訂貨」(Order Goods) 使用案例的後置條件中加入子句。

   您可以建立從需求到後置條件子句的個別連結，方法是在使用案例圖的不同註解中撰寫這些子句。 您可以將每個註解連結至需求工作項目，並將註解連結至圖表上的使用案例。

### <a name="base-tests-on-the-requirements-types"></a>測試是以需求類型為基礎
 需求模型的類型 (即類別、介面和列舉) 描述使用者如何認為和溝通有關其業務的概念和關聯性。 它會排除只與系統內部設計相關的類型。

 根據這些需求類型，設計您的測試。 這種做法可協助您確保討論需求變更時，可以輕鬆地關聯變更與測試中的必要變更。 這樣即可直接與使用者和其他利害關係人討論測試和其預期結果。 這表示可以在開發程序外部維護使用者需求，並且避免輕率的測試設計造成可能的設計缺陷。

 對於手動測試，這種做法包含遵守測試指令碼中需求模型的詞彙。 對於自動化測試，這種做法包含使用需求類別圖做為測試程式碼的基礎，以及建立存取子和更新程式函式以將需求模型連結至程式碼。

 例如，需求模型可能包括「菜單」 (Menu)、「菜單項目」(Menu Item)、「訂單」(Order) 類型，以及其間的關聯。 此模型代表訂餐系統所儲存和處理的資訊，但不代表其實作的複雜性。 在工作系統中，於資料庫中、使用者介面中和 API 上，每種類型都可能會有數個不同的實現。 在分散式系統中，系統不同部分中所儲存的每個執行個體同時可能會有數個變化。

 若要測試使用案例 (例如「新增訂單項目」 (Add Item to Order)，測試方法可能會包括與下面類似的程式碼：

```
Order order = ... ; // set up an order
// Store prior state:
int countBefore = order.MenuItems.Count;
// Perform use case:
MenuItem chosenItem = ...; // choose an item
AddItemToOrder (chosenItem, order);
// Verify part of postcondition:
int countAfter = order.MenuItems.Count;
Assert (countAfter == countBefore = 1);
```

 請注意，此測試方法會使用需求模型的類別。 關聯和屬性 (Attribute) 會實現為 .NET 屬性 (Property)。

 為了讓這項作業運作，類別的屬性必須定義為唯讀函式或存取子，以存取系統來擷取其目前狀態的相關資訊。 模擬使用案例的方法 (例如 AddItemToOrder) 必須透過其 API 或使用者介面下的層級來驅動系統。 測試物件的建構函式 (例如 Order 和 MenuItem) 也必須驅動系統建立系統內的對應項目。

 許多存取子和更新程式都已經可以透過應用程式的一般 API 使用。 但是，可能需要撰寫一些額外函式，才能啟用測試。 這些額外的存取子和更新程式有時稱為「測試檢測」。 因為它們根據系統內部設計，所以系統開發人員負責提供它們，測試人員則根據需求模型撰寫測試的程式碼。

 撰寫自動化測試時，您可以使用一般測試來包裝存取子和更新程式。

### <a name="tests-for-business-rules"></a>商務規則的測試
 有些需求未與任何一個使用案例直接相關。 例如，DinnerNow 公司可讓客人從許多「菜單」( Menu) 中進行選擇，但是需要每筆「」 Order 中，所有選擇的「項目」(Item) 都應該來自單一「「菜單」( Menu)。 關於需求類別模型中「訂單」 (Order)、「菜單」(Menu) 與項目」(Item) 之間的關聯，這個商務規則可以表示為非變異。

 這類非變異規則不只控管目前定義的所有使用案例，同時控管稍後定義的任何其他使用案例。 因此，適用於將它與任何使用案例分開撰寫，以及與使用案例分開進行測試。

## <a name="deriving-subsystem-tests-from-models"></a>從模型衍生子系統測試
 在大型系統的高階設計中，您可以識別元件或子系統。 這些代表可個別設計或位於不同電腦的組件，或是可以使用許多方式重新合併的可重複使用模組。

 您可以將用於整個系統的相同準則套用至每個主要元件。 在大型專案中，每個元件都可以有它自己的需求模型。 在較小的專案中，可以建立架構模型或高階設計，以顯示主要元件和其互動。 如需詳細資訊，請參閱 [模型您的應用程式架構](../modeling/model-your-app-s-architecture.md)。

 在任一情況下，您都可以建立模型項目與子系統測試之間的關聯性，方法與建立需求模型與系統測試之間的關聯性相同。

### <a name="isolate-components-with-provided-and-required-interfaces"></a>使用提供的和需要的介面來隔離元件
 適用於識別元件與系統其他組件或外部服務的所有相依性，以及將這些項目呈現為「需要的介面」。 這項練習通常會導致某項重新設計，而讓元件更為低耦合並可輕鬆地與設計的其餘部分區隔。

 這項低耦合的優點是可以將元件通常使用的服務取代為模擬物件，以執行元件來進行測試。 這些是設定以進行測試的元件。 模擬元件提供您元件所需的介面，以回應具有模擬資料的查詢。 模擬元件會形成整個測試控管的一部分，用以連線至元件的所有介面。

 模擬測試的優點是，雖然您元件所使用服務的其他元件仍然處於開發階段，您還是可以開發您的元件。

## <a name="maintain-the-relationships-between-tests-and-model"></a>維護測試與模型之間的關聯性
 在每隔幾週即執行反覆項目的典型專案中，會在接近每次反覆項目的開頭保留需求檢閱。 會議會討論要在下一個反覆項目傳送的功能。 需求模型可以用來協助討論將開發的概念、案例和動作序列。 商務利害關係人會設定優先順序、開發人員會進行評估，測試人員則確保正確地擷取每個功能的預期行為。

 撰寫測試是定義需求的最有效方式，同時也是確保人員清楚了解所需項目的有效方法。 不過，撰寫測試在規格研討會期間可能需要很久的時間，因此建立模型可能更為快速。

 從測試的觀點，需求模型可以視為測試的縮寫。 因此，務必維護測試與整個專案中模型之間的關聯性。

## <a name="attaching-test-cases-to-model-elements"></a><a name="Attaching"></a> 將測試案例附加至模型專案
 如果您的專案使用 [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)]，則可以將測試連結至模型中的項目。 這可讓您快速找出需求中變更所影響的測試，並協助您追蹤已實現需求的範圍。

 您可以將測試連結至所有類型的項目。 以下是一些範例：

- 將使用案例連結至可執行它的測試。

- 在連結至使用案例的註解中撰寫使用案例後置條件的子句或目標，然後將測試連結至每個註解。

- 在類別圖或活動圖的註解中撰寫非變異規則，並將它們連結至測試。

- 將測試連結至活動圖或個別活動。

- 將測試套件連結至它所測試的元件或子系統。

#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>將測試連結至模型項目或關聯性

1. 在 [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] 中，建立需求，並以它為測試套件的基礎。

    您所建立的需求是 [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)] 中的工作項目。 這可能是使用者案例、需求或使用案例工作專案，視您的專案搭配 Team Foundation 使用的流程範本而定。 如需詳細資訊，請參閱 [關於 agile 工具和 agile 專案管理](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)。

2. 將需求工作項目連結至模型中的一個或多個項目。

    在模型圖中，以滑鼠右鍵按一下專案、批註或關聯性，然後按一下 [ **連結至工作專案**]。

3. 加入測試套件 (驗證模型項目中所表示的需求的測試案例)。

## <a name="see-also"></a>請參閱

- [建立應用程式模型](../modeling/create-models-for-your-app.md)
- [模型使用者需求](../modeling/model-user-requirements.md)
- [建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)
- [分析架構並製作架構模型](../modeling/analyze-and-model-your-architecture.md)
