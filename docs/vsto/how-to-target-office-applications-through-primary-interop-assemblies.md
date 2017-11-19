---
title: "如何： 透過主要 Interop 組件的 Office 應用程式為目標 |Microsoft 文件"
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
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
ms.assetid: 9bedae85-32b6-4df6-82b2-9d124fb49636
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9a96ec16afda8823ddf9918340498e29efdff2f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Assembly Binding Redirection
  當您建立新的 Office 專案時，Visual Studio 會自動將參考加入建置專案所需的 Microsoft Office 主要 Interop 組件 (PIA)。 在下列情節中，您必須將參考加入其他 PIA：  
  
-   您想使用專案中其他 Microsoft Office 應用程式的功能。 例如，您想將專案中的 Microsoft Office Excel 功能用於 Microsoft Office Word。  
  
-   您想在 Visual Studio 中自動化沒有專用專案的 Microsoft Office 應用程式 (例如 Microsoft Office Access)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>加入主要 Interop 組件的參考  
  
1.  開啟您的 Office 專案，然後選取中的專案名稱**方案總管 中**。  
  
2.  在 [專案] 功能表上，按一下 [新增參考]。  
  
3.  在**Framework**索引標籤上，選取您想在的 PIA**元件名稱**清單。 如需可用 Microsoft Office 主要 interop 組件的詳細資訊，請參閱[Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
     如果專案的目標[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更新版本，**內嵌 Interop 類型**組件參考的屬性設定為**True**預設。 藉由使用這個項目，方案就不要求使用者電腦上須有 PIA。 如需詳細資訊，請參閱 [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md)。  
  
    > [!NOTE]  
    >  Office 專案中，一律加入 Office Pia 的參考使用**.NET**  索引標籤**加入參考**對話方塊而非**COM**  索引標籤。如需詳細資訊，請參閱 [Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
4.  按一下 [確定]。  
  
     組件名稱會出現在**參考**資料夾**方案總管 中**。  
  
## <a name="see-also"></a>另請參閱  
 [Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)   
 [開發 Office 方案](../vsto/developing-office-solutions.md)   
 [如何：安裝 Office 主要 Interop 組件](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  