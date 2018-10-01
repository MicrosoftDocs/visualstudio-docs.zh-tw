---
title: 將自訂控制項加入至資料來源視窗 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: acdab62754a8cbbe7b97ea9723fba202d5078ac0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491895"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>將自訂控制項加入 [資料來源] 視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[將自訂控制項加入至資料來源視窗](https://docs.microsoft.com/visualstudio/data-tools/add-custom-controls-to-the-data-sources-window)。  
  
  
當您拖曳的項目**Zdroje dat**至設計介面，以建立資料繫結控制項的視窗，您可以選取您所建立的控制項型別。 在視窗中的每個項目具有會顯示您可以選擇從控制項下拉式清單。 一組控制項與每個項目相關聯取決於項目的資料型別。 如果您想要建立的控制項不會出現在清單中，您可以遵循本主題中的指示，將控制項加入至清單。  
  
 如需有關選取的項目中建立的資料繫結控制項**資料來源** 視窗中，請參閱[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
> [!NOTE]
>  根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更您的設定，在**工具**功能表上，選取**匯入和匯出設定**。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
##  <a name="customizinglist"></a> 自訂資料類型的可繫結控制項的清單  
 若要新增或移除的項目中的可用控制項清單中的控制項**Zdroje dat**有特定的資料類型，執行下列步驟的視窗。  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>若要選取要列出的資料類型的控制項  
  
1.  請確定 WPF 設計工具] 或 [Windows Form 設計工具已開啟。  
  
2.  在 [ **Zdroje dat** ] 視窗中，按一下您新增至] 視窗中，資料來源的一部分的項目，然後按一下 [下拉式選單，項目。  
  
3.  在下拉式功能表中，按一下**自訂**。 其中一個下列對話方塊隨即開啟：  
  
    -   如果 Windows Form 設計工具開啟，請**自訂資料欄位 UI**頁**選項**對話方塊隨即開啟。  
  
    -   如果 WPF 設計工具開啟，請**自訂控制項繫結**對話方塊隨即開啟。  
  
4.  在對話方塊中，選取 將資料類型從**資料型別**下拉式清單。  
  
    -   若要自訂的資料表或物件的控制項清單，請選取 **[清單]**。  
  
    -   若要自訂控制項的資料行的資料表或物件的屬性清單，選取 基礎資料存放區中的資料行或屬性的資料類型。  
  
    -   若要自訂控制項以顯示具有使用者定義的圖形資料物件的清單，請選取 **[其他]**。 例如，選取 **[其他]** 如果應用程式的自訂控制項以顯示來自多個屬性的特定物件的資料。  
  
5.  在 **關聯的控制項**方塊中，選取您想要選取的資料類型，可用的每個控制項或清除任何您想要從清單中移除的控制項。  
  
    > [!NOTE]
    >  如果您想要選取的控制項不會不出現在**關聯的控制項** 方塊中，您必須將控制項新增至清單。 如需詳細資訊，請參閱 < [Adding Controls to 清單相關聯控制項的資料型別的](#addingcontrols)。  
  
6.  按一下 [確定 **Deploying Office Solutions**]。  
  
7.  在  **Zdroje dat**視窗中，按一下資料的項目類型只是關聯一或多個控制項，然後按一下 下拉式選單，項目。  
  
     您在選取的控制項**關聯的控制項**方塊現在會出現在下拉式清單功能表中的項目。  
  
##  <a name="addingcontrols"></a> Addcontrols 至相關聯的控制項，資料類型的清單  
 如果您想要控制項相關聯的資料類型，但不會顯示控制項，這是在**關聯的控制項** 方塊中，您必須將控制項新增至清單。 控制項必須位於目前的方案中，或參考的組件。 它也必須提供**工具箱**，且具有指定控制項的資料繫結行為的屬性。  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>將控制項加入至關聯控制項的清單  
  
1.  將所需的控制項加入**工具箱**以滑鼠右鍵按一下**工具箱**，然後選取**選擇項目**。  
  
     控制項必須具有下列屬性的其中之一。  
  
    |屬性|描述|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|實作簡單的控制項顯示資料，單一資料行 （或屬性） 的這個屬性，例如<xref:System.Windows.Forms.TextBox>。|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|實作這個屬性的控制項上，顯示清單 （或資料表） 的資料，例如<xref:System.Windows.Forms.DataGridView>。|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|實作這個屬性的控制項上，顯示清單 （或資料表） 的資料，但是也需要呈現單一資料行或屬性，例如<xref:System.Windows.Forms.ComboBox>。|  
  
2.  Windows form 上**選項**對話方塊中，開啟**自訂資料欄位 UI**頁面。 或者，您也可以針對 WPF 中，開啟**自訂控制項繫結** 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 自訂資料類型的清單可繫結控制項的](#customizinglist)。  
  
3.  在 **關聯的控制項**方塊中，您剛加入至控制項**工具箱**現在應該會出現。  
  
    > [!NOTE]
    >  位在目前方案中，或是參考的組件中的控制項才可以加入至相關聯控制項的清單。 （控制項也必須實作其中一個資料繫結屬性上表中。）若要將資料繫結至自訂控制項，不適用於**資料來源** 視窗中，將控制項從**工具箱**放至設計介面，然後拖曳的項目繫結至從**資料來源**視窗拖曳至控制項。  
  
## <a name="see-also"></a>另請參閱  
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)

