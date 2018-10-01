---
title: 自訂繫結 對話方塊的控制項 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datauicustomization
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Customize Control Binding dialog box
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4d47fe3962651db91dcfdf6e59653db539a9f44b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490320"
---
# <a name="customize-control-binding-dialog-box"></a>自訂控制項繫結對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用**自訂控制項繫結**對話方塊中指定的項目中可以使用哪些控制項[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)。  
  
 在每個項目**Zdroje dat**視窗具有相關聯的控制項可繫結至項目清單。 適用於每個項目控制項是項目的資料類型所決定。 每個資料類型有一份有效的關聯控制項定義在這個對話方塊中，包含預設控制項。  
  
 您將項目拖曳至設計介面，以建立資料繫結控制項之前，您可以選取要建立的控制項。 如果您拖曳的項目**Zdroje dat**視窗拖曳至設計介面，而不需選取項目的資料型別都會加入至設計介面，選取控制項時，預設的控制項。  
  
 如需有關如何使用這個對話方塊中，以自訂的控制項中的項目清單**資料來源** 視窗中，請參閱[將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **資料類型**  
 會顯示一份與控制項相關聯的類型：  
  
-   資料表、 實體和物件會表示為 **[清單]** 型別。  
  
-   實體和物件的公用屬性或資料行被以實際的資料類型之資料行的基礎資料存放區中的屬性。  
  
-   具有使用者定義的圖形物件會表示為 **[其他]**。 比方說，如果您的應用程式的自訂控制項，會顯示物件的多個屬性的資料，請選取 **[其他]** 控制項的資料類型。  
  
 **相關聯的控制項**  
 會顯示一份您可以建立特定的資料類型與關聯的控制項。 如果您想要在選取的資料類型相關聯的特定控制項**資料型別**清單中，選取對應的核取方塊。 清除核取方塊，若要移除的關聯。 檢查所顯示的捷徑功能表中會出現控制項**Zdroje dat**視窗相關聯的資料型別的項目。  
  
 您可以將控制項加入清單加上有數個資料繫結屬性的控制項**工具箱**。 如需詳細資訊，請參閱 <<c0> [ 將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
 **設為預設值**  
 將選取的控制項類型的預設值為選取的資料類型的項目。 預設控制項會顯示中所顯示的捷徑功能表的第一個選項**Zdroje dat**視窗中的項目。 只有一種控制項類型可指派為資料類型的預設值。  
  
 **清除預設值**  
 移除選取的資料類型的預設值為控制項指定。 如果沒有針對選取的資料類型，沒有預設值 **[無]** 中所顯示的捷徑功能表的第一個選項會出現**Zdroje dat**視窗相關聯的類型項目。  
  
## <a name="see-also"></a>另請參閱  
 [資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [加入新的資料來源](../data-tools/add-new-data-sources.md)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)