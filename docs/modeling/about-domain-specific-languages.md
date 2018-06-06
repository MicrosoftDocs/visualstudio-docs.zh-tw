---
title: 關於網域指定的語言
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0743fa0dd1f8b876c4396d4e52d9c8636c504d67
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749141"
---
# <a name="about-domain-specific-languages"></a>關於網域指定的語言

與一般用途的程式語言，例如 C# 或 UML，不同的網域特定定義域語言 (DSL) 被為了 express 特定問題空間或網域中的陳述式。

已知的 Dsl 包含規則運算式和 SQL。 每個 DSL 是比較好的一般用途的語言比描述作業的描述會在它自己的範圍之外的想法文字字串或資料庫，但更差。 個別的產業也有自己的 Dsl。 比方說，在電信產業中，呼叫的描述語言都廣泛利用在電話呼叫中，指定狀態的順序，並在空中旅行業界的標準 DSL 用來描述航班預約。

您的業務和您的專案也處理特殊的無法 DSL 與說明的概念集。 例如，您可以定義的其中一個應用程式的 DSL:

-   在網站上的導覽路徑的計劃。

-   如電子元件佈線圖。

-   輸送帶的配置和行李處理設備機場的網路。

當您設計 DSL 時，定義*網域類別*針對每個網域，例如網頁、 燈或機場登機報到櫃檯中的重要概念。 您定義*網域關係*例如超連結、 網路或將連結在一起的概念一條輸送帶。

DSL 的使用者可以建立*模型。* 模型是*執行個體*DSL。 例如，這些主題說明特定的網站或特定的裝置或處理系統中特定機場行李的線路。

您的使用者可以檢視模型，為圖表或在 Windows form。 模型也可以檢視為 XML，這是儲存的方式。 當您定義 DSL 時，您會定義使用者的螢幕上顯示每個網域類別和關聯性的執行個體的方式。 典型的 DSL 會顯示為圖示或矩形箭號來連接的集合。

下圖顯示一個小型的模型中要 DSL:

![都鐸王朝家譜模型](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>您可以使用達成 Dsl

DSL 的一般應用程式是要產生程式碼或其他成品。 當您定義 DSL 時，您可以定義*文字範本*所讀取的 DSL 模型，以及產生文字檔案。

例如，您可以撰寫範本取得機場計劃，並且產生軟體行李處理，以及一些使用者文件描述計劃的一部分。

當您已經定義 DSL 時，您可以將它散發給其他使用者都可以將它安裝在他們自己的電腦上。 DSL 的使用者可以建立和編輯 Visual Studio 中的模型。

您也可以定義功能表命令和其他工具，可協助使用者編輯 DSL、 驗證條件約束，以協助確保正確地使用 DSL 和項目範本，可協助使用者建立的新執行個體。 您可以包裝其工具和其他 Visual Studio 擴充功能的一或多個 Dsl 作為整合式套件。

一般而言，開發團隊必須撰寫類似的程式碼適用於數個產品時，會建立特定領域語言。 比方說，專門用來在行李處理系統中的公司可能會定義可從中產生每個安裝的程式碼部分的行李追蹤 DSL。 DSL 的好處是，它可以了解他們的客戶，從它產生的程式碼相當可靠，因此，系統可以快速更新客戶的需求變更時。

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 可讓您建立的網域特定定義域語言具有自己的圖形設計工具和您自己的圖表標記法，並接著使用的語言來產生適當的原始程式碼，每個專案。

## <a name="domain-specific-development"></a>特定領域開發

特定領域開發是識別您可以建立模型使用的網域特定定義域語言，然後建構語言，並將它部署至應用程式開發人員的應用程式的組件的程序。 開發人員使用網域特定領域語言建構其應用程式特定的模型、 使用模型來產生原始程式碼，然後再使用原始碼來開發應用程式。

## <a name="aspects-of-graphical-domain-specific-development"></a>圖形化的網域特定開發的層面

圖形化的特定領域語言必須包含下列功能：

- Notation

- 網域模型

- 成品產生

- 序列化

- 與 Visual Studio 整合

### <a name="notation"></a>Notation

特定領域語言必須相當少的項目，可以輕鬆地定義及擴充，可表示網域特有的概念。 標記法是由表示項目的圖形和連接器，代表在圖表介面上項目之間的關聯性所組成。 在[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]，可以擴充的圖形，並調整以代表您的特定領域語言的項目。

### <a name="domain-model"></a>網域模型

特定領域語言必須結合一組項目和其連貫的文法之間的關聯性。 它也必須定義的項目和關聯性組合是否有效。 例如，程式設計語言通常會阻止中從第二個類別衍生一個類別，而第二個類別衍生自第一個類別中的循環繼承。 條件約束也可用來表示商務邏輯，例如，一個人不能自己的相依性。 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 使用條件約束來表示特定領域語言最需要的限制類型。

### <a name="artifact-generation"></a>成品產生

特定領域語言的主要用途之一是產生的成品，例如，原始程式碼、 XML 檔案或其他可用的資料。 一般而言，模型中的變更表示該成品的變更。 您可以使用[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]產生成品，以及當您變更模型時重新產生。

### <a name="serialization"></a>序列化

特定領域語言必須被 persisted 某種形式的可編輯、 儲存、 關閉，並重新載入。 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 使用 XML 格式，可讓您定義和自訂如何序列化或保存您的特定領域語言。

### <a name="integration-with-visual-studio"></a>與 Visual Studio 整合

因為[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]裝載在 Visual Studio 中，它會擴充許多 Visual Studio 視窗和控制項。 它也可讓您自訂的功能表命令、 工具箱項目和其他項目使用者介面的行為。

您也可以建立模型匯流排配接器的特定領域語言。 此配接器可讓您參考的模型和模型，並讓您撰寫程式碼可以存取及更新的 DSL 執行個體中的項目。 藉由使用功能強大的模型匯流排機制，您可以撰寫 Visual Studio 擴充功能，可搭配多個模型。 您也可以撰寫處理模型的獨立應用程式。 如需詳細資訊，請參閱[整合的模型，使用 Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。

## <a name="benefits-of-domain-specific-development"></a>特定領域開發的優點

特定領域語言可以提供下列優點：

- 包含完全符合問題空間的建構。

     不同於一般用途的程式語言，網域特定領域語言是由項目和直接呈現的問題空間邏輯的關聯性所組成。 例如，保險原則應用程式必須包含原則和宣告的項目。 特定領域語言，可以更輕鬆地設計應用程式，以及尋找和修正錯誤的邏輯。

- 可讓非開發人員不知道了解整體設計的網域。

     透過使用圖形化的特定領域語言，您可以建立網域的視覺表示法，讓非開發人員可以輕鬆地了解應用程式的設計。

- 可讓您更輕鬆地建立最後的應用程式的原型。

     開發人員可以使用它們的模型建立原型應用程式，它們可以顯示給用戶端所產生的程式碼。

## <a name="the-process-of-domain-specific-development"></a>特定領域開發程序

大部分的軟體開發團隊使用的特定領域語言，請遵循下列步驟，建立並使用他們的模型：

-   小組會區別永遠不會變更的部分網域的變動的部分。

-   開發人員撰寫程式碼的固定部分，並將擴充點，變數的組件。

-   軟體開發人員或是架構設計人員建立特定領域語言，其中包含的領域，以及擴充點，變數的組件固定的組件的設計模式。

-   領導軟體開發人員或設計師會對小組產生的各種應用程式的開發人員部署特定領域語言。

-   每個開發人員建立的模型，適用於特定應用程式。