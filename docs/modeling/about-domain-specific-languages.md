---
title: 關於網域指定的語言
description: 瞭解特定領域語言 (DSL) 如何設計來表達特定問題空間或網域中的語句。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab56292aafda25efc0b3dfeeb14e93d4502a5567
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384976"
---
# <a name="about-domain-specific-languages"></a>關於網域指定的語言

和一般用途的語言（例如 c # 或 UML）不同的是，特定領域語言 (DSL) 是設計用來表示特定問題空間或網域中的語句。

知名的 Dsl 包括正則運算式和 SQL。 每個 DSL 都比一般用途的語言更好用來描述文字字串或資料庫上的作業，但更糟的是，用來描述其本身範圍外的想法。 個別產業也有自己的 Dsl。 例如，在電信產業中，通話描述語言廣泛用來指定通話中的狀態順序，而在空中旅遊產業中，標準 DSL 是用來描述航班預訂。

您的業務和專案也會處理一組可以使用 DSL 描述的特殊概念。 例如，您可以定義其中一個應用程式的 DSL：

- 規劃網站中的導覽路徑。

- 電子元件的接線圖。

- 機場的網路和行李處理機場的設備。

當您設計 DSL 時，您會為網域中的每個重要概念定義 *網域類別* ，例如，網頁、燈泡或機場簽入辦公桌。 您可以定義 *網域關聯* 性，例如超連結、網路或傳送帶，以將這些概念連結在一起。

DSL 的使用者會建立 *模型。* 模型是 DSL 的 *實例* 。 例如，它們會描述特定的網站、特定裝置的線路或特定機場的行李處理系統。

您的使用者可以將模型視為圖表或 Windows 表單來查看。 您也可以將模型視為 XML，也就是儲存它們的方式。 當您定義 DSL 時，會定義每個網域類別和關聯性的實例如何顯示在使用者的畫面上。 一般的 DSL 會顯示為以箭號連接的圖示或矩形集合。

下圖顯示圖表 DSL 中的小型模型：

![都鐸王朝家譜模型](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>您可以使用 Dsl 來做什麼

DSL 的一般應用是產生程式碼或其他成品。 當您定義 DSL 時，可以定義 *文字模板* 來讀取 DSL 的模型並產生文字檔。

例如，您可以撰寫範本以拍攝機場方案，並產生用於行李處理的部分軟體，以及一些描述方案的使用者檔。

定義 DSL 之後，您就可以將它散發給其他使用者，以便將它安裝在自己的電腦上。 DSL 的使用者可以在 Visual Studio 中建立和編輯模型。

您也可以定義功能表命令和其他工具，以協助使用者編輯 DSL、驗證條件約束，以確保能正確使用 DSL，以及協助使用者建立新實例的專案範本。 您可以將一或多個 Dsl 的工具和其他 Visual Studio 擴充功能包裝為整合套件。

一般來說，當開發小組必須撰寫數個產品的類似程式碼時，就會建立特定領域語言。 例如，專門從事行李處理系統的公司可能會定義一個行李追蹤 DSL，讓他們可以為每個安裝產生一些程式碼。 DSL 的優點是，它可以由其客戶瞭解、其產生的程式碼是可靠的，而且如果客戶的需求變更，系統可以快速更新。

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 可讓您建立特定領域的語言，此語言具有您自己的圖形設計工具和您自己的圖表標記法，然後使用該語言為每個專案產生適當的原始程式碼。

## <a name="domain-specific-development"></a>Domain-Specific 開發

特定領域開發是識別應用程式元件的程式，這些元件可以使用特定領域語言來建立模型，然後再建立語言並將其部署至應用程式開發人員。 開發人員會使用特定領域語言來建立其應用程式專屬的模型、使用模型來產生原始程式碼，然後使用原始程式碼來開發應用程式。

## <a name="aspects-of-graphical-domain-specific-development"></a>圖形化 Domain-Specific 開發的層面

圖形網域特定語言必須包含下列功能：

- 表示法

- 領域模型

- 成品產生

- 序列化

- 與 Visual Studio 整合

### <a name="notation"></a>表示法

特定領域語言必須有一組相當小的元素，可輕鬆地定義和擴充，以代表定義域特定的結構。 標記法包含圖形（代表專案）和接點（代表專案之間的關聯性，在圖形化圖介面上）。 在中 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] ，可以擴充及調整圖形，以代表您的網域特定語言的元素。

### <a name="domain-model"></a>領域模型

特定領域語言必須將一組專案和兩者之間的關聯性合併成一致的文法。 它也必須定義專案和關聯性的組合是否有效。 例如，程式設計語言通常會防止迴圈繼承，其中一個類別衍生自第二個類別，第二個類別衍生自第一個類別。 條件約束也可以用來表達商務邏輯，例如，一個人不能是自己的相依。 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 使用條件約束來表達大部分網域特定語言所需的限制類型。

### <a name="artifact-generation"></a>成品產生

特定領域語言的主要用途之一，就是產生成品，例如原始程式碼、XML 檔案或一些其他可用的資料。 一般而言，模型中的變更表示成品的變更。 您可以使用 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 來產生成品，並在變更模型時重新產生成品。

### <a name="serialization"></a>序列化

特定領域語言必須以某種形式保存，才能進行編輯、儲存、關閉和重載。 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 使用 XML 格式，可讓您定義和自訂特定領域語言的序列化或保存方式。

### <a name="integration-with-visual-studio"></a>與 Visual Studio 整合

因為 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 是裝載在 Visual Studio 中，所以它會延伸許多 Visual Studio 視窗和控制項。 它也可讓您自訂功能表命令、工具箱專案和其他使用者介面元素的行為。

您也可以為特定領域語言建立模型匯流排介面卡。 此介面卡可讓您參考模型內的模型和元素，並可讓您撰寫可存取及更新 DSL 實例的程式碼。 藉由使用強大的模型匯流排機制，您可以撰寫適用于多個模型的 Visual Studio 延伸模組。 您也可以撰寫適用于模型的獨立應用程式。 如需詳細資訊，請參閱 [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。

## <a name="benefits-of-domain-specific-development"></a>Domain-Specific 開發的優點

特定領域語言可以提供下列優點：

- 包含完全符合問題空間的結構。

     不同于一般用途的語言，網域專屬的語言是由直接代表問題空間邏輯的元素和關聯性所組成。 例如，保險原則應用程式必須包含原則和宣告的元素。 特定領域語言可讓您更輕鬆地設計應用程式，以及尋找和修正邏輯的錯誤。

- 讓非開發人員和不知道網域的人瞭解整體設計。

     藉由使用圖形化網域專屬的語言，您可以建立網域的視覺標記法，讓非開發人員可以輕鬆地瞭解應用程式的設計。

- 可讓您更輕鬆地建立最終應用程式的原型。

     開發人員可以使用其模型所產生的程式碼，建立可向用戶端顯示的原型應用程式。

## <a name="the-process-of-domain-specific-development"></a>Domain-Specific 開發的流程

大部分使用網域專屬語言的軟體發展小組都遵循下列步驟來建立及使用其模型：

- 小組會區分網域的變數部分與從未變更的部分。

- 開發人員會撰寫固定部分的程式碼，並保留變數部分的擴充點。

- 首席軟體發展人員或架構設計人員會建立特定領域語言，其中併入了定義域固定部分的設計模式以及變數部分的擴充點。

- 首席軟體發展人員或架構設計人員將特定領域語言部署給小組所產生之各種應用程式的開發人員。

- 每位開發人員都會建立適用于特定應用程式的模型。
