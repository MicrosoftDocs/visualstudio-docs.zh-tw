---
title: 網域屬性的屬性
description: 瞭解定義域屬性是可保存值之模型專案的功能，以及定義域屬性如何列在圖表的 [網域類別] 方塊中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97bfbcf73a950692d5736b7a6e0b529cfe658caa
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361517"
---
# <a name="properties-of-domain-properties"></a>網域屬性的屬性
*網域屬性* 是可保存值之模型專案的功能。 例如，`Person` 網域類別可能具有屬性 `Name` 和 `BirthDate`。 在 DSL 定義中，網域屬性會列在圖表上的網域類別方塊中以及 DSL Explorer 中的網域類別之下。 如需詳細資訊，請參閱 [如何定義 Domain-Specific 語言](../modeling/how-to-define-a-domain-specific-language.md)。

> [!NOTE]
> "property" 一字有兩種用法。 *網域屬性* 是您在網域類別上定義的功能。 相較之下，DSL 的許多元素都有屬性，這些 *屬性* 會列在 dsl 定義的 [ **屬性** ] 視窗中。 例如，每個網域屬性都有一組屬性，這些屬性會在本主題中說明。

 在執行階段，當使用者建立網域類別的執行個體時，可以在 [屬性] 視窗中看到網域屬性的值，並可顯示在圖形上。

 大部分的網域屬性會以一般 CLR 屬性實作。 然而，從程式設計的觀點而言，網域屬性的功能比一般程式屬性的功能更豐富：

- 您可以定義監視屬性狀態的規則和事件。 如需詳細資訊，請參閱 [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。

- 異動有助於防止不一致的狀態。 如需詳細資訊，請參閱 [在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

  當您在圖表或 DSL Explorer 中選取 [網域屬性] 時，可以在 [屬性] 視窗中查看下列項目。 如需如何使用這些專案的詳細資訊，請參閱 [自訂和擴充 Domain-Specific 語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

|屬性|描述|預設值|
|-|-|-|
|**說明**|此描述可用來記載產生之設計工具的使用者介面 (UI)。|\<none>|
|**顯示名稱**|將在產生的設計工具中針對此網域屬性顯示的名稱。 它可以包含空格和標點符號，例如 "Song Title"。|\<none>|
|**項目名稱提供者**|如果您將 `Is Element Name` 設為 `true`，才適用此提供者。 您可以撰寫程式碼，為網域類別的新項目提供名稱，覆寫預設行為。<br /><br /> 在 DSL 專案的程式碼檔中，建立從 <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider> 衍生的類別。<br /><br /> 然後在 DSL Explorer 中，以滑鼠右鍵按一下 DSL 的根 ，然後按一下 [加入外部類型]。 輸入您的類別名稱。<br /><br /> 再度選取此網域屬性，然後在下拉式清單中選取類別的名稱。|\<none>|
|**Getter 存取修飾詞**|網域類別的存取層級 (`public` 或 `internal`)。 此層級可控制程式碼存取屬性的範圍。|`public`|
|**Help 關鍵字**|這個選擇性關鍵字可用來為此網域屬性編製 F1 說明的索引。|\<none>|
|**Is Browsable**|如果為 `True`，則在此 DSL 的模型開啟時，會在屬性視窗中向使用者顯示網域屬性。<br /><br /> 如果為 `False`，則在 UI 中會隱藏網域屬性。<br /><br /> 如果您想要讓網域屬性可見但唯讀，則設定為 [ **僅限 UI 唯讀**]。|`True`|
|**Is Element Name**|如果為 `True`，此網域屬性將在 DSL Explorer 中顯示為其模型項目的名稱。<br /><br /> 新的模型項目將接收此屬性的唯一預設值。 如果您想要控制這些值的產生方式，請設定 **元素名稱提供者**。|`False`|
|**Is UI Read Only**|如果為 `True`，則無法使用 UI 變更網域屬性的值。 它仍然可由程式設定，並且可以在 [屬性] 視窗中看見它。<br /><br /> 如果您想要從使用者隱藏網域屬性，請將設定 **為可流覽**。 如果您想要透過程式來控制存取權，請設定 **Setter 存取修飾** 詞。|`False`|
|**種類**|網域屬性的類型 (`Normal`、`Calculated` 或 `CustomStorage`)。 如需詳細資訊，請參閱 [計算和自訂儲存體屬性](../modeling/calculated-and-custom-storage-properties.md)。|`Normal`|
|**名稱**|此網域屬性的名稱。 它必須是有效的識別碼，例如 **SongTitle**。|\<none>|
|**備註**|與此網域屬性相關聯的非正式附註。|\<none>|
|**Setter 存取修飾詞**|Setter 的存取修飾詞。 此修飾詞可控制程式碼設定屬性的範圍。|`public`|
|**類型**|屬性的類型。 若要加入可用類型的清單，請以滑鼠右鍵按一下 [DSL explorer] 中 DSL 的根，然後按一下 [ **加入外部類型**]。|`String`|

## <a name="see-also"></a>請參閱

- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)