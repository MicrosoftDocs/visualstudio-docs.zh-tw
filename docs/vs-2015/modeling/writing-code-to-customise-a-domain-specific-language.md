---
title: 撰寫程式碼以自訂域特定語言 |Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662979"
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>撰寫程式碼來自訂網域指定的語言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本節說明如何使用自訂程式碼，以特定領域語言存取、修改或建立模型。

 有幾個內容可以讓您撰寫可搭配 DSL 使用的程式碼：

- **自訂命令。** 您可以建立一個命令，讓使用者以滑鼠右鍵按一下圖表，然後可以修改模型來叫用。 如需詳細資訊，請參閱[如何：將命令新增至快捷方式功能表](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)。

- **Validation (驗證)，** 您可以撰寫程式碼來驗證模型是否處於正確的狀態。 如需詳細資訊，請參閱[使用特定領域語言進行驗證](../modeling/validation-in-a-domain-specific-language.md)。

- **覆寫預設行為。** 您可以修改從 Dsldefinition.dsl 檔產生之程式碼的許多層面。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。

- **文字轉換。** 您可以撰寫包含存取模型之程式碼的文字模板，並產生文字檔，例如產生程式碼。 如需詳細資訊，請參閱[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

- **其他 Visual Studio 延伸模組。** 您可以撰寫個別的 VSIX 擴充功能來讀取和修改模型。 如需詳細資訊，請參閱[如何：在程式碼中從檔案開啟模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  您在 Dsldefinition.dsl 檔中定義的類別實例會保存在稱為*記憶體內部存放區*（IMS）或*存放區*的資料結構中。 您在 DSL 中定義的類別，一律會將存放區當做引數提供給函式。 例如，如果您的 DSL 定義一個稱為範例的類別：

  `Example element = new Example (theStore);`

  將物件保留在存放區中（而不是一般物件）會提供數個優點。

- **交易**。 您可以將一系列相關的變更分組到一個交易中：

   `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

   `{`

   `// make several changes to Store elements here`

   `t.Commit();`

   `}`

   如果在變更期間發生例外狀況，所以不會執行最後的認可（），儲存區將會重設為其先前的狀態。 這可協助您確保錯誤不會讓模型處於不一致的狀態。 如需詳細資訊，請參閱[在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

- **二進位關聯**性。 如果您定義兩個類別之間的關聯性，則兩端的實例都會有一個可流覽至另一端的屬性。 這兩個端點一律會進行同步處理。 例如，如果您使用名為父系和子系的角色來定義 parenthood 關聯性，您可以撰寫：

   `John.Children.Add(Mary)`

   下列兩個運算式現在都是 true：

   `John.Children.Contains(Mary)`

   `Mary.Parents.Contains(John)`

   您也可以藉由撰寫來達到相同的效果：

   `Mary.Parents.Add(John)`

   如需詳細資訊，請參閱[在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

- **規則和事件**。 您可以定義在進行指定的變更時引發的規則。 例如，您可以使用規則，讓圖表上的圖形與所呈現的模型元素保持在最新狀態。 如需詳細資訊，請參閱[回應和傳播變更](../modeling/responding-to-and-propagating-changes.md)。

- **序列化**。 存放區提供將其包含的物件序列化為檔案的標準方式。 您可以自訂序列化和還原序列化的規則。 如需詳細資訊，請參閱[自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)。

## <a name="see-also"></a>請參閱
 [自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)
