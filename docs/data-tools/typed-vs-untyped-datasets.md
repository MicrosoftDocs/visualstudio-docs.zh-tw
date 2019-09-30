---
title: 具類型資料集與不具類型資料集的比較
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1c5ae8c665c195a1a50e02afda97ec34ac163297
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252925"
---
# <a name="typed-vs-untyped-datasets"></a>具類型資料集與不具類型資料集的比較
具類型資料集是第一次衍生自基類<xref:System.Data.DataSet>的資料集，然後使用來自**DataSet 設計工具**的資訊（儲存在 .xsd 檔案中）來產生新的強型別資料集類別。 架構（資料表、資料行等等）中的資訊會產生並編譯成這個新的資料集類別，做為一組第一類物件和屬性。 因為具類型的資料集繼承自<xref:System.Data.DataSet>基類，所以具類型的類別會假設<xref:System.Data.DataSet>類別的所有功能，而且可以搭配<xref:System.Data.DataSet>接受類別實例做為參數的方法使用。

相反地，不具類型的資料集沒有對應的內建架構。 如同在具類型的資料集中，不具類型的資料集包含資料表、資料行等等，但是只會以集合的形式公開。 （不過，在不具類型的資料集中手動建立資料表和其他資料元素之後，您可以使用資料集的<xref:System.Data.DataSet.WriteXmlSchema%2A>方法，將資料集的結構匯出為架構）。

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>在具類型和不具類型的資料集中進行對比資料存取
具類型資料集的類別具有物件模型，其中的屬性會採用資料表和資料行的實際名稱。 例如，如果您使用具類型的資料集，則可以使用如下的程式碼來參考資料行：

[!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
[!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

相反地，如果您使用不具類型的資料集，則對等的程式碼為：

[!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
[!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

輸入的存取權不僅更容易閱讀，而且 IntelliSense 也會在 Visual Studio 程式**代碼編輯器**中受到完整支援。 除了更容易使用之外，具類型資料集的語法也會在編譯時期提供類型檢查，大幅降低將值指派給資料整合員時發生錯誤的可能性。 如果您在<xref:System.Data.DataSet>類別中變更資料行的名稱，然後再編譯應用程式，就會收到組建錯誤。 按兩下**工作清單**中的組建錯誤，即可直接移至參考舊資料行名稱的一行或幾行程式碼。 在執行時間，存取具類型資料集中的資料表和資料行也會稍微快速，因為存取是在編譯時期決定，而不是在執行時間透過集合。

雖然具類型的資料集有許多優點，但不具類型的資料集在各種情況下都很有用。 最明顯的情況是當資料集沒有可用的架構時。 例如，如果您的應用程式與傳回資料集的元件互動，但您事先不知道它的結構為何，就可能會發生這種情況。 同樣地，在某些情況下，您會使用沒有靜態、可預測結構的資料。 在這種情況下，使用具型別資料集並不可行，因為您必須重新產生具有資料結構中每個變更的具型別資料集類別。

更常見的情況是，您可能會很多次地建立資料集，而不需要有架構。 在此情況下，資料集只是一個方便的結構，您可以在其中保存資訊，只要資料可以關聯式方式表示即可。 同時，您可以利用資料集的功能，例如，將資訊序列化以傳遞至另一個進程，或寫出 XML 檔案的功能。

## <a name="see-also"></a>另請參閱

- [資料集工具](../data-tools/dataset-tools-in-visual-studio.md)