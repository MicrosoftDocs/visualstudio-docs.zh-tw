---
title: 使用 DSL 程式庫共用 DSL 之間的類別
description: 瞭解在 Visual Studio 的視覺效果和模型 SDK 中，您可以建立不完整的 DSL 定義，以將其匯入至另一個 DSL。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3729e4f386ec5a21c8f30ee3f0df6e7ffa8d891
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385496"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>使用 DSL 程式庫共用 DSL 之間的類別
在 Visual Studio 的視覺效果和模型 SDK 中，您可以建立不完整的 DSL 定義，以將其匯入至另一個 DSL。 這可讓您考慮類似模型的一般部分。

## <a name="creating-and-using-dsl-libraries"></a>建立和使用 DSL 程式庫

#### <a name="to-create-a-dsl-library"></a>建立 DSL 程式庫

1. 建立新的 DSL 專案，然後選擇 [DSL 程式庫] 解決方案範本。

     將會使用空的模型來建立單一 DSL 專案。

2. 您可以新增網域類別、關聯性、圖形等等。

     程式庫中的元素不需要形成單一嵌入樹狀結構。

     若要定義匯入工具可以使用的關聯性，請建立兩個網域類別，並在兩者之間建立關聯性。

     請考慮將網域類別的 **繼承修飾** 詞設定為 `Abstract` 。

3. 您可以新增在 [DSL Explorer] 中定義的元素，例如連接產生器。

4. 您可以加入需要額外程式碼的自訂，例如驗證條件約束。

5. 按一下 [ **轉換所有範本**]。

6. 建置專案。

7. 當您將 DSL 散發給其他人使用時，您必須同時提供已編譯的元件 (DLL) 和檔案 `DslDefinition.dsl` 。 您可以在底下的資料夾中找到已編譯的元件 `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>匯入 DSL 程式庫

1. 在另一個 DSL 定義的 [ **Dsl Explorer**] 中，以滑鼠右鍵按一下 dsl 的根類別，然後按一下 [ **新增 DslLibrary 匯入**]。

2. 在屬性視窗中，設定文件庫的檔案 **路徑** 。 您可以使用相對或絕對路徑。

    匯入的程式庫會以唯讀模式出現在 [DSL Explorer] 中。

3. 您可以使用匯入的類別做為基類。 在匯入 DSL 中建立網域類別，並在屬性視窗中，將 **基類** 設定為匯入的類別。

4. 按一下 [轉換所有範本]。

5. 將元件的參考加入至 DSL 專案， (DLL) 由 DSL 程式庫專案所建立。

6. 建置方案。

   DSL 程式庫可以匯入其他程式庫。 當您匯入程式庫時，其匯入也會自動出現在 [DSL Explorer] 中。

## <a name="see-also"></a>另請參閱

- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
