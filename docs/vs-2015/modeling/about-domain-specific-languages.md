---
title: 關於特定領域語言 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b76142dfbc2dca860591bf3c3cb73c2971f56b22
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655374"
---
# <a name="about-domain-specific-languages"></a>關於網域指定的語言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

與一般用途的語言（例如C#或 UML）不同的是，特定領域語言（DSL）的設計是用來表示特定問題空間或網域中的語句。

 知名的 Dsl 包括正則運算式和 SQL。 每個 DSL 的效果都比一般用途的語言更適合用來描述文字字串或資料庫上的作業，但更糟的是描述其本身範圍以外的想法。 個別產業也有自己的 Dsl。 例如，在電信產業中，呼叫描述語言廣泛用來指定電話中的狀態順序，而在空中旅遊產業中，標準 DSL 是用來描述航班的預訂。

 您的企業和您的專案也會處理一組可以與 DSL 一併描述的特殊概念。 例如，您可以為下列其中一個應用程式定義 DSL：

- 網站中的導覽路徑計畫。

- 電子元件的接線圖。

- 機場的網路和行李處理設備。

  當您設計 DSL 時，您可以為網域中的每個重要概念（例如網頁、燈泡或機場簽入桌）定義*網域類別*。 您可以定義*網域關聯*性（例如超連結、有線或傳送帶），以將概念連結在一起。

  DSL 的使用者會建立*模型。* 模型是 DSL 的*實例*。 例如，他們會描述特定的網站，或特定裝置的接線，或特定機場中的行李處理系統。

  您的使用者可以將模型當做圖表或 Windows form 來觀看。 模型也可以視為 XML，也就是它們的儲存方式。 當您定義 DSL 時，您會定義每個網域類別和關聯性的實例如何顯示在使用者的畫面上。 一般的 DSL 會顯示為以箭號連接的圖示或矩形集合。

  下圖顯示圖表 DSL 中的小型模型：

  ![Tudor 家族樹狀結構模型](../modeling/media/tudor-familytreemodel.png "Tudor_FamilyTreeModel")

## <a name="what-you-can-do-with-dsls"></a>您可以使用 Dsl 執行的動作
 DSL 的一般應用就是產生程式碼或其他成品。 當您定義 DSL 時，可以定義可讀取 DSL 模型並產生文字檔的*文字模板*。

 例如，您可以撰寫接受機場計畫的範本，並產生軟體的一部分進行行李處理，以及一些描述該計畫的使用者檔。

 定義 DSL 之後，您可以將它散發給可以在自己的電腦上安裝它的其他使用者。 DSL 的使用者可以在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中建立和編輯模型。

 您也可以定義功能表命令和其他工具，協助使用者編輯 DSL、驗證條件約束，以協助確保正確使用 DSL，以及協助使用者建立新實例的專案範本。 您可以將一或多個 Dsl 連同其工具和其他 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組包裝為整合套件。

 一般而言，當開發小組必須針對數個產品撰寫類似的程式碼時，就會建立特定領域語言。 例如，專門用於行李處理系統的公司可能會定義一個行李追蹤 DSL，讓他們可以為每個安裝產生一些程式碼。 DSL 的優點是它可以讓客戶瞭解，從它產生的程式碼是可靠的，而且如果客戶的需求改變，系統就可以快速更新。

 [!INCLUDE[dsl](../includes/dsl-md.md)] 可讓您建立具有自己圖形化設計工具和自己的圖表標記法的特定領域語言，然後使用該語言為每個專案產生適當的原始程式碼。

## <a name="domain-specific-development"></a>特定領域開發
 網域特定開發是指使用特定領域語言來識別應用程式的各個部分，然後再建立語言並將它部署到應用程式開發人員的過程。 開發人員使用特定領域語言來建立其應用程式特有的模型、使用模型來產生原始程式碼，然後使用原始程式碼來開發應用程式。

## <a name="aspects-of-graphical-domain-specific-development"></a>圖形領域特定開發的層面
 圖形領域特定語言必須包含下列功能：

- Notation

- 領域模型

- 成品產生

- 序列化

- 與 Visual Studio 整合

### <a name="notation"></a>Notation
 網域指定的語言必須具有一組合理的元素，而且可以輕鬆地定義和擴充，以代表特定領域的結構。 標記法包含圖形（表示元素）和連接器（表示專案之間的關聯性），其位於圖形化圖表介面上。 在 [!INCLUDE[dsl](../includes/dsl-md.md)] 中，可以擴充和調整圖形，以代表特定領域語言的元素。

### <a name="domain-model"></a>領域模型
 網域指定的語言必須將一組專案和兩者之間的關聯性結合成一致的文法。 它也必須定義元素和關聯性的組合是否有效。 例如，程式設計語言通常會防止迴圈繼承，其中一個類別衍生自第二個類別，而第二個類別衍生自第一個類別。 條件約束也可以用來表達商務邏輯，例如，一個人不能與自己相依。 [!INCLUDE[dsl](../includes/dsl-md.md)] 使用條件約束來表達大部分特定領域語言所需的限制類型。

### <a name="artifact-generation"></a>成品產生
 特定領域語言的主要用途之一，就是產生成品，例如原始程式碼、XML 檔案或一些其他可用的資料。 一般而言，模型中的變更表示成品中的變更。 您可以使用 [!INCLUDE[dsl](../includes/dsl-md.md)] 來產生成品，並在變更模型時重新產生成品。

### <a name="serialization"></a>序列化
 網域指定的語言必須以某種形式保存，才能編輯、儲存、關閉和重載。 [!INCLUDE[dsl](../includes/dsl-md.md)] 使用 XML 格式，可讓您定義及自訂您的特定領域語言的序列化或保存方式。

### <a name="integration-with-visual-studio"></a>與 Visual Studio 整合
 因為 [!INCLUDE[dsl](../includes/dsl-md.md)] 裝載于 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中，所以它會擴充許多 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 視窗和控制項。 它也可讓您自訂功能表命令、工具箱專案和其他使用者介面元素的行為。

 您也可以為特定領域語言建立模型匯流排介面卡。 此介面卡可讓您參考模型中的模型和專案，並可讓您撰寫可存取和更新 DSL 實例的程式碼。 藉由使用強大的模型匯流排機制，您可以撰寫可搭配多個模型使用的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組。 您也可以撰寫與模型搭配使用的獨立應用程式。 如需詳細資訊，請參閱[使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。

## <a name="benefits-of-domain-specific-development"></a>網域特定開發的優點
 特定領域語言可以提供下列優點：

- 包含完全符合問題空間的結構。

     不同于一般用途的語言，特定領域語言是由直接代表問題空間邏輯的元素和關係所組成。 例如，保險原則應用程式必須包含原則和宣告的元素。 網域指定的語言可讓您更輕鬆地設計應用程式，並尋找和更正邏輯的錯誤。

- 讓不知道網域的非開發人員和人員瞭解整體設計。

     藉由使用圖形領域特定語言，您可以建立網域的視覺標記法，讓非開發人員可以輕易地瞭解應用程式的設計。

- 可讓您更輕鬆地建立最終應用程式的原型。

     開發人員可以使用其模型所產生的程式碼，來建立可向用戶端顯示的原型應用程式。

## <a name="the-process-of-domain-specific-development"></a>網域特定開發的程式
 大部分使用特定領域語言的軟體發展小組都遵循下列步驟來建立和使用其模型：

- 小組會區分網域的變數部分與永不變更的部分。

- 開發人員會針對固定元件撰寫程式碼，並保留變數元件的擴充點。

- 潛在客戶軟體發展人員或架構師會建立特定領域語言，其中包含網域固定部分的設計模式，以及變數部分的擴充點。

- 首席軟體發展人員或架構設計人員會將特定領域語言部署給小組所產生之各種應用程式的開發人員。

- 每位開發人員都會建立一個適用于特定應用程式的模型。
