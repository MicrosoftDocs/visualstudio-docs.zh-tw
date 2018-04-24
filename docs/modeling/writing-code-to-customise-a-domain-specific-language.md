---
title: 自訂網域特定領域語言
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: e441de64c955fcc6780c4606a5a9855907d63f9f
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>撰寫程式碼以自訂特定領域語言

本節說明如何使用自訂程式碼存取、 修改或建立特定領域語言的模型。

有數種內容中，您可以撰寫可搭配 DSL 的程式碼：

-   **自訂命令。** 您可以建立命令，使用者可以叫用，以滑鼠右鍵按一下圖表中，並且它可以修改模型。 如需詳細資訊，請參閱[如何： 新增命令至捷徑功能表](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)。

-   **Validation (驗證)，** 您可以撰寫程式碼，用來驗證模型處於正確狀態。 如需詳細資訊，請參閱[中特定領域語言驗證](../modeling/validation-in-a-domain-specific-language.md)。

-   **覆寫預設行為。** 您可以修改 DslDefinition.dsl 從產生的程式碼的許多層面。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。

-   **文字轉換。** 您可以撰寫文字範本，其中包含存取模型，並產生文字檔案，例如若要產生程式碼的程式碼。 如需詳細資訊，請參閱[特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

-   **其他 Visual Studio 擴充功能。** 您可以撰寫個別的 VSIX 擴充功能的讀取和修改模型。 如需詳細資訊，請參閱[How to： 從程式碼中的檔案中開啟模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)

您在 DslDefinition.dsl 中定義的類別執行個體保留在資料結構，稱為*記憶體中存放區*(IMS) 或*存放區*。 您一律在 DSL 中定義的類別建構函式做為引數需要存放區。 例如，如果 DSL 定義類別，呼叫範例：

`Example element = new Example (theStore);`

在保留物件 （而不是只為一般物件） 的存放區中有數個優點。

-   **交易**。 您可以分組到某交易內的相關變更的一系列：

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     使最終的 commit （） 不會執行變更時，發生例外狀況，如果存放區將會重設為先前的狀態。 這可協助您確認該錯誤不會讓模型處於不一致的狀態。 如需詳細資訊，請參閱[巡覽和更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

-   **二進位關聯性**。 如果您定義兩個類別之間的關聯性，在兩端的執行個體就會有另一端的導覽屬性。 一律會同步處理兩個端點。 例如，如果您使用名為父代和子系的角色定義 parenthood 關聯性，您可以撰寫：

     `John.Children.Add(Mary)`

     現在，這兩個下列運算式是 true:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     您也可以撰寫，以達到相同的效果：

     `Mary.Parents.Add(John)`

     如需詳細資訊，請參閱[巡覽和更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

-   **規則和事件**。 您可以定義規則，指定變更時就會引發。 規則使用，例如，要保留在圖表上的圖形的最新狀態所呈現的模型項目。 如需詳細資訊，請參閱[回應和傳播變更](../modeling/responding-to-and-propagating-changes.md)。

-   **序列化**。 存放區提供的標準方式序列化至檔案包含的物件。 您可以自訂序列化和還原序列化的規則。 如需詳細資訊，請參閱[自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)。

## <a name="see-also"></a>另請參閱

- [自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)