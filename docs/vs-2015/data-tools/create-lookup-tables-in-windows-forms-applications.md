---
title: 在 Windows Forms 應用程式中建立查閱資料表 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3979d08757445e9df5fc159fe7642b04bf74b995
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72630927"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>在 Windows Forms 應用程式中建立查閱資料表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

「詞彙*查閱」資料表*描述系結至兩個相關資料表的控制項。 這些查閱控制項會根據第二個數據表中選取的值，顯示第一個資料表中的資料。

 將父資料表的主要節點（從 [[資料來源] 視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)）拖曳至表單上已系結至相關子資料工作表中之資料行的控制項，即可建立查閱資料表。

 例如，假設 sales 資料庫中的 `Orders` 資料表。 @No__t_0 資料表中的每筆記錄都包含 `CustomerID`，以指出哪個客戶下訂單。 @No__t_0 是指向 `Customers` 資料表中客戶記錄的外鍵。 在此案例中，您會展開 [**資料來源**] 視窗中的 [`Orders`] 資料表，並將主要節點設定為 [**詳細**資料]。 然後將 [`CustomerID`] 資料行設定為使用 <xref:System.Windows.Forms.ComboBox> （或支援查閱系結的任何其他控制項），然後將 [`Orders`] 節點拖曳至表單上。 最後，將 [`Customers`] 節點拖曳至系結至相關資料行的控制項，在此案例中，<xref:System.Windows.Forms.ComboBox> 系結至 `CustomerID` 資料行。

## <a name="to-databind-a-lookup-control"></a>若要將查閱控制項進行 databind

1. 開啟 [資料來源] 視窗。

    > [!NOTE]
    > 在 [**資料來源**] 視窗中，查閱資料表需要有兩個相關的資料表或物件。

2. 展開 [**資料來源**] 視窗中的節點，直到您可以看到父資料表及其所有資料行，以及相關的子資料工作表及其所有資料行為止。

    > [!NOTE]
    > 子資料工作表節點是在父資料表中顯示為可擴充子節點的節點。

3. 從子資料工作表節點的控制項清單中選取 [**詳細資料**]，將子資料工作表的卸載類型變更為 [**詳細資料**]。 如需詳細資訊，請參閱[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

4. 找出與兩個數據表相關聯的節點（上一個範例中的 `CustomerID` 節點）。從控制項清單中選取 [ **ComboBox** ]，將其卸載類型變更為 [<xref:System.Windows.Forms.ComboBox>]。

5. 將 [主要子資料工作表] 節點從 [**資料來源**] 視窗拖曳至表單上。

     資料系結控制項（具有描述性標籤）和工具區域（<xref:System.Windows.Forms.BindingNavigator>）會出現在表單上。 [資料集](../data-tools/dataset-tools-in-visual-studio.md)、TableAdapter、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator> 會出現在元件匣中。

6. 現在將 [主要父資料表] 節點從 [**資料來源**] 視窗直接拖曳至查閱控制項（<xref:System.Windows.Forms.ComboBox>）。

     現在已建立查閱系結。 請參閱下表，以取得在控制項上設定的特定屬性。

    |屬性|設定說明|
    |--------------|----------------------------|
    |**DataSource**|Visual Studio 會將此屬性設定為針對您拖曳至控制項之資料表所建立的 <xref:System.Windows.Forms.BindingSource> (與建立控制項時所建立的 <xref:System.Windows.Forms.BindingSource> 相反)。<br /><br /> 如果您需要進行調整，請將此設定為包含您要顯示之資料行的資料表 <xref:System.Windows.Forms.BindingSource>。|
    |**DisplayMember**|Visual Studio 會將此屬性設定為主索引鍵後面具有字串資料類型的第一個資料行 (針對您拖曳至控制項的資料表)。<br /><br /> 如果您需要進行調整，請將此設為您想要顯示的資料行名稱。|
    |**ValueMember**|Visual Studio 會將此屬性設定為參與主索引鍵的第一個資料行，或者，如果未定義索引鍵，則為資料表中的第一個資料行。<br /><br /> 如果您需要進行調整，請將此設定為包含您要顯示之資料行之資料表中的主鍵。|
    |**SelectedValue**|Visual Studio 將此屬性設定為從 [**資料來源**] 視窗中卸載的原始資料行。<br /><br /> 如果您需要進行調整，請將此設定為相關資料表中的外鍵資料行。|

## <a name="see-also"></a>另請參閱
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
