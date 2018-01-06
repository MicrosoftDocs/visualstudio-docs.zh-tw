---
title: "設定要從資料來源視窗拖曳時建立的控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 5556a5d9a537684a8d1e73ee363b4c9ac8f6baa8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>設定從 [資料來源] 視窗拖曳時要建立的控制項
您可以建立資料繫結控制項項目從**資料來源**視窗拖曳至 WPF 設計工具或 Windows Form 設計工具。 每個項目**資料來源**視窗有時將它拖曳至設計工具所建立的預設控制項。 不過，您可以選擇建立不同的控制項。  
  
## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>設定要建立的資料表或物件的控制項  
您拖曳項目，代表資料的資料表或從物件之前**資料來源**視窗中，您可以選擇一個控制項，以顯示所有資料，或個別控制項中都顯示每個資料行或屬性。  
  
在此內容中，詞彙*物件*指的是自訂的商務物件、 實體 （以實體資料模型） 或服務所傳回的物件。  
  
### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>若要設定要針對資料表或物件建立控制項  
  
1.  請確定 WPF 設計工具] 或 [Windows Form 設計工具已開啟。  
  
2.  在**資料來源**視窗中，選取代表資料表的項目，或您想要設定的物件。  
  
3.  按一下下拉式清單項目的功能表，並按一下功能表中的下列項目：  
  
    -   若要在個別控制項中顯示每個資料欄位，請按一下**詳細資料**。 當您將資料的項目拖曳至設計工具時，此動作會建立不同的資料繫結控制項，每個資料行或屬性的父資料表或物件，以及每個控制項的標籤。  
  
    -   若要顯示的所有資料在單一的控制項中，選取不同的控制項在清單中，例如**DataGrid**或**清單**在 WPF 應用程式，或**DataGridView** Windows Form 中應用程式。  
  
    可用的控制項清單取決於哪一個設計工具上已開啟，.NET Framework 版本做為專案目標，以及是否加入自訂控制項的支援資料繫結至**工具箱**。 如果您想要建立的控制項不在可用的控制項清單中，您可以將控制項加入清單。 如需詳細資訊，請參閱[將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
    若要了解如何建立自訂的 Windows Form 控制項加入至資料的資料表或物件中的控制項清單**資料來源**視窗中，請參閱[建立支援複雜資料的 Windows Form 使用者控制項繫結](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。  
  
## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>設定要用於建立資料行或屬性的控制項  
拖曳的資料行或從物件的屬性所代表的項目之前**資料來源**至設計工具 視窗中的，您可以設定要建立控制項。  
  
#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>若要設定要用於建立資料行或屬性的控制項  
  
1.  請確定 WPF 設計工具] 或 [Windows Form 設計工具已開啟。  
  
2.  在**資料來源**視窗中，展開所需的資料表，或要顯示其資料行或屬性的物件。  
  
3.  選取您要將控制項設為建立每個資料行或屬性。  
  
4.  按一下下拉式功能表，針對資料行或屬性，然後選取您想要的項目拖曳至設計工具時建立的控制項。  
  
     可用的控制項清單取決於哪一個設計工具上已開啟，.NET Framework 版本做為專案目標，以及哪些自訂控制項的支援資料繫結，您已新增至**工具箱**。 如果您想要建立的控制項的可用控制項清單中，您可以將控制項加入清單。 如需詳細資訊，請參閱[將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
     若要了解如何建立自訂控制項加入至控制項的資料行或在屬性清單**資料來源**視窗中，請參閱[建立 Windows Form 使用者控制項支援簡單資料繫結](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     如果您不想要建立資料行或屬性的控制項，選取**無**下拉式選單中。 如果您想要將父資料表或物件拖曳至設計工具中，但您不想要包含的特定資料行或屬性，這非常有用。  
  
## <a name="see-also"></a>另請參閱
[將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)