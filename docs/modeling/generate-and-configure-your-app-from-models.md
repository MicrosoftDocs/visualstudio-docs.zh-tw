---
title: 透過模型產生和設定應用程式
description: 瞭解模型所代表的內容，以及如何從模型產生或設定應用程式的元件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 68339159ed9926490f22a82cd30ce69f45ab6a30
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388863"
---
# <a name="generate-and-configure-your-app-from-models"></a>透過模型產生和設定應用程式
您可以透過模型產生或設定應用程式的各部分。

 模型在呈現需求方面比程式碼更為直接。 直接從模型中衍生應用程式的行為，會比更新程式碼更能快速並可靠地回應變更的需求。 雖然需要進行一些初始工作才能設定衍生，但是如果您預期需求會變更，或打算進行產品的數個變化，則會傳回這項投資。

## <a name="generating-the-code-of-your-application-from-a-model"></a>透過模型產生應用程式碼
 產生程式碼的最簡單方式是使用文字範本。 您可以在保留模型的相同 Visual Studio 方案中產生程式碼。 如需詳細資訊，請參閱

- [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)

  這種方法很容易透過累加方式套用。 從僅適用於特定案例的應用程式開始進行，然後選擇應用程式中想要與模型不同的一些組件。 重新命名這些組件的原始程式檔，讓它們變成文字範本 (.tt) 檔案。 目前，將會透過範本檔案自動產生來源 .cs 檔案，讓應用程式像以前一樣地運作。

  然後，您可以取得一部分的程式碼，並將它取代為文字範本運算式，而運算式會讀取模型並產生原始程式檔的那個部分。 模型至少有一個值應該產生原始程式檔，讓您可以再次執行應用程式，而且會像以前一樣地運作。 測試不同的模型值之後，即可繼續進行程式碼之另一個組件中的插入範本運算式。

  這種累加方法表示產生程式碼通常是一種低風險方式。 所產生應用程式的執行效能通常會像手動撰寫的版本一樣好。

  不過，如果您從現有應用程式開始進行，則可能會發現需要進行許多重構，才能區隔模型所控管的不同行為，讓它們各自不同。 建議您在預估專案成本時評估應用程式的這個層面。

## <a name="configuring-your-application-from-a-model"></a>透過模型設定應用程式
 如果您想要改變應用程式在執行階段的行為，則無法使用程式碼產生，而程式碼產生會在編譯應用程式之前產生原始程式碼。 相反地，您可以設計應用程式以讀取模型，並據此改變其行為。 如需詳細資訊，請參閱

- [如何：在程式碼中開啟檔案的模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  這種方法也可以透過累加方式套用，但是開始時還需要進行其他工作。 您需要撰寫可讀取模型的程式碼，以及設定一個允許變動組件存取其值的架構。 將變動組件設為一般的成本高於程式碼產生。

  一般應用程式的執行效能通常不像其特定對應項目一樣好。 如果效能十分重要，則您的專案計劃應該包含這項風險的評估。

## <a name="developing-a-derived-application"></a>開發衍生的應用程式
 您可能會發現下列一般方針十分有用。

- **啟動特定，然後一般化。** 先撰寫應用程式的特定版本。 這個版本應該作用於一組條件。 滿意其運作正常狀態時，即可讓它的一部分衍生自模型。 逐漸擴充衍生的組件。

     例如，在您設計 web 應用程式來呈現模型中所定義的頁面之前，請先設計具有一組特定網頁的網站。

- **建立變化層面的模型。** 識別將會改變的層面 (兩個部署之間，或一段時間的需求變更)。 這些是應該衍生自模型的層面。

     例如，如果一組網頁和兩者之間的連結變更，但頁面的樣式和格式一律相同，則模型應該描述連結，但不需要描述頁面的格式。

- **個別的考慮。** 如果變動層面可以分成獨立區域，請為每個區域使用不同的模型。 使用 ModelBus，您可以定義影響兩個模型的作業以及其間的條件約束。

     例如，使用一個模型來定義網頁與不同模型之間的導覽，以定義頁面的版面配置。

- **模型化需求，而非方案。** 設計模型，使其能描述使用者需求。 反之，請不要根據實作的變動層面來設計標記法。

     例如，web 導覽模型應該代表網頁和兩者之間的超連結。 Web 流覽模型不應代表應用程式中的 HTML 或類別片段。

- **產生或解讀？** 如果特定部署的需求極少變更，請透過模型產生程式碼。 如果需求可能經常變更，或可能共存於相同部署的多個變異中，請撰寫應用程式，使它可以讀取和轉譯模型。

     例如，如果您使用網站模型來開發一連串不同和個別安裝的網站，則應該從模型產生網站的程式碼。 但是，您可以使用您的模型來控制每天變更的網站，因此最好是撰寫可讀取模型並據以呈現網站的網頁伺服器。

- **UML 或 DSL？** 請考慮使用造型來擴充 UML 以建立模型標記法。 如果沒有符合用途的 UML 圖表，請定義 DSL。 但是，請避免破壞 UML 的標準語意。

     例如，UML 類別圖是方塊與箭號的集合；運用這個標記法，您理論上可以定義任何項目。 但是，不建議您使用類別圖，而事實上描述一組類型的位置除外。 例如，您可以調整類別圖來描述不同類型的網頁。

## <a name="see-also"></a>另請參閱

- [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)
- [如何：在程式碼中開啟檔案的模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
