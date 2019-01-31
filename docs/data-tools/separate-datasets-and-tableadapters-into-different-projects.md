---
title: 將資料集和 TableAdapter 分成不同的專案
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: f5d3386cd6a379a1d38c40f97f3a9c4ef93e293d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947630"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>將資料集和 TableAdapter 分成不同的專案
具類型資料集已經過加強，以便[TableAdapters](create-and-configure-tableadapters.md)和資料集類別產生為不同的專案。 這可讓您快速分隔應用程式層，並產生多層式架構資料應用程式。

下列程序描述使用的程序**Dataset 設計工具**至包含產生的 TableAdapter 程式碼的專案不同的專案中產生資料集的程式碼。

## <a name="separate-datasets-and-tableadapters"></a>不同的資料集和 Tableadapter
當您將資料集的程式碼分開 TableAdapter 的程式碼時，包含資料集程式碼的專案必須位於目前的方案。 如果這個專案不位於目前的方案，其無法在**資料集 Project**清單中**屬性**視窗。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>將資料集分成不同的專案

1.  開啟的方案，包含資料集 (*.xsd*檔案)。

    > [!NOTE]
    >  如果方案不包含您要區隔您的資料集程式碼的專案，建立專案，或將現有的專案加入方案。

2.  按兩下具類型資料集檔案 ( *.xsd*檔案) 中**方案總管**若要開啟中的資料集**Dataset 設計工具**。

3.  選取的空白區域**Dataset 設計工具**。

4.  在 [**屬性**] 視窗中，找出**資料集 Project**節點。

5.  在 **資料集 Project**清單中，選取您要在其中產生資料集的程式碼專案的名稱。

     選取您要產生資料集程式碼的專案之後**資料集檔案**屬性會填入預設的檔案名稱。 如有必要，您可以變更此名稱。 此外，如果您想要產生資料集的程式碼至特定的目錄，您可以設定**專案資料夾**的資料夾名稱的屬性。

    > [!NOTE]
    >  當您分隔資料集和 Tableadapter (藉由設定**資料集 Project**屬性)，將不會自動移動專案中的現有部份資料集類別。 現有的部分資料集類別必須手動將移至資料集專案。

6.  儲存的資料集。

     資料集程式碼會產生中選取的專案**資料集專案**屬性，而**TableAdapter**到目前的專案產生程式碼。

根據預設，您可將資料集和 TableAdapter 程式碼之後, 的結果會是離散的類別檔案中的每個專案。 原始的專案具有名為的檔案*DatasetName.Designer.vb* (或*DatasetName.Designer.cs*) 包含 TableAdapter 的程式碼。 專案中指定**資料集 Project**屬性具有名為的檔案*DatasetName.DataSet.Designer.vb* (或*DatasetName.DataSet.Designer.cs*)，包含資料集程式碼。

> [!NOTE]
>  若要檢視產生的類別檔案，請選取資料集的 TableAdapter 專案。 然後，在**方案總管**，選取**顯示所有檔案**。

## <a name="see-also"></a>另請參閱

- [多層式架構 (N-Tier) 資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)
- [逐步解說：建立多層式架構 (N-Tier) 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [階層式更新](../data-tools/hierarchical-update.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)