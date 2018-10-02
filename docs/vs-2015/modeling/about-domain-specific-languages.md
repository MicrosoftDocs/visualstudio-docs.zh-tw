---
title: 關於特定領域語言 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 971c63d25aee9c8676921b5ee7e112ae41a8a251
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491971"
---
# <a name="about-domain-specific-languages"></a>關於網域指定的語言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[定義域專屬語言相關](https://docs.microsoft.com/visualstudio/modeling/about-domain-specific-languages)。  
  
不同於一般用途的程式語言，例如 C# 或 UML，定義域專屬語言 (DSL) 被設計來表達工作的特定問題空間或網域中的陳述式。  
  
 已知的 Dsl 包含規則運算式和 SQL。 每個 DSL 是王道比一般用途的語言來描述文字字串或資料庫，但更糟的作業描述自己的範圍以外的想法。 個別的產業也有自己的 Dsl。 比方說，在電信業中，呼叫的描述語言都廣泛利用通話，在指定狀態的順序，並在空中旅遊業 DSL 用來描述航班預約的標準。  
  
 您的業務和您的專案也會處理特殊組可以與 DSL 中所述的概念。 例如，您可以定義 DSL 的其中一個應用程式：  
  
-   在網站上的導覽路徑的計劃。  
  
-   電子元件配線圖表。  
  
-   傳送帶互連和行李處理設備，如機場的網路。  
  
 當您設計 DSL 時，您會定義*網域類別*針對每個網域，例如網頁、 lamp、 或機場登機報到櫃檯的重要概念。 您定義*網域關聯性*例如超連結、 網路或一條輸送帶將連結在一起的概念。  
  
 您的 DSL 的使用者可以建立*模型。* 模型都*執行個體*的 DSL。 比方說，它們會描述特定的網站或特定的裝置或處理系統中特定的機場行李的連接。  
  
 您的使用者可以檢視模型，為圖表或 Windows 表單。 模型也可以檢視為 XML，這是儲存的方式。 當您定義 DSL 時，您會定義每個網域類別和關聯性的執行個體出現在使用者畫面上的方式。 典型的 DSL 會顯示為圖示或箭號連接的矩形的集合。  
  
 下圖顯示在圖表的 DSL 中的小型模型：  
  
 ![都鐸王朝家譜模型](../modeling/media/tudor-familytreemodel.png "Tudor_FamilyTreeModel")  
  
## <a name="what-you-can-do-with-dsls"></a>您可以執行與 Dsl  
 DSL 的一般應用程式會產生程式碼或其他成品。 當您定義您的 DSL 時，您可以定義*文字範本*其讀取 DSL 的模型，並產生文字檔案。  
  
 比方說，您可以撰寫範本，採用的機場計劃，並產生軟體的行李處理，以及一些描述該計劃的使用者文件的一部分。  
  
 當您已經定義 DSL 時，您可以將它散發給其他使用者都可以在自己的電腦上安裝它。 您的 DSL 的使用者能夠建立和編輯模型中的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
 您也可以定義功能表命令和其他工具，可協助使用者編輯的 DSL 中，以確保正確地使用 DSL，並協助使用者的項目範本建立新的執行個體的驗證條件約束。 您可以包裝其工具和其他的一或多個 Dsl[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]延伸模組為整合式套件。  
  
 一般而言，開發小組必須撰寫類似的程式碼適用於數個產品時，會建立特定領域語言。 比方說，公司，專長為行李處理系統中可能會定義從中便可以產生部分的程式碼，每個安裝的行李追蹤 DSL。 DSL 的優點是，它可以理解的客戶，從它產生的程式碼可靠，而且，系統可以快速更新客戶的需求變更時。  
  
 [!INCLUDE[dsl](../includes/dsl-md.md)] 可讓您建立特定領域語言具有自己的圖形化設計工具和您自己圖表標記法中，然後產生適當的原始程式碼，每個專案中使用的語言。  
  
## <a name="domain-specific-development"></a>定義域專屬開發  
 定義域專屬開發是識別您可以藉由使用特定領域語言，然後建構的語言，並將它部署至應用程式開發人員模型化的應用程式的組件的程序。 開發人員會使用特定領域語言建構模型，專屬於他們的應用程式，使用模型來產生原始程式碼，然後使用原始碼開發的應用程式。  
  
## <a name="aspects-of-graphical-domain-specific-development"></a>圖形化的定義域專屬開發層面  
 圖形化的定義域專屬語言都必須包含下列功能：  
  
-   Notation  
  
-   網域模型  
  
-   成品產生  
  
-   序列化  
  
-   與 Visual Studio 整合  
  
### <a name="notation"></a>Notation  
 特定領域語言必須相當少的項目，可以輕鬆地定義並擴充，可表示網域特有的概念。 標記法是由代表項目的圖形和連接器，代表項目，在圖表介面上之間的關聯性所組成。 在 [!INCLUDE[dsl](../includes/dsl-md.md)]的圖形可以擴充並調整，以代表您的網域特定語言的項目。  
  
### <a name="domain-model"></a>網域模型  
 特定領域語言必須結合的一組項目和一致的文法到其間的關聯性。 它也必須定義項目和關聯性的組合是否有效。 例如，程式設計語言通常會造成循環繼承，在其中一個類別衍生自第二個類別，第二個類別衍生自第一個類別。 條件約束也可用來表示商務邏輯，例如，一個人不能自己的相依性。 [!INCLUDE[dsl](../includes/dsl-md.md)] 使用條件約束來表示之最特定領域語言需要限制的類型。  
  
### <a name="artifact-generation"></a>成品產生  
 特定領域語言的主要用途之一是產生的成品，例如，原始程式碼、 XML 檔案或一些其他可用的資料。 一般而言，變更模型中的表示之成品的變更。 您可以使用[!INCLUDE[dsl](../includes/dsl-md.md)]產生成品，以及當您變更模型時，重新產生它們。  
  
### <a name="serialization"></a>序列化  
 特定領域語言必須保存某種形式的可編輯、 儲存、 關閉，並重新載入。 [!INCLUDE[dsl](../includes/dsl-md.md)] 使用 XML 格式，可讓您定義和自訂如何序列化或保存您的定義域專屬語言。  
  
### <a name="integration-with-visual-studio"></a>與 Visual Studio 整合  
 因為[!INCLUDE[dsl](../includes/dsl-md.md)]裝載於[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，它會擴充許多[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]視窗和控制項。 它也可讓您自訂功能表命令、 工具箱項目，及其他項目的使用者介面的行為。  
  
 您也可以針對您的特定領域語言建立模型匯流排配接器。 此配接器可讓您參考的模型和模型，並讓您撰寫程式碼可以存取及更新的 DSL 執行個體中的項目。 藉由使用功能強大的模型匯流排機制，您可以撰寫[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]處理多個模型的擴充功能。 您也可以撰寫使用模型的獨立應用程式。 如需詳細資訊，請參閱 <<c0> [ 使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。  
  
## <a name="benefits-of-domain-specific-development"></a>定義域專屬開發的優點  
 特定領域語言，可提供下列優點：  
  
-   包含完全符合問題空間的建構。  
  
     不同於一般用途的語言，定義域專屬語言是由項目和直接代表問題空間的邏輯關聯性所組成。 比方說，保險原則應用程式必須包含原則和宣告的項目。 特定領域語言，可讓您更輕鬆地設計應用程式，並尋找和修正錯誤的邏輯。  
  
-   可讓非開發人員與人員不知道了解整體設計的網域。  
  
     藉由使用圖形化的特定領域語言，您可以建立網域的視覺表示法，使非開發人員可以輕鬆地了解應用程式的設計。  
  
-   可讓您更輕鬆地建立原型的最終的應用程式。  
  
     開發人員可以使用它們的模型來建立原型應用程式，其可顯示給用戶端所產生的程式碼。  
  
## <a name="the-process-of-domain-specific-development"></a>定義域專屬的開發程序  
 大部分使用定義域專屬語言的軟體開發團隊，請遵循下列步驟來建立和使用其模型：  
  
-   小組會區別永遠不會變更的部分網域的變動組件。  
  
-   開發人員撰寫的固定的組件的程式碼，並將變動組件的擴充點。  
  
-   領導軟體開發人員或架構設計人員會建立特定領域語言，其中包含固定的組件的領域，以及擴充點，變數的組件的設計模式。  
  
-   領導軟體開發人員或架構設計人員會部署特定領域語言，小組會產生各種應用程式的開發人員。  
  
-   每位開發人員建立適用於特定的應用程式的模型。



