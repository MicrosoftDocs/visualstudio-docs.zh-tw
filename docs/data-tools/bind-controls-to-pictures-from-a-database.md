---
title: 從資料庫將控制項繫結至圖片
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e9093c2a2d7cec95e4fdd08ff4273ae8f8126a36
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282980"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>從資料庫將控制項繫結至圖片

您可以使用 [**資料來源**] 視窗，將資料庫中的影像系結至應用程式中的控制項。 例如，您可以將影像系結至 <xref:System.Windows.Controls.Image> WPF 應用程式中的控制項，或系結至 <xref:System.Windows.Forms.PictureBox> Windows Forms 應用程式中的控制項。

資料庫中的圖片通常會儲存為位元組陣列。 [**資料來源**] 視窗中儲存為位元組陣列的專案預設會將其控制項類型設定為 [**無**]，因為位元組陣列可以包含來自簡單位元組陣列的任何內容到大型應用程式的可執行檔。 若要在代表影像的 [**資料來源**] 視窗中建立位元組陣列專案的資料繫結控制項，您必須選取要建立的控制項。

下列程式假設 [**資料來源**] 視窗已填入系結至您影像的專案。

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>若要將資料庫中的圖片系結至控制項

1. 請確定您要加入控制項的設計介面已在 WPF 設計工具或 Windows Form 設計工具中開啟。

2. 在 [**資料來源**] 視窗中，展開所需的資料表或物件，以顯示其資料行或屬性。

   > [!TIP]
   > 如果 [**資料來源**] 視窗未開啟，請選取 [**視圖**] [  >  **其他視窗**] [  >  **資料來源**] 加以開啟。

3. 選取包含影像資料的資料行或屬性，然後從下拉式控制項清單中選取下列其中一個控制項：

    - 如果 WPF 設計工具已開啟，請選取 [**影像**]。

    - 如果 Windows Forms 設計工具已開啟，請選取 [ **PictureBox**]。

    - 或者，您可以選取支援資料系結並可顯示影像的不同控制項。 如果您要使用的控制項不在可用控制項清單中，您可以將它新增至清單，然後選取它。 如需詳細資訊，請參閱[將自訂控制項加入至 [資料來源] 視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
