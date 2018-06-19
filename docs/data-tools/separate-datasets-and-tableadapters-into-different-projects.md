---
title: 個別的資料集和 TableAdapters 分成不同的專案
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fe7d774a9a5fa1e14cdbcb9c5d730a01fdcdeee9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921441"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>個別的資料集和 TableAdapters 分成不同的專案
具類型資料集已經過加強，以便[Tableadapter](create-and-configure-tableadapters.md)和資料集類別產生為不同的專案。 這可讓您快速分隔應用程式層級，並產生多層式架構資料應用程式。

下列程序描述的程序使用**Dataset 設計工具**產生資料集的程式碼到專案中包含所產生的 TableAdapter 程式碼的專案不同。

## <a name="separate-datasets-and-tableadapters"></a>個別的資料集和 Tableadapter
當您將資料集程式碼分開 TableAdapter 的程式碼時，包含資料集程式碼的專案必須位於目前的方案。 如果目前的方案中找不到這個專案，將不會予以提供**資料集專案**清單中**屬性**視窗。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>將資料集分成不同的專案

1.  開啟包含資料集 （.xsd 檔案） 的方案。

    > [!NOTE]
    >  如果方案不包含您要劃分資料集的程式碼的專案，建立專案，或將現有的專案加入方案。

2.  按兩下具類型資料集檔案 （.xsd 檔案） 中**方案總管 中**開啟中的資料集**Dataset 設計工具**。

3.  選取的空白區域**Dataset 設計工具**。

4.  在**屬性**視窗中，找出**資料集專案**節點。

5.  在**資料集專案**清單中，選取您要產生資料集的程式碼專案的名稱。

     選取您要產生資料集程式碼的專案之後**資料集檔案**屬性會填入預設的檔案名稱。 如有必要，您可以變更此名稱。 此外，如果您想要產生資料集的程式碼至特定的目錄，您可以將**專案資料夾**屬性設為資料夾的名稱。

    > [!NOTE]
    >  當您分隔資料集與 Tableadapter 時 (藉由設定**資料集專案**屬性)，將不會自動移動專案中的現有部份資料集類別。 現有資料集部分類別必須手動移至資料集專案。

6.  儲存資料集。

     資料集程式碼便會產生至選取的專案中**資料集專案**屬性，而**TableAdapter**到目前的專案產生程式碼。

根據預設，您可將資料集和 TableAdapter 的程式碼之後, 的結果會是離散的類別檔案中的每個專案。 原始專案有檔名為 DatasetName.Designer.vb （或 DatasetName.Designer.cs） 包含 TableAdapter 的程式碼。 專案中指定的**資料集專案**屬性有檔名為 DatasetName.DataSet.Designer.vb （或 DatasetName.DataSet.Designer.cs），其中包含資料集程式碼。

> [!NOTE]
>  若要檢視產生的類別檔案，請選取資料集或 TableAdapter 專案。 然後，在**方案總管 中**，選取**顯示所有檔案**。

## <a name="see-also"></a>另請參閱

- [多層式架構 (N-Tier) 資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)
- [逐步解說：建立多層式架構 (N-Tier) 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [階層式更新](../data-tools/hierarchical-update.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)