---
title: 計算及自訂的儲存區屬性
description: 瞭解特定領域語言中的所有網域屬性 (DSL) 如何顯示給使用者在圖表和您的 language explorer 中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f98dca6759b9e4a77e71139b6d9ec9b394d99b04
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385418"
---
# <a name="calculated-and-custom-storage-properties"></a>計算及自訂的儲存區屬性
特定領域語言中的所有網域屬性 (DSL) 可在圖表和您的 language explorer 中顯示給使用者，並且可透過程式碼存取。 但是，屬性的值儲存方式會有所不同。

## <a name="kinds-of-domain-properties"></a>網域屬性的種類
 在 DSL 定義中，您可以設定網域屬性的 **種類** ，如下表所示：

|網域屬性種類|描述|
|-|-|
|**標準** (預設) |*儲存在存放區* 中並序列化為檔案的網域屬性。|
|**導出**|唯讀網域屬性，不會儲存在存放區中，而是從其他值計算而來。<br /><br /> 例如， `Person.Age` 可以從計算 `Person.BirthDate` 。<br /><br /> 您必須提供執行計算的程式碼。 一般而言，您會從其他定義域屬性計算值。 不過，您也可以使用外部資源。|
|**自訂儲存體**|未直接儲存在存放區中，但可以是 get 和 set 的網域屬性。<br /><br /> 您必須提供取得和設定值的方法。<br /><br /> 例如， `Person.FullAddress` 可以儲存在 `Person.StreetAddress` 、和中 `Person.City` `Person.PostalCode` 。<br /><br /> 您也可以存取外部資源，例如，從資料庫取得和設定值。<br /><br /> 當為 true 時，您的程式碼不應設定存放區中的值 `Store.InUndoRedoOrRollback` 。 請參閱 [交易和自訂 setter](#setters)。|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>提供計算或自訂儲存體屬性的程式碼
 如果您將網域屬性的種類設定為 [計算] 或 [自訂] 儲存區，則必須提供存取方法。 當您建立方案時，錯誤報表會告訴您所需的內容。

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>若要定義計算或自訂的儲存體屬性

1. 在 [Dsldefinition.dsl 檔] 中，選取 [圖表] 或 [ **Dsl Explorer**] 中的網域屬性。

2. 在 [**屬性**] 視窗中，將 [**種類**] 欄位設定為 [**計算**] 或 [**自訂] 儲存體**

     請確定您也已將其類型設定為您想要的 **類型** 。

3. 在 **方案總管** 的工具列中，按一下 [**轉換所有範本**]。

4. 在 [建置] 功能表上，按一下 [建置方案]。

     您會收到下列錯誤訊息：「*YourClass* 不包含 Get *YourProperty* 的定義」。

5. 按兩下錯誤訊息。

     Dsl\GeneratedCode\DomainClasses.cs 或 DomainRelationships 會開啟。 在反白顯示的方法呼叫上方，批註會提示您提供 Get *YourProperty* () 的實作為。

    > [!NOTE]
    > 這個檔案是從 Dsldefinition.dsl 檔產生。 如果您編輯這個檔案，下次按一下 [ **轉換所有範本**] 時，您的變更將會遺失。 相反地，請在個別的檔案中新增必要的方法。

6. 在不同的資料夾中建立或開啟類別檔案，例如 CustomCode \\ *YourDomainClass*.cs。

     請確定命名空間與產生的程式碼中的命名空間相同。

7. 在類別檔案中，寫入網域類別的部分實作為。 在類別中，撰寫與 `Get` 下列範例類似的遺漏方法的定義：

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. 如果您將 **種類** 設定為 **自訂存放裝置**，您也必須提供 `Set` 方法。 例如：

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     當為 true 時，您的程式碼不應設定存放區中的值 `Store.InUndoRedoOrRollback` 。 請參閱 [交易和自訂 setter](#setters)。

9. 建置並執行解決方案。

10. 測試屬性。 請確定您嘗試 **復原** 和 **重做**。

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> 交易和自訂 Setter
 在 [自訂儲存] 屬性的 Set 方法中，您不需要開啟交易，因為通常會在使用中交易內呼叫該方法。

 不過，如果使用者叫用復原或重做，或回復交易，也可能會呼叫 Set 方法。 當 <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> 為 true 時，您的 Set 方法應如下所示：

- 它不應該在存放區中進行變更，例如將值指派給其他定義域屬性。 復原管理員將會設定其值。

- 但是，它應該會更新任何外部資源，例如資料庫或檔案內容，或存放區以外的物件。 這可確保它們會以存放區中的值保留在 synchronism 中。

  例如：

```
void SetAgeValue(int value)
{
  // If we are in Undo, no changes to Store objects:
  if (!this.Store.InUndoRedoOrRollback)
  {
    this.BirthYear = System.DateTime.Today.Year - value;
  }
  // But always update external objects:
  System.IO.File.WriteAllText(AgeFile, value);
}
```

 如需交易的詳細資訊，請參閱 [在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

## <a name="see-also"></a>另請參閱

- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [網域屬性的屬性](../modeling/properties-of-domain-properties.md)
- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
