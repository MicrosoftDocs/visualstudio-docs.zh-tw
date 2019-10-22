---
title: 使用 DSL 程式庫共用 DSL 之間的類別
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5293473e35424ccc6ee357d63a9355cacf0d6725
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670755"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>使用 DSL 程式庫共用 DSL 之間的類別
在 Visual Studio 視覺效果和模型化 SDK 中，您可以建立一個不完整的 DSL 定義，讓您可以將其匯入至另一個 DSL。 這可讓您將類似模型的常見部分納入考慮。

## <a name="creating-and-using-dsl-libraries"></a>建立和使用 DSL 程式庫

#### <a name="to-create-a-dsl-library"></a>建立 DSL 程式庫

1. 建立新的 DSL 專案，然後選擇 [DSL 程式庫] 方案範本。

     將使用空的模型建立單一 DSL 專案。

2. 您可以加入網域類別、關聯性、圖形等等。

     程式庫中的元素不需要形成單一內嵌樹狀結構。

     若要定義匯入工具可以使用的關聯性，請建立兩個網域類別，並建立它們之間的關聯性。

     請考慮將網域類別的**繼承修飾**詞設定為 `Abstract`。

3. 您可以加入您在 DSL Explorer 中定義的元素，例如連接產生器。

4. 您可以加入需要額外程式碼的自訂，例如驗證條件約束。

5. 按一下 [**轉換所有範本**]。

6. 建置專案。

7. 當您散發 DSL 供其他人使用時，您必須同時提供已編譯的元件（DLL）和檔案 `DslDefinition.dsl`。 您可以在下的資料夾中找到已編譯的元件 `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>匯入 DSL 程式庫

1. 在另一個 DSL 定義的 [ **Dsl Explorer**] 中，以滑鼠右鍵按一下 dsl 的根類別，然後按一下 [**新增 DslLibrary 匯入**]。

2. 在 屬性視窗中，設定**文檔**庫的檔案路徑。 您可以使用相對或絕對路徑。

    匯入的程式庫會在 [DSL Explorer] 中以唯讀模式顯示。

3. 您可以使用匯入的類別做為基類。 在匯入 DSL 中建立網域類別，然後在屬性視窗中，將**基類**設定為匯入的類別。

4. 按一下 [轉換所有範本]。

5. 將 DSL 程式庫專案所建立之元件（DLL）的參考新增至 DSL 專案。

6. 建置方案。

   DSL 程式庫可以匯入其他程式庫。 當您匯入程式庫時，其匯入也會自動顯示在 DSL Explorer 中。

## <a name="see-also"></a>請參閱

- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
