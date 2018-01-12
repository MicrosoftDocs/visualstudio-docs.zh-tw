---
title: "VBA 和 Office 方案在 Visual Studio 中比較 |Microsoft 文件"
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
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d6b2fd1cbf3ad2d58575b22b55f7ec1dc40b6ed4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>VBA 和 Office 方案 (在 Visual Studio 中) 比較
  Microsoft Visual Basic for Applications (VBA) 會使用與 Office 應用程式緊密整合的 Unmanaged 程式碼。 使用 Visual Studio 建立的 Microsoft Office 專案可讓您充分利用 .NET Framework 和 Visual Studio 設計工具。  
  
 如需您可以使用 Visual Studio 建立的 Office 方案類型的資訊，請參閱[Office 方案開發概觀 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="comparison"></a>邏輯比對  
 下表提供 VBA 方案和 Visual Studio 中的 Office 方案之間的基本比較。  
  
|VBA 方案|Visual Studio 中的 Office 方案|  
|-------------------|---------------------------------------|  
|使用已連接到特定文件並一起保存的程式碼。|使用與文件 (適用於文件層級自訂) 分開儲存的程式碼，或應用程式 (適用於 VSTO 增益集) 所載入之組件中的程式碼。|  
|使用 Office 物件模型和 VBA API。|可讓您存取 Office 物件模型和 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] API。|  
|針對巨集錄製和簡化開發人員經驗而設計。|針對安全性、簡化的程式碼維護，以及使用完整 Visual Studio 整合式開發環境 (IDE) 的能力而設計。|  
|相當適用於從與 Office 應用程式非常緊密整合獲益的方案。|相當適用於從 Visual Studio 完整資源和 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]獲益的方案。|  
|對於企業而言有限制，尤其是在安全性和部署方面。|針對在企業中使用而設計。|  
  
 有些事仍然使用 VBA 較容易快速地達成。 具體而言，您可能想要繼續使用 VBA 的原因有：  
  
-   自訂工作表函式。  
  
-   巨集錄製。  
  
## <a name="combining-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>合併 VBA 方案與使用 Visual Studio 建立的 Office 方案  
 您可以從使用 Visual Studio 建立的 Office 方案中呼叫 VBA 程式碼，也可以從 VBA 在使用 Visual Studio 建立的 Office 方案中呼叫程式碼。 特定技術會依 Office 方案是 VSTO 增益集或文件層級自訂而有所不同。 如需詳細資訊，請參閱 [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) 與 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)。  
  
## <a name="see-also"></a>請參閱  
 [Office 方案開發概觀 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [在 VSTO 增益集中呼叫程式碼，從其他 Office 方案](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)   
 [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [開始使用 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  