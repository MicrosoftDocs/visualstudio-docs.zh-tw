---
title: 撰寫程式碼以自訂域特定的語言 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4448e9a1c65ccba4a9ae48d0271f9fd91fc011b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662979"
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>撰寫程式碼來自訂網域指定的語言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本節說明如何使用自訂程式碼來存取、修改或建立特定領域語言的模型。

 您可以在幾個內容中撰寫可搭配 DSL 使用的程式碼：

- **自訂命令。** 您可以建立一個命令，讓使用者以滑鼠右鍵按一下圖表，然後可以修改模型，來叫用該命令。 如需詳細資訊，請參閱 [如何：將命令新增至快捷方式功能表](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)。

- **驗證。** 您可以撰寫驗證模型是否處於正確狀態的程式碼。 如需詳細資訊，請參閱 [以網域指定的語言進行驗證](../modeling/validation-in-a-domain-specific-language.md)。

- **覆寫預設行為。** 您可以修改 Dsldefinition.dsl 檔所產生之程式碼的許多層面。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。

- **文字轉換。** 您可以撰寫文字模板，其中包含可存取模型並產生文字檔的程式碼，例如，用來產生程式碼。 如需詳細資訊，請參閱 [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

- **其他 Visual Studio 延伸模組。** 您可以撰寫可讀取和修改模型的個別 VSIX 擴充功能。 如需詳細資訊，請參閱 [如何：在程式碼中從檔案開啟模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  您在 Dsldefinition.dsl 檔中定義之類別的實例會保留在資料結構中，稱為 *記憶體中存放區* (IMS) 或 *存放區*。 您在 DSL 中定義的類別一律會採用存放區做為函式的引數。 例如，如果您的 DSL 定義了稱為 Example 的類別：

  `Example element = new Example (theStore);`

  將物件保留在存放區中 (而不是一般物件) 提供數個優點。

- **Transactions**。 您可以將一連串相關的變更組成交易：

   `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

   `{`

   `// make several changes to Store elements here`

   `t.Commit();`

   `}`

   如果在變更期間發生例外狀況，所以不會執行最終認可 ( # A1，則存放區將重設為先前的狀態。 這可協助您確保錯誤不會讓模型處於不一致的狀態。 如需詳細資訊，請參閱 [在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

- **二元關聯**性。 如果您定義兩個類別之間的關聯性，兩端的實例都有一個可流覽至另一端的屬性。 這兩個端點一律會進行同步處理。 例如，如果您使用名為父系和子系的角色來定義 parenthood 關聯性，您可以撰寫：

   `John.Children.Add(Mary)`

   下列兩個運算式現在都成立：

   `John.Children.Contains(Mary)`

   `Mary.Parents.Contains(John)`

   您也可以撰寫下列內容來達成相同的效果：

   `Mary.Parents.Add(John)`

   如需詳細資訊，請參閱 [在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

- **規則和事件**。 您可以定義每當進行指定的變更時，就會引發的規則。 例如，您可以使用規則，將圖表上的圖形與它們所呈現的模型元素保持在最新狀態。 如需詳細資訊，請參閱 [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。

- **序列化**。 存放區提供將它所包含之物件序列化至檔案的標準方式。 您可以自訂序列化和還原序列化的規則。 如需詳細資訊，請參閱 [自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)。

## <a name="see-also"></a>另請參閱
 [自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)
