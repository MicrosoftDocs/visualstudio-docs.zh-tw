---
title: 設定要從資料來源視窗拖曳時要建立的控制項 |Microsoft Docs
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
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 14803b84e8695839b05726b3cadd3f2150079946
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943419"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>設定從 [資料來源] 視窗拖曳時要建立的控制項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
您可以建立資料繫結控制項項目從**Zdroje dat**視窗拖曳至 WPF 設計工具或 Windows Form 設計工具。 在每個項目**Zdroje dat**視窗已將它拖曳至設計工具時，會建立一個預設控制項。 不過，您可以選擇建立不同的控制項。  
  
## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>設定要為資料表或物件建立的控制項  
 您拖曳項目，表示資料的資料表或物件之前**Zdroje dat**  視窗中，您可以選擇一個控制項，顯示所有資料，或都顯示個別控制項中的每個資料行或屬性。  
  
 在此情況下，詞彙*物件*指的是自訂商務物件、 實體 （在 Entity Data Model) 或服務所傳回的物件。  
  
#### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>若要設定要針對資料表或物件來建立控制項  
  
1. 請確定 WPF 設計工具] 或 [Windows Form 設計工具已開啟。  
  
2. 在 [ **Zdroje dat** ] 視窗中，選取表示資料表的項目，或您要設定物件。  
  
3. 按一下 項目，下拉式功能表，然後按一下其中一個功能表中的下列項目：  
  
   - 若要在個別控制項中顯示每個資料欄位，請按一下**詳細資料**。 當您將資料的項目拖曳至設計工具時，這個動作會建立不同的資料繫結控制項，每個資料行或屬性的父資料表或物件，以及每個控制項的標籤。  
  
   - 若要顯示的所有資料的單一控制項，選取不同的控制項清單中，例如**DataGrid**或是**清單**WPF 應用程式中，或**DataGridView** Windows Form 中應用程式。  
  
     可用的控制項清單取決於哪一個設計工具上已開啟，.NET Framework 版本做為專案目標，以及是否您已新增自訂控制項的支援資料繫結至**工具箱**。 如果您想要建立的控制項是可用的控制項清單中，您可以將控制項加入清單。 如需詳細資訊，請參閱 <<c0> [ 將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
     若要了解如何建立自訂的 Windows Form 控制項加入至控制項中資料的資料表或物件的清單**資料來源** 視窗中，請參閱[建立支援複雜資料的 Windows Forms 使用者控制項繫結](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。  
  
## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>設定為資料行或屬性建立的控制項  
 您拖曳項目，表示資料行或從物件的屬性之前**Zdroje dat**至設計工具 視窗中的，您可以設定要建立的控制項。  
  
#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>若要設定為資料行或屬性建立的控制項  
  
1.  請確定 WPF 設計工具] 或 [Windows Form 設計工具已開啟。  
  
2.  在 [ **Zdroje dat** ] 視窗中，展開所需的資料表，或要顯示其資料行或屬性的物件。  
  
3.  選取您要將控制項設為建立每個資料行或屬性。  
  
4.  按一下 資料行或屬性的下拉式選單，然後選取您想要建立項目拖曳至設計工具時的控制項。  
  
     可用的控制項清單取決於哪一個設計工具上已開啟，.NET Framework 版本做為專案目標，以及哪些自訂控制項資料繫結，您已加入該支援**工具箱**。 如果您想要建立的控制項是可用的控制項清單中，您可以將控制項加入清單。 如需詳細資訊，請參閱 <<c0> [ 將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
     若要了解如何建立自訂控制項，可以加入的資料行或屬性中的控制項清單**資料來源** 視窗中，請參閱[建立支援簡單資料繫結WindowsForm使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     如果您不想要建立資料行或屬性的控制項，選取**無**下拉式選單中。 如果您想要將父資料表或物件拖曳至設計工具中，但不是想包含的特定資料行或屬性，這非常有用。  
  
## <a name="see-also"></a>另請參閱  
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
