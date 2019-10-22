---
title: 將控制項系結至資料庫中的圖片 |Microsoft Docs
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
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b8f6ee192399c8af8a508b2f9c2817db954bb36
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673006"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>從資料庫將控制項繫結至圖片
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 [**資料來源**] 視窗，將資料庫中的影像系結至應用程式中的控制項。 例如，您可以將影像系結至 WPF 應用程式中的 <xref:System.Windows.Controls.Image> 控制項，或系結至 Windows Forms 應用程式中的 <xref:System.Windows.Forms.PictureBox> 控制項。

 資料庫中的圖片通常會儲存為位元組陣列。 [**資料來源**] 視窗中儲存為位元組陣列的專案預設會將其控制項類型設定為 [**無**]，因為位元組陣列可以包含來自簡單位元組陣列的任何內容到大型應用程式的可執行檔。 若要在代表影像的 [**資料來源**] 視窗中建立位元組陣列專案的資料繫結控制項，您必須選取要建立的控制項。

 下列程式假設 [**資料來源**] 視窗已填入系結至您影像的專案。

## <a name="bind-a-picture-in-a-database-to-a-control"></a>將資料庫中的圖片系結至控制項

1. 請確定您要加入控制項的設計介面已在 WPF 設計工具或 Windows Form 設計工具中開啟。

2. 在 [**資料來源**] 視窗中，展開所需的資料表或物件，以顯示其資料行或屬性。

3. 選取包含影像資料的資料行或屬性，然後從下拉式控制項清單中選取下列其中一個控制項：

    - 如果 WPF 設計工具已開啟，請選取 [**影像**]。

    - 如果 Windows Forms 設計工具已開啟，請選取 [ **PictureBox**]。

    - 或者，您可以選取支援資料系結並可顯示影像的不同控制項。 如果您要使用的控制項不在可用控制項清單中，您可以將它新增至清單，然後選取它。 如需詳細資訊，請參閱[將自訂控制項加入至 [資料來源] 視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

## <a name="see-also"></a>請參閱
 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)
