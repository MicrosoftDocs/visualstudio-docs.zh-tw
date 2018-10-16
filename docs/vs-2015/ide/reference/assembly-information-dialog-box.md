---
title: 組件資訊對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8526dfbe970c43e1ab55534c13a1e6708b2b4693
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248023"
---
# <a name="assembly-information-dialog-box"></a>組件資訊對話方塊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
您可以使用 [組件資訊] 對話方塊來指定 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 全域組件屬性的值，該值會儲存在隨專案自動建立的 AssemblyInfo 檔案中。 在方案總管中，若是 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]，此檔案是在 [我的專案] 節點中 (按一下 [顯示所有檔案] 即可檢視)；若是 [!INCLUDE[csprcs](../../includes/csprcs-md.md)]，則是在 [屬性] 底下。 如需組件屬性的詳細資訊，請參閱[屬性](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)。  
  
 若要存取這個對話方塊，請選取方案總管中的專案節點，然後按一下 [專案] 功能表上的 [屬性]。 當 [專案設計工具] 出現時，請按一下 [應用程式] 索引標籤。在 [應用程式] 頁面上，按一下 [組件資訊] 按鈕。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **標題**  
 指定組件資訊清單的標題。 對應至 <xref:System.Reflection.AssemblyTitleAttribute>。  
  
 **描述**  
 指定組件資訊清單的選擇性描述。 對應至 <xref:System.Reflection.AssemblyDescriptionAttribute>。  
  
 **公司**  
 指定組件資訊清單的公司名稱。 對應至 <xref:System.Reflection.AssemblyCompanyAttribute>。  
  
 **產品**  
 指定組件資訊清單的產品名稱。 對應至 <xref:System.Reflection.AssemblyProductAttribute>。  
  
 **著作權**  
 指定組件資訊清單的著作權標示。 對應至 <xref:System.Reflection.AssemblyCopyrightAttribute>。  
  
 **商標**  
 指定組件資訊清單的商標。 對應至 <xref:System.Reflection.AssemblyTrademarkAttribute>。  
  
 **組件版本**  
 指定組件的版本。 對應至 <xref:System.Reflection.AssemblyVersionAttribute>。  
  
 **檔案版本**  
 指示版本號碼，以指示編譯器使用 Win32 檔案版本資源的特定版本。 對應至 <xref:System.Reflection.AssemblyFileVersionAttribute>。  
  
 **GUID**  
 識別組件的唯一 GUID。 當您建立專案時，Visual Studio 會產生組件的 GUID。 對應至 <xref:System.Guid>。  
  
 **中性語言**  
 指定組件所支援的文化特性。 對應至 <xref:System.Resources.NeutralResourcesLanguageAttribute>。 預設值為 [(無)]。  
  
 **讓組件成為 COM-Visible**  
 指定組件中的類型是否可供 COM 使用。 對應至 <xref:System.Runtime.InteropServices.ComVisibleAttribute>。  
  
## <a name="see-also"></a>另請參閱  
 [Application Page, Project Designer (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [屬性](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)



