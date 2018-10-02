---
title: 原始檔中隱藏項目概觀 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7f02a57be8d267126deb6736c9e0a690b1ac3e2d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491772"
---
# <a name="in-source-suppression-overview"></a>原始檔中隱藏項目概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[在來源隱藏項目概觀](https://docs.microsoft.com/visualstudio/code-quality/in-source-suppression-overview)。  
  
在原始程式檔隱藏項目是隱藏或忽略 managed 程式碼中的程式碼分析違規加上能夠**SuppressMessage**屬性會造成違規的程式碼區段。 **SuppressMessage**屬性是在編譯時期定義 CODE_ANALYSIS 編譯的符號時，才會包含您的 managed 程式碼組件的 IL 中繼資料中的條件式屬性。  
  
 在 C++/CLI 中，若要加入此屬性，請在標頭檔中使用 CA_SUPPRESS_MESSAGE 或 CA_GLOBAL_SUPPRESS_MESSAGE 巨集。  
  
 您不應該使用在原始程式檔的隱藏項目上的發行組建，以避免不小心傳送來源在隱藏項目中繼資料。 在原始程式檔隱藏項目處理成本，因為您的應用程式的效能也會降低包含在原始程式檔隱藏項目中繼資料。  
  
> [!NOTE]
>  您沒有交給程式碼這些屬性自行。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用功能表項目隱藏的警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。 找不到適用於 c + + 程式碼的功能表項目。  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage 屬性  
 當您以滑鼠右鍵按一下中的程式碼分析警告**錯誤清單**，然後按一下 **隱藏訊息**，則**SuppressMessage**屬性會加入您的程式碼或為專案的全域隱藏項目檔案。  
  
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
  
-   **規則類別**-規則定義所在的類別。 如需程式碼分析規則類別的詳細資訊，請參閱[程式碼分析 Managed 程式碼警告](../code-quality/code-analysis-for-managed-code-warnings.md)。  
  
-   **規則 Id** -規則的識別碼。 支援包括同時短期和長期的規則識別項的名稱。 簡短名稱是 CAXXXX;CAXXXX:FriendlyTypeName 長的名稱。  
  
-   **理由**-用來記錄原因隱藏訊息的文字。  
  
-   **訊息識別碼**-每個訊息發生問題的唯一識別碼。  
  
-   **範圍**-在其要隱藏警告的目標。 如果未指定目標，則會將它設定為屬性的目標。 支援的範圍包括下列各項：  
  
    -   Module  
  
    -   命名空間  
  
    -   資源  
  
    -   類型  
  
    -   成員  
  
-   **目標**-識別項，用來指定在其要隱藏警告的目標。 它必須包含完整項目名稱。  
  
## <a name="suppressmessage-usage"></a>SuppressMessage 使用量  
 程式碼分析警告會隱藏的層級的執行個體**SuppressMessage**屬性會套用。 的目的是緊密結合的程式碼的隱藏項目資訊發生違規的位置。  
  
 一般格式的隱藏項目包含規則的類別和包含選擇性的人們可讀取表示法，規則名稱的規則識別碼。 例如，套用至物件的  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 如果有最小化在原始程式檔隱藏項目中繼資料的嚴格的效能考量，規則名稱本身可以省略了。規則類別和其規則識別碼一起構成夠唯一的規則識別項。 例如，套用至物件的  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 因為可維護性問題而不建議這種格式。  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>在方法主體中隱藏多個違規  
 屬性只能套用至方法，而且不可以內嵌在方法主體。 不過，您也可以做為訊息識別碼來區別多個項目違反方法內的指定識別項。  
  
 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]  
  
## <a name="generated-code"></a>產生的程式碼  
 Managed 程式碼編譯器和某些協力廠商工具產生程式碼，以便快速的程式碼開發。 編譯器所產生的程式碼會出現在原始程式檔，通常會標示**GeneratedCodeAttribute**屬性。  
  
 您可以選擇是否要隱藏程式碼分析警告與錯誤產生的程式碼。 如需如何隱藏這類警告和錯誤的資訊，請參閱[如何： 隱藏的警告，產生的程式碼](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)。  
  
 請注意，程式碼分析忽略**GeneratedCodeAttribute**套用至整個組件或單一參數時。 這些情況下很少發生。  
  
## <a name="global-level-suppressions"></a>全域層級隱藏項目  
 Managed 程式碼分析工具會檢查**SuppressMessage**會套用到組件、 模組、 類型、 成員或參數層級的屬性。 它也會引發對資源和命名空間的違規。 這些違規必須套用的全域層級是範圍和目標。 例如，下列訊息會隱藏命名空間違規：  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  當您隱藏警告，其中含有命名空間範圍時，它會隱藏對本身的命名空間的警告。 它不會抑制警告針對命名空間內的型別。  
  
 可以表示任何隱藏項目，藉由指定明確的範圍。 這些隱藏項目必須即時的全域層級。 您無法指定成員層級隱藏項目來裝飾型別。  
  
 全域層級隱藏項目會隱藏編譯器產生的程式碼未明確提供的使用者來源對應到參考的訊息的唯一方式。 例如，下列程式碼會封鎖對編譯器發出的建構函式的違規：  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  目標永遠會包含完整項目名稱。  
  
## <a name="global-suppression-file"></a>全域隱藏項目檔  
 全域隱藏項目檔案會維護的全域層級隱藏項目或未指定目標的隱藏項目會隱藏項目。 比方說，隱藏項目組件層級的違規會儲存此檔案中。 此外，有些 ASP.NET 隱藏項目會儲存在這個檔案中，因為專案層級設定不適用於表單後面的程式碼。 建立全域隱藏項目並將其加入您的專案，您選取第一次**專案隱藏項目檔中的流程範本**選項**隱藏訊息**命令，在 [錯誤清單] 視窗。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用功能表項目隱藏的警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.CodeAnalysis>



