---
title: 計算和自訂儲存體屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 372159a7405eb7a350aa55c55cf0c7e582dc98e4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668364"
---
# <a name="calculated-and-custom-storage-properties"></a>計算及自訂的儲存區屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

特定領域語言（DSL）中的所有網域屬性都可以在圖表和您的語言瀏覽器中顯示給使用者，並可由程式碼存取。 不過，屬性的值儲存方式會不同。

## <a name="kinds-of-domain-properties"></a>網域屬性的種類
 在 DSL 定義中，您可以設定網域屬性的**種類**，如下表所列：

|網域屬性種類|描述|
|--------------------------|-----------------|
|**標準**（預設值）|*儲存在存放區*中並序列化為檔案的網域屬性。|
|**計**|唯讀網域屬性，不會儲存在存放區中，而是從其他值計算而來。<br /><br /> 例如，`Person.Age` 可以從 `Person.BirthDate` 計算出來。<br /><br /> 您必須提供執行計算的程式碼。 通常，您會計算來自其他網域屬性的值。 不過，您也可以使用外部資源。|
|**自訂儲存體**|不會直接儲存在存放區中，但可以同時取得和設定的網域屬性。<br /><br /> 您必須提供取得和設定值的方法。<br /><br /> 例如，`Person.FullAddress` 可以儲存在 `Person.StreetAddress`、`Person.City` 和 `Person.PostalCode` 中。<br /><br /> 您也可以存取外部資源，例如，從資料庫取得和設定值。<br /><br /> 當 `Store.InUndoRedoOrRollback` 為 true 時，您的程式碼不應設定存放區中的值。 請參閱[交易和自訂 setter](#setters)。|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>提供計算或自訂儲存屬性的程式碼
 如果您將網域屬性的種類設定為 [計算] 或 [自訂] 儲存體，則必須提供存取方法。 當您建立解決方案時，錯誤報表會告訴您所需的內容。

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>若要定義計算或自訂儲存體屬性

1. 在 Dsldefinition.dsl 檔中，于圖表或在 [ **Dsl Explorer**] 中選取 [網域] 屬性。

2. 在 [**屬性**] 視窗中，將 [**類型**] 欄位設定為 [**計算**] 或 [**自訂儲存體**]

     請確定您也將其**類型**設為您想要的內容。

3. 按一下**方案總管**工具列中的 [**轉換所有範本**]。

4. 在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

     您會收到下列錯誤訊息：「*YourClass*不包含 Get*YourProperty*的定義」。

5. 按兩下錯誤訊息。

     Dsl\GeneratedCode\DomainClasses.cs 或 DomainRelationships.cs 隨即開啟。 在反白顯示的方法呼叫上方，批註會提示您提供 Get*YourProperty*（）的執行。

    > [!NOTE]
    > 這個檔案是從 Dsldefinition.dsl 檔產生的。 如果您編輯此檔案，下次按一下 [**轉換所有範本**] 時，您的變更將會遺失。 相反地，請在個別的檔案中新增必要的方法。

6. 在個別的資料夾中建立或開啟類別檔案，例如 CustomCode \\*YourDomainClass*。

     請確定命名空間與產生的程式碼中的相同。

7. 在類別檔案中，撰寫網域類別的部分執行。 在類別中，針對遺漏的 `Get` 方法撰寫定義，類似于下列範例：

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. 如果您將 [**類型**] 設定為 [**自訂存放裝置**]，您也必須提供 `Set` 方法。 例如:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     當 `Store.InUndoRedoOrRollback` 為 true 時，您的程式碼不應設定存放區中的值。 請參閱[交易和自訂 setter](#setters)。

9. 建置並執行方案。

10. 測試屬性。 請確定您嘗試 [**復原**] 和 [**重做**]。

## <a name="setters"></a>交易和自訂 Setter
 在自訂儲存區屬性的 Set 方法中，您不需要開啟交易，因為方法通常是在使用中交易內呼叫。

 不過，如果使用者叫用 [復原] 或 [重做]，或是正在回復交易，也可能會呼叫 Set 方法。 當 <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> 為 true 時，Set 方法的行為應如下所示：

- 它不應該在存放區中進行變更，例如將值指派給其他網域屬性。 復原管理員將會設定其值。

- 不過，它應該會更新任何外部資源，例如資料庫或檔案內容，或存放區外的物件。 這會確保它們會保留在 synchronism 中，並具有存放區中的值。

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

 如需交易的詳細資訊，請參閱[在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

## <a name="see-also"></a>請參閱
 [導覽和更新](../modeling/navigating-and-updating-a-model-in-program-code.md)[網域屬性之](../modeling/properties-of-domain-properties.md)程式碼屬性中的模型[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
