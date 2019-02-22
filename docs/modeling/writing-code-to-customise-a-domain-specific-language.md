---
title: 來自訂特定領域語言
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42cba18e3b02bb1bb4a8316f82c62ae50700ca8f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955410"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>撰寫程式碼來自訂特定領域語言

本節將說明如何使用自訂程式碼來存取、 修改或建立特定領域語言的模型。

有數種內容中，您可以撰寫與 DSL 搭配運作的程式碼：

-   **自訂命令。** 您可以建立命令的使用者可以用滑鼠右鍵按一下圖表中，叫用，並且它也可以修改模型。 如需詳細資訊，請參閱[＜How to：將命令加入至捷徑功能表](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)。

-   **Validation (驗證)，** 您可以撰寫程式碼，確認模型處於正確狀態。 如需詳細資訊，請參閱 <<c0> [ 定義域專屬語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)。

-   **覆寫預設行為。** 您可以修改 DslDefinition.dsl 從產生的程式碼的許多層面。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。

-   **文字轉換。** 您可以撰寫文字範本，其中包含存取模型，並產生文字檔案，例如若要產生程式碼的程式碼。 如需詳細資訊，請參閱 <<c0> [ 特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

-   **其他 Visual Studio 擴充功能。** 您可以撰寫個別的 VSIX 擴充功能來讀取和修改模型。 如需詳細資訊，請參閱[＜How to：從程式碼中的檔案中開啟模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)

您在 DslDefinition.dsl 中定義之類別執行個體保留在資料結構，稱為*記憶體中存放區*(IMS) 或*存放區*。 您一律在 DSL 中定義的類別建構函式做為引數需要存放區。 例如，如果您的 DSL 定義名為範例的類別：

`Example element = new Example (theStore);`

保留 （而不是只為一般的物件） 的存放區中的物件提供數個優點。

-   **交易**。 您可以分組到某交易相關的變更一系列：

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     如此就不會執行最終的 commit （） 進行變更時，發生例外狀況，如果先前的狀態將會重設的存放區。 這可協助您確定該錯誤不會讓模型處於不一致的狀態。 如需詳細資訊，請參閱 <<c0> [ 巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

-   **二進位關聯性**。 如果您定義兩個類別之間的關聯性，在兩端的執行個體就會具有瀏覽至另一端的屬性。 這兩個部分會一律會同步處理。 例如，如果您使用名為父代和子系的角色定義 parenthood 關聯性，您可以撰寫：

     `John.Children.Add(Mary)`

     現在，這兩個下列運算式是 true:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     您也可以撰寫，以達到相同的效果：

     `Mary.Parents.Add(John)`

     如需詳細資訊，請參閱 <<c0> [ 巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

-   **規則和事件**。 您可以定義規則，以指定有變更時就會引發。 會使用規則，比方說，保留最新的模型項目呈現在圖表上的圖形。 如需詳細資訊，請參閱 <<c0> [ 回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。

-   **序列化**。 存放區提供標準的方式來序列化至檔案包含的物件。 您可以自訂的規則來序列化和還原序列化。 如需詳細資訊，請參閱 <<c0> [ 自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)。

## <a name="see-also"></a>另請參閱

- [自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)