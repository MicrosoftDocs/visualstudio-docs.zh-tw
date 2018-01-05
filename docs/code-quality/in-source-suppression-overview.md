---
title: "原始檔中隱藏項目概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92babbf3c7a5863d178463b69525bdb722bf28ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="in-source-suppression-overview"></a>原始檔中隱藏項目概觀
在原始程式檔隱藏項目是隱藏或忽略 managed 程式碼中的程式碼分析違規所加入的能力**SuppressMessage**屬性造成違規的程式碼區段。 **SuppressMessage**屬性是在編譯時期定義 CODE_ANALYSIS 編譯的符號時，才包含 managed 程式碼組件的 IL 中繼資料中條件式屬性。  
  
 在 C++/CLI 中，若要加入此屬性，請在標頭檔中使用 CA_SUPPRESS_MESSAGE 或 CA_GLOBAL_SUPPRESS_MESSAGE 巨集。  
  
 您不應該使用原始檔中隱藏項目上的發行組建，以避免不小心傳送的原始檔中隱藏項目中繼資料。 在來源隱藏的處理成本，因為應用程式的效能可能下降藉由在原始程式檔隱藏項目中繼資料。  
  
> [!NOTE]
>  您沒有要將程式碼這些屬性自己。 如需詳細資訊，請參閱[How to： 使用功能表項目隱藏的警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。 功能表項目不是適用於 c + + 程式碼。  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage 屬性  
 當您以滑鼠右鍵按一下程式碼分析警告在**錯誤清單**，然後按一下 **隱藏訊息**、 **SuppressMessage**程式碼中或以加入屬性專案的全域隱藏項目檔案。  
  
 **SuppressMessage**屬性具有下列格式：  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```csharp  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 [C++]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 其中：  
  
-   **規則類別**-定義此規則的類別目錄。 如需程式碼分析規則類別的詳細資訊，請參閱[Managed 程式碼警告的程式碼分析](../code-quality/code-analysis-for-managed-code-warnings.md)。  
  
-   **Rule Id** -規則的識別碼。 支援包括同時短期或長期的規則識別項名稱。 簡短名稱是 CAXXXX;完整名稱是 CAXXXX:FriendlyTypeName。  
  
-   **對齊**-用來記錄原因隱藏訊息的文字。  
  
-   **訊息識別碼**-針對每則訊息有問題的唯一識別碼。  
  
-   **範圍**位在其要隱藏警告的目標。 如果未指定目標，則會將它設定為屬性的目標。 支援的範圍包括下列各項：  
  
    -   Module  
  
    -   命名空間  
  
    -   資源  
  
    -   類型  
  
    -   成員  
  
-   **目標**-識別項，用來指定在其要隱藏警告的目標。 它必須包含完整項目名稱。  
  
## <a name="suppressmessage-usage"></a>SuppressMessage 使用量  
 程式碼分析警告會隱藏層級的執行個體**SuppressMessage**屬性會套用。 目的是緊密結合的程式碼的隱藏項目資訊發生違規。  
  
 一般格式的隱藏項目包括規則分類和規則識別項包含規則名稱的選擇性人們可讀取表示。 例如，套用至物件的  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 如果有嚴格的效能原因，而最小化在原始程式檔隱藏項目中繼資料，規則名稱本身可以省略。規則類別和其規則識別碼一起構成充分唯一的規則識別項。 例如，套用至物件的  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 因為可維護性問題，所以不建議這種格式。  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>方法主體中隱藏多個違規  
 屬性只能套用至方法，而且不可以內嵌在方法主體。 不過，您可以指定的識別碼做為訊息識別碼來區別的方法內發生違規的多個項目。  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-csharp[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## <a name="generated-code"></a>產生的程式碼  
 Managed 程式碼編譯器和某些協力廠商工具產生程式碼，以便快速的程式碼開發。 出現在原始程式檔的編譯器所產生程式碼通常會標示**GeneratedCodeAttribute**屬性。  
  
 您可以選擇是否要隱藏程式碼分析警告與錯誤產生的程式碼。 如需如何隱藏這類警告和錯誤的資訊，請參閱[如何： 隱藏產生的程式碼的警告](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)。  
  
 請注意，程式碼分析會略過**GeneratedCodeAttribute**套用至整個組件或單一參數時。 這些情況下很少發生。  
  
## <a name="global-level-suppressions"></a>全域層級隱藏項目  
 Managed 程式碼分析工具會檢查**SuppressMessage**會套用到組件、 模組、 類型、 成員或參數的層級的屬性。 它也會引發對資源和命名空間的違規。 這些違規必須在全域層級套用，並為範圍並為目標。 例如，下列訊息會隱藏命名空間違規：  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  當您隱藏警告，並且包含命名空間範圍內時，它會抑制警告針對命名空間本身。 它不會隱藏對型別在命名空間中的警告。  
  
 可以表示任何隱藏項目，藉由指定明確的範圍。 這些隱藏項目必須駐留在全域層級。 您無法指定成員層級隱藏項目，而將型別。  
  
 全域層級隱藏項目會隱藏編譯器產生的程式碼不會對應至提供明確的使用者來源是指的訊息的唯一方式。 例如，下列程式碼會隱藏編譯器發出的建構函式的違規：  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  目標一定會包含完整項目名稱。  
  
## <a name="global-suppression-file"></a>全域隱藏項目檔  
 全域隱藏項目檔案維護的全域層級隱藏項目或未指定目標的隱藏項目的隱藏項目。 例如，組件層級違規的隱藏項目會儲存此檔案中。 此外，某些 ASP.NET 隱藏項目會儲存在這個檔案中，因為專案層級設定不適用於表單背後的程式碼。 建立全域隱藏項目並將其加入您的專案選取 第一次**專案隱藏項目檔中**選項**隱藏訊息**錯誤清單 視窗中命令。 如需詳細資訊，請參閱[How to： 使用功能表項目隱藏的警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Diagnostics.CodeAnalysis>