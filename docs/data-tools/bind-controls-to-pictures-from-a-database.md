---
title: 從資料庫將控制項繫結至圖片
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d93ca95a67bc3816d8d65a799282dc6c7969e093
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304908"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>從資料庫將控制項繫結至圖片

您可以使用**Zdroje dat**視窗，以在資料庫中的影像繫結至您的應用程式中的控制項。 比方說，您可以繫結至映像<xref:System.Windows.Controls.Image>控制 WPF 應用程式中，或為<xref:System.Windows.Forms.PictureBox>Windows Forms 應用程式中的控制項。

在資料庫中的圖片，通常會儲存為位元組陣列。 中的項目**資料來源**會儲存為位元組陣列有輸入其控制項的視窗設**無**預設情況下，因為位元組陣列可以包含簡單的可執行檔的位元組陣列中的任何項目大型的應用程式。 若要建立資料繫結控制項中的位元組陣列項目的**Zdroje dat**代表影像的視窗中，您必須選取要建立的控制項。

下列程序假設**Zdroje dat**視窗已填入項目繫結至您的映像。

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>在資料庫中將圖片繫結至控制項

1.  請確定您想要將控制項加入設計介面是在 WPF 設計工具或 Windows Form 設計工具中開啟。

2.  在 [ **Zdroje dat** ] 視窗中，展開所需的資料表，或要顯示其資料行或屬性的物件。

   > [!TIP]
   > 如果**資料來源** 視窗未開啟，請開啟所選取**檢視** > **其他 Windows** > **Zdroje dat**.

3.  選取的資料行或屬性，其中包含影像資料，並從下拉式清單控制項清單中選取其中一個下列控制項：

    - 如果 WPF 設計工具開啟，請選取**映像**。

    - 如果開啟 Windows Form 設計工具，請選取**PictureBox**。

    - 或者，您可以選取不同的控制項可支援資料繫結，並且可以顯示映像。 如果您想要使用的控制項不在可用的控制項清單中，您可以將它新增至清單，，然後選取它。 如需詳細資訊，請參閱 <<c0> [ 將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)