---
title: 原始檔隱藏專案中的總覽 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 63d405b0e62735c0c1e3d7bb716ea2db29bc19fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651567"
---
# <a name="in-source-suppression-overview"></a>原始檔中隱藏項目概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

原始碼隱藏功能可讓您藉由將 **SuppressMessage** 屬性新增至造成違規的程式碼區段，來隱藏或忽略 managed 程式碼中的程式碼分析違規。 **SuppressMessage**屬性是條件式屬性，只有在編譯時期定義了 CODE_ANALYSIS 編譯符號時，才會包含在 managed 程式碼元件的 IL 中繼資料中。

 在 C++/CLI 中，若要加入此屬性，請在標頭檔中使用 CA_SUPPRESS_MESSAGE 或 CA_GLOBAL_SUPPRESS_MESSAGE 巨集。

 您不應該在發行組建上使用原始檔中的隱藏專案，以防止意外傳送來源隱藏中繼資料。 由於來源內抑制的處理成本，您的應用程式效能也可以藉由包含來源內抑制中繼資料來降低。

> [!NOTE]
> 您不需要自行為這些屬性編寫程式碼。 如需詳細資訊，請參閱 [如何：使用功能表項目隱藏警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。 C + + 程式碼無法使用功能表項目。

## <a name="suppressmessage-attribute"></a>SuppressMessage 屬性
 當您以滑鼠右鍵按一下 [ **錯誤清單** ] 中的程式碼分析警告，然後按一下 [ **隱藏訊息 (s) **] 時，就會在您的程式碼或專案的全域隱藏專案檔中新增 **SuppressMessage** 屬性。

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

- **規則類別** -規則定義所在的分類。 如需程式碼分析規則類別的詳細資訊，請參閱 [Managed 程式碼警告的程式碼分析](../code-quality/code-analysis-for-managed-code-warnings.md)。

- **規則** 識別碼-規則的識別碼。 支援包含規則識別碼的簡短和完整名稱。 簡短名稱是 CAXXXX;完整名稱是 CAXXXX： FriendlyTypeName。

- **理由** -用來記錄隱藏訊息原因的文字。

- **訊息識別碼** -每個訊息之問題的唯一識別碼。

- **範圍** -隱藏警告的目標。 如果未指定目標，則會將它設定為屬性的目標。 支援的範圍包括下列各項：

  - 模組

  - 命名空間

  - 資源

  - 類型

  - member

- **目標** -用來指定要隱藏警告之目標的識別碼。 它必須包含完整的專案名稱。

## <a name="suppressmessage-usage"></a>SuppressMessage 使用方式
 程式碼分析警告會隱藏在套用 **SuppressMessage** 屬性實例的層級上。 這項功能的目的是要將隱藏的資訊緊密地結合到違規發生的程式碼。

 隱藏專案的一般形式包括規則類別目錄和規則識別碼，其中包含規則名稱的選擇性人類可讀取標記法。 例如，

 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

 如果最小化來源隱藏專案中繼資料的效能有嚴格的原因，則規則名稱本身可以是空的。規則類別和其規則識別碼會形成足夠的唯一規則識別碼。 例如，

 `[SuppressMessage("Microsoft.Design", "CA1039")]`

 因為可維護性問題，所以不建議使用此格式。

## <a name="suppressing-multiple-violations-within-a-method-body"></a>隱藏方法主體內的多個違規
 屬性只能套用至方法，無法內嵌于方法主體內。 不過，您可以指定識別碼作為訊息識別碼，以區分方法內出現的多次違規。

 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]

## <a name="generated-code"></a>產生的程式碼
 Managed 程式碼編譯器和一些協力廠商工具會產生程式碼，以加速程式碼開發。 出現在原始程式檔中的編譯器產生程式碼通常會以 **GeneratedCodeAttribute** 屬性標記。

 您可以選擇是否要隱藏所產生程式碼的程式碼分析警告和錯誤。 如需如何隱藏這類警告和錯誤的詳細資訊，請參閱 [如何：隱藏所產生程式碼的警告](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)。

 請注意，當程式碼套用至整個元件或單一參數時，程式碼分析會忽略 **GeneratedCodeAttribute** 。 這種情況很少發生。

## <a name="global-level-suppressions"></a>全域層級隱藏
 Managed 程式碼分析工具會檢查元件、模組、類型、成員或參數層級所套用的 **SuppressMessage** 屬性。 它也會對資源和命名空間引發違規。 這些違規必須套用到全域層級，並設定範圍並設為目標。 例如，下列訊息會抑制命名空間違規：

 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> 當您隱藏命名空間範圍的警告時，它會抑制對命名空間本身的警告。 它不會對命名空間中的類型隱藏警告。

 任何隱藏專案都可以藉由指定明確的範圍來表示。 這些隱藏項必須存留在全域層級。 您無法藉由裝飾類型來指定成員層級隱藏專案。

 全域層級隱藏的唯一方法是隱藏參考編譯器產生之程式碼的訊息，而該程式碼不會對應至明確提供的使用者來源。 例如，下列程式碼會針對編譯器發出的函式抑制違規：

 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> 目標一律包含完整的專案名稱。

## <a name="global-suppression-file"></a>全域隱藏專案檔
 全域隱藏專案檔會維護不指定目標的全域層級隱藏專案或隱藏專案。 例如，元件層級違規的隱藏項會儲存在此檔案中。 此外，某些 ASP.NET 隱藏專案會儲存在此檔案中，因為表單背後的程式碼無法使用專案層級設定。 當您第一次在 [錯誤清單] 視窗中，選取 [**抑制 Message (s) ** ] 命令的 [**在專案隱藏**檔] 選項時，就會建立全域隱藏專案並加入至您的專案。 如需詳細資訊，請參閱 [如何：使用功能表項目隱藏警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。

## <a name="see-also"></a>另請參閱
 <xref:System.Diagnostics.CodeAnalysis>
