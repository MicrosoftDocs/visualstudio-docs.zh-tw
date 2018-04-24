---
title: 計算及自訂的儲存區屬性
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1bdf6d413287f75fa57ef80525a43f86cd55c74d
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="calculated-and-custom-storage-properties"></a>計算及自訂的儲存區屬性
特定領域語言 (DSL) 中的所有網域屬性可以顯示在圖表上和您語言總管中，對使用者和程式碼可以存取。 不過，屬性不同，其值會儲存的方式。

## <a name="kinds-of-domain-properties"></a>類型的定義域屬性
 DSL 定義中，您可以設定**種類**的網域屬性，如下表中所列：

|網域屬性類型|描述|
|--------------------------|-----------------|
|**標準**（預設值）|儲存在網域屬性*儲存*和序列化為檔案。|
|**計算**|唯讀的網域屬性不會儲存在存放區，但會從其他值計算出。<br /><br /> 例如，`Person.Age`無法從計算`Person.BirthDate`。<br /><br /> 您必須提供程式碼會執行計算。 一般而言，您會計算來自其他網域屬性的值。 不過，您也可以使用外部資源。|
|**自訂儲存體**|網域屬性不會儲存直接在存放區，但可以是 get 和 set。<br /><br /> 您必須提供的方法，取得並設定的值。<br /><br /> 例如，`Person.FullAddress`可以儲存在`Person.StreetAddress`， `Person.City`，和`Person.PostalCode`。<br /><br /> 您也可以存取外部資源，例如若要取得並設定資料庫中的值。<br /><br /> 您的程式碼不應該設定存放區中的值時`Store.InUndoRedoOrRollback`為 true。 請參閱[交易和自訂的 Setter](#setters)。|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>提供程式碼的導出或自訂的儲存體屬性
 如果您將網域屬性的種類為計算或自訂儲存體，您必須提供存取方法。 當您建置方案時，錯誤報表會告訴您所需內容。

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>若要定義導出或自訂的儲存體屬性

1.  在 DslDefinition.dsl，選取的網域屬性，在圖表中或在**DSL 總管**。

2.  在**屬性**視窗中，將**種類**欄位設為**計算**或**自訂儲存體**。

     請確定您有也設定其**類型**想要查看。

3.  按一下**轉換所有範本**的工具列中的**方案總管 中**。

4.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

     您收到下列錯誤訊息: 「*YourClass*不包含定義 get*YourProperty*。 」

5.  按兩下錯誤訊息。

     Dsl\GeneratedCode\DomainClasses.cs 或 DomainRelationships.cs 隨即開啟。 反白顯示的方法呼叫上方註解會提示您提供實作 get*YourProperty*（)。

    > [!NOTE]
    >  這個檔案是從 DslDefinition.dsl 產生。 如果您編輯此檔案，您的變更將會遺失您按一下 下一次**轉換所有範本**。 相反地，加入所需的方法，在個別的檔案。

6.  建立或開啟類別檔案，在個別的資料夾，例如 CustomCode\\*YourDomainClass*。 cs。

     請確定命名空間是產生的程式碼相同。

7.  類別檔案中寫入網域類別的部分的實作。 在類別中，撰寫的定義。 遺漏`Get`與下列範例類似的方法：

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8.  如果您設定**種類**至**自訂儲存體**，您也必須提供`Set`方法。 例如: 

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     您的程式碼不應該設定存放區中的值時`Store.InUndoRedoOrRollback`為 true。 請參閱[交易和自訂的 Setter](#setters)。

9. 建置並執行方案。

10. 測試屬性。 請確定您嘗試**復原**和**重做**。

##  <a name="setters"></a> 交易和自訂的 Setter
 在自訂儲存體屬性的 Set 方法，您不必開啟交易，因為在使用中交易內通常呼叫方法。

 不過，如果在使用者叫用復原或取消復原，或正在復原交易，可能也稱為 Set 方法。 當<xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A>為 true，Set 方法的行為，如下所示：

-   它不應該在存放區，例如將值指派至其他網域屬性進行變更。 復原管理員會設定其值。

-   不過，它應該更新任何外部的資源，例如資料庫或檔案內容中或外部存放區物件。 如此可確保它們會保留在 synchronism 存放區中的值。

 例如: 

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

 如需有關交易的詳細資訊，請參閱[巡覽和更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

## <a name="see-also"></a>另請參閱

- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [網域屬性的屬性](../modeling/properties-of-domain-properties.md)
- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)