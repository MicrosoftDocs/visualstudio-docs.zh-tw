---
title: 將控制項繫結至圖片從資料庫 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7c2dce31d5d2d2564c4a277b479dbf1e463b4632
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666127"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>從資料庫將控制項繫結至圖片
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用**Zdroje dat**視窗，以在資料庫中的影像繫結至您的應用程式中的控制項。 比方說，您可以繫結至映像<xref:System.Windows.Controls.Image>控制 WPF 應用程式中，或為<xref:System.Windows.Forms.PictureBox>Windows Forms 應用程式中的控制項。  
  
 在資料庫中的圖片，通常會儲存為位元組陣列。 中的項目**資料來源**會儲存為位元組陣列有輸入其控制項的視窗設**無**預設情況下，因為位元組陣列可以包含簡單的可執行檔的位元組陣列中的任何項目大型的應用程式。 若要建立資料繫結控制項中的位元組陣列項目的**Zdroje dat**代表影像的視窗中，您必須選取要建立的控制項。  
  
 下列程序假設**Zdroje dat**視窗已填入項目繫結至您的映像。
  
## <a name="bind-a-picture-in-a-database-to-a-control"></a>將資料庫中的圖片繫結至控制項  
  
1.  請確定您想要將控制項加入設計介面是在 WPF 設計工具或 Windows Form 設計工具中開啟。  
  
2.  在 [ **Zdroje dat** ] 視窗中，展開所需的資料表，或要顯示其資料行或屬性的物件。  
  
3.  選取的資料行或屬性，其中包含影像資料，並從下拉式清單控制項清單中選取其中一個下列控制項：  
  
    -   如果 WPF 設計工具開啟，請選取**映像**。  
  
    -   如果開啟 Windows Form 設計工具，請選取**PictureBox**。  
  
    -   或者，您可以選取不同的控制項可支援資料繫結，並且可以顯示映像。 如果您想要使用的控制項不在可用的控制項清單中，您可以將它新增至清單，，然後選取它。 如需詳細資訊，請參閱 <<c0> [ 將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)
