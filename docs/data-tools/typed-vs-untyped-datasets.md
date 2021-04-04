---
title: 具類型資料集與不具類型資料集的比較
description: 瞭解具類型與不具類型資料集之間的差異。 在具類型和不具類型的資料集中進行資料存取的對比。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: daf4f722eb51a08e7a6ddb287e5b54956ecdfe73
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216016"
---
# <a name="typed-vs-untyped-datasets"></a>具類型資料集與不具類型資料集的比較
具型別資料集是第一個衍生自基類的資料集， <xref:System.Data.DataSet> 然後使用儲存在 .xsd 檔中 **DataSet 設計工具** 的資訊來產生新的強型別資料集類別。 架構 (資料表、資料行等等) 的資訊會產生並編譯成這個新的資料集類別，做為一組第一級的物件和屬性。 由於具型別資料集繼承自基類，因此具型別 <xref:System.Data.DataSet> 類別會假設類別的所有功能， <xref:System.Data.DataSet> 而且可以與採用類別實例作為參數的方法搭配使用 <xref:System.Data.DataSet> 。

相反地，不具類型的資料集沒有對應的內建架構。 如同在具型別資料集中，不具類型的資料集包含資料表、資料行等等，但這些資料集只會以集合的形式公開。 不過 (不過，在不具類型的資料集中手動建立資料表和其他資料元素之後，您可以使用資料集的方法，將資料集的結構匯出為架構 <xref:System.Data.DataSet.WriteXmlSchema%2A> 。 ) 

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>具類型與不具類型資料集的資料存取對比
具類型資料集的類別具有物件模型，其中的屬性會採用資料表和資料行的實際名稱。 例如，如果您使用具類型的資料集，您可以使用下列程式碼來參考資料行：

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet4":::

相反地，如果您使用不具類型的資料集，則對等的程式碼為：

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet5":::

具型別存取不僅容易閱讀，而且 IntelliSense 在 Visual Studio 程式 **代碼編輯器** 中也受到完整支援。 除了更容易使用之外，具型別資料集的語法也會在編譯時期提供型別檢查，大幅減少將值指派給資料整合員的可能錯誤。 如果您在類別中變更資料行的名稱， <xref:System.Data.DataSet> 然後編譯您的應用程式，則會收到組建錯誤。 按兩下 **工作清單** 中的組建錯誤，即可直接移至參考舊資料行名稱的程式程式碼或程式程式碼。 在執行時間，存取具型別資料集的資料表和資料行也會稍微快一點，因為存取是在編譯時期決定，而不是在執行時間透過集合來決定。

雖然具類型的資料集有許多優點，但不具類型的資料集在各種情況下都很有用。 最明顯的情況是，資料集沒有任何可用的架構。 例如，如果您的應用程式與傳回資料集的元件互動，但您事先不知道其結構為何，就可能發生這種情況。 同樣地，有時候您會使用沒有靜態、可預測結構的資料。 在此情況下，使用具類型的資料集並不實用，因為您必須在資料結構中的每個變更時重新產生具類型的資料集類別。

更常見的情況是，您可能會有許多時候動態建立資料集，而不需要提供架構。 在這種情況下，資料集只是一個方便的結構，您可以在其中保留資訊，只要資料可以用關聯式方式來表示。 同時，您可以利用資料集的功能，例如序列化資訊以傳遞至另一個進程，或寫出 XML 檔案的能力。

## <a name="see-also"></a>另請參閱

- [資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
