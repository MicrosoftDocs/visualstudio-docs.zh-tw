---
title: 具型別與具型別
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 32bbbe0aef325ee3866ec441404e30ec9f182b38
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922319"
---
# <a name="typed-vs-untyped-datasets"></a>具型別與具型別
具類型資料集是第一次衍生自基底的資料集<xref:System.Data.DataSet>類別，並接著會使用從資訊**Dataset 設計工具**，其會儲存於.xsd 檔案，以產生新的強類型 dataset 類別。 從結構描述 （資料表、 資料行，等等） 的資訊會產生，並編譯成這個新的資料集類別，當做第一級物件和屬性的一組。 因為具類型資料集繼承自基底<xref:System.Data.DataSet>類別，型別的類別假設所有的功能<xref:System.Data.DataSet>類別，並可以搭配這些方法會採用的執行個體<xref:System.Data.DataSet>類別做為參數。

 是不具類型的資料集，相較之下，已沒有相對應的內建結構描述。 具類型的資料集，與不具類型的資料集包含資料表、 資料行，等等，但僅做為集合所公開。 (不過，您手動建立的資料表和其他資料元素中不具類型的資料集之後，您可以匯出資料集的結構為結構描述使用的資料集<xref:System.Data.DataSet.WriteXmlSchema%2A>方法。)

## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>對照在具類型和不具類型資料集中的資料存取
 具類型資料集的類別具有物件模型中的屬性會採用資料表和資料行的實際名稱。 例如，如果您使用具類型資料集，您可以使用如下所示的程式碼參考的資料行：

 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

 相反地，如果您正在使用不具類型的資料集，是對等的程式碼：

 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

 具類型的存取不只容易閱讀，但也完全支援中的 IntelliSense [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **程式碼編輯器**。 除了容易使用，具類型資料集的語法會提供類型檢查在編譯時期，大幅減少指派值給資料集成員的錯誤的可能性。 如果您變更中的資料行名稱您<xref:System.Data.DataSet>類別，然後編譯您的應用程式，您會收到建置錯誤。 按兩下的建置錯誤**工作清單**，您可以直接移至程式碼行，參考舊的資料行名稱。 存取資料表和資料行中具類型資料集仍在執行階段稍微快一些，因為存取由決定在編譯時期，不是透過在執行階段集合。

 即使具類型資料集有許多優點，不具類型的資料集是在許多情況下很有用。 最明顯的案例時，會提供資料集沒有結構描述。 這可能會發生，例如，如果您的應用程式互動的元件傳回的資料集，但您不知道事先其結構為何。 同樣地，但有些的時候，當您使用沒有靜態、 可預測結構的資料。 在此情況下，很適合使用具類型的資料集，因為您必須重新產生具類型資料集類別與資料結構中的每個變更。

 較常見地，有許多次時您可能會以動態方式建立資料集，而不需要提供的結構描述。 在此情況下，資料集都是只是一個便利的結構，您可以在其中保留的詳細資訊，只要資料可以代表關聯的方式。 同時，您可以利用資料集的功能，例如序列化資訊將傳遞給另一個處理序，或以寫出 XML 檔案的能力。

## <a name="see-also"></a>另請參閱

- [資料集工具](../data-tools/dataset-tools-in-visual-studio.md)