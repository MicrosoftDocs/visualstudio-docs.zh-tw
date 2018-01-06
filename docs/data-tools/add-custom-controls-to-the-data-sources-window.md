---
title: "將自訂控制項加入至資料來源視窗 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: ffa55100e9bbec33fdbca19ab2757c4de63f5030
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>將自訂控制項加入 [資料來源] 視窗
當您拖曳的項目**資料來源**至設計介面來建立資料繫結控制項視窗中的，您可以選取您建立的控制項類型。 在視窗中的每個項目有會顯示您可以選擇從控制項下拉式清單。 項目的資料類型所決定的每個項目相關聯的控制項集合。 如果您想要建立的控制項不會出現在清單中，您可以遵循本主題中的指示，將控制項加入至清單。  
  
 如需有關選取資料繫結控制項中的項目建立**資料來源**視窗中，請參閱[設定要從資料來源視窗拖曳時建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
> [!NOTE]
>  根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更您的設定，在**工具**功能表上，選取**匯入和匯出設定**。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
##  <a name="customizinglist"></a>自訂繫結控制項的資料類型的清單  
 若要加入或移除控制項，從可用的控制項清單中的項目**資料來源**視窗具有特定資料類型，請執行下列步驟。  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>若要選取要列出的資料類型的控制項  
  
1.  請確定 WPF 設計工具] 或 [Windows Form 設計工具已開啟。  
  
2.  在**資料來源**視窗中，按一下您新增至視窗中，資料來源的一部分的項目，然後按一下 下拉式清單項目的功能表。  
  
3.  在下拉式功能表中，按一下**自訂**。 其中一個下列對話方塊隨即開啟：  
  
    -   如果 Windows Form 設計工具開啟，請**自訂資料欄位 UI**頁面**選項**對話方塊隨即開啟。  
  
    -   如果 WPF 設計工具開啟，請**自訂控制項繫結**對話方塊隨即開啟。  
  
4.  在對話方塊中，選取 將資料類型從**資料型別**下拉式清單。  
  
    -   若要自訂控制項的資料表或物件清單，請選取**[清單]**。  
  
    -   若要自訂控制項的資料行的資料表或物件的屬性清單，選取在基礎資料存放區中的資料行或屬性的資料類型。  
  
    -   若要自訂控制項以顯示具有使用者定義的圖形資料物件的清單，請選取**[其他]**。 例如，選取**[其他]**如果您的應用程式具有自訂控制項以顯示來自多個特定物件屬性的資料。  
  
5.  在**相關聯控制項**方塊中，選取您想要選取的資料類型，可用的每個控制項或清除您想要從清單中移除任何控制項的選取項目。  
  
    > [!NOTE]
    >  如果您想要選取的控制項不會顯示在**相關聯控制項** 方塊中，您必須將控制項加入至清單。 如需詳細資訊，請參閱[將控制項加入清單的相關聯控制項的資料型別](#addingcontrols)。  
  
6.  按一下 [確定 **Deploying Office Solutions**]。  
  
7.  在**資料來源**視窗中，按一下資料的項目輸入只相關一或多個控制項，然後按一下 下拉式清單項目的功能表。  
  
     您在選取的控制項**相關聯控制項**方塊現在會出現在下拉式清單項目的功能表。  
  
##  <a name="addingcontrols"></a>將控制項加入至相關聯控制項的資料類型清單  
 如果您想要將控制項與資料型別產生關聯，但是控制項不在**相關聯控制項** 方塊中，您必須將控制項加入至清單。 控制項必須位於目前的方案中，或參考的組件。 它也必須用於**工具箱**，並具有指定控制項的資料繫結行為的屬性。  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>將控制項加入至相關聯的控制項的清單  
  
1.  將所需的控制項加入**工具箱**以滑鼠右鍵按一下**工具箱**，然後選取**選擇項目**。  
  
     控制項必須具有下列屬性。  
  
    |屬性|描述|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|實作此屬性顯示的資料，單一資料行 （或屬性） 的簡單控制項，例如<xref:System.Windows.Forms.TextBox>。|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|實作這個屬性的控制項，顯示清單 （或資料表） 的資料，例如<xref:System.Windows.Forms.DataGridView>。|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|實作這個屬性的控制項，顯示清單 （或資料表） 的資料，但是也需要呈現單一資料行或屬性，例如<xref:System.Windows.Forms.ComboBox>。|  
  
2.  Windows form 上**選項**對話方塊中，開啟**自訂資料欄位 UI**頁面。 或者，為 WPF 中，開啟**自訂控制項繫結** 對話方塊。 如需詳細資訊，請參閱[自訂資料類型的清單的可繫結控制項](#customizinglist)。  
  
3.  在**相關聯控制項**方塊中，您剛剛加入的控制項**工具箱**現在應該會出現。  
  
    > [!NOTE]
    >  只有位於目前的方案內，或參考的組件的控制項可以加入至相關聯的控制項的清單。 （控制項也必須實作其中一個資料繫結屬性上表中。）若要將資料繫結中沒有的自訂控制項**資料來源**視窗中，拖曳控制項**工具箱**拖曳至設計介面，然後拖曳的項目，從繫結至**資料來源**視窗拖曳至控制項。  
  
## <a name="see-also"></a>請參閱  
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)