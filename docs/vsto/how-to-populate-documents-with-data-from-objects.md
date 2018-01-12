---
title: "如何： 從物件的資料填入文件 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 02f2b735ceb473f7ffe55345c1cd45dc084edb80
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>如何：將物件的資料填入文件
  在 Microsoft Office Word 文件層級專案中使用資料物件存取資料時，其運作方式與在 Windows Form 專案中的運作方式相同。 您可以使用相同的工具和程式碼，將資料從物件帶入方案中，也可以使用 Windows Form 控制項顯示資料。 此外，也可以使用主控制項來顯示資料。 主控制項是 Microsoft Office Word 中的原生物件，已使用事件和資料繫結功能強化。 如需詳細資訊，請參閱 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 您必須先完成三個基本步驟，才能將物件的資料填入文件：  
  
-   將控制項加入可繫結到資料的文件。  
  
-   將資料物件加入文件。  
  
-   將資料物件連接至 BindingSource。   
  
## <a name="adding-a-data-object"></a>加入資料物件  
  
#### <a name="to-add-a-data-object"></a>若要加入資料物件  
  
-   開啟 [資料來源]  視窗，並從物件建立資料來源。 如需詳細資訊，請參閱[新增資料來源](/visualstudio/data-tools/add-new-data-sources)。  
  
## <a name="connecting-the-data-object-to-the-bindingsource"></a>將資料物件連接至 BindingSource  
 在文件層級專案中，您可以在設計階段將控制項加入文件，並將控制項繫結至資料。  
  
 在 VSTO 增益集專案中，您可以在執行階段建立並繫結控制項。  
  
### <a name="document-level-projects"></a>文件層級專案  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>若要將資料物件連接至 BindingSource  
  
1.  將想要的資料欄位從 [資料來源]  視窗拖曳至您的文件。 這樣會自動建立控制項。  
  
2.  在程式碼中，針對您為資料來源所選取的物件類型，建立執行個體。  
  
3.  將該執行個體指派給 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 的 <xref:System.Windows.Forms.BindingSource>屬性。  
  
### <a name="application-level-projects"></a>應用程式層級專案  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>若要將資料物件連接至 BindingSource  
  
1.  在程式碼中，針對與資料來源相關聯的物件類型，建立執行個體。  
  
2.  建立 <xref:System.Windows.Forms.BindingSource>的執行個體。  
  
3.  將該資料來源執行個體指派給 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 的 <xref:System.Windows.Forms.BindingSource>屬性。  
  
4.  將資料來源做為資料繫結加入控制項中。  
  
## <a name="see-also"></a>請參閱  
 
 [加入新的資料來源](/visualstudio/data-tools/add-new-data-sources)   
 [Windows Form 控制項繫結至 Visual Stduio 中的資料](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)
 
 [如何： 從資料庫的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何： 從主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [連接到 Windows Form 應用程式中的資料](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource 元件概觀](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  