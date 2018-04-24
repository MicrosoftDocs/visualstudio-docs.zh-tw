---
title: 從資料庫繫結控制項至圖片
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 722eb290e9018ef92608c8d554a371c94ba63caa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="bind-controls-to-pictures-from-a-database"></a>從資料庫繫結控制項至圖片

您可以使用**資料來源**視窗來將資料庫中的映像繫結至您的應用程式中的控制項。 比方說，您可以繫結至影像<xref:System.Windows.Controls.Image>控制在 WPF 應用程式，或為<xref:System.Windows.Forms.PictureBox>Windows Forms 應用程式中的控制項。

資料庫中的圖片，通常會儲存為位元組陣列。 中的項目**資料來源**儲存為位元組陣列有輸入其控制項的視窗設定為**無**根據預設，由於位元組陣列可能包含簡單的可執行檔的位元組陣列中的任何項目大型的應用程式。 若要建立資料繫結控制項中的位元組陣列項目的**資料來源**表示影像的視窗中，您必須選取要建立的控制項。

下列程序假設**資料來源**視窗已經填入繫結至您的映像中的項目。

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>若要將資料庫中的圖片繫結至控制項

1.  請確定您想要將控制項加入設計介面是在 WPF 設計工具或 Windows Form 設計工具中開啟。

2.  在**資料來源**視窗中，展開所需的資料表，或要顯示其資料行或屬性的物件。

3.  選取的資料行或屬性，其中包含影像資料，並從它的下拉式清單控制項清單中選取下列控制項的其中一個：

    -   如果 WPF 設計工具開啟，請選取**映像**。

    -   如果開啟 Windows Form 設計工具，請選取**PictureBox**。

    -   或者，您可以選取不同的控制項可支援資料繫結，並且可以顯示的影像。 如果您想要使用的控制項不在可用的控制項清單中，您可以將其加入清單並加以選取。 如需詳細資訊，請參閱[將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)