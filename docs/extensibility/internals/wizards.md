---
title: "精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6d9d468997d0e0f4cc913db1b9ac316f4e698f99
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wizards"></a>精靈
建立精靈之後，您通常想要將它加入至[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE)，以便其他人可以使用它。 加入的精靈則會出現在**加入新的專案**或**加入新項目**對話方塊。 若要查看**加入新的專案**或**加入新項目**對話方塊方塊中，開啟的方案中以滑鼠右鍵按一下**方案總管 中**，指向 **新增**，和然後按一下 **新專案**或**新項目**。  
  
 精靈可以實作在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，讓使用者選取的樹狀檢視中開啟時，可用的值從**加入新的專案**對話方塊或**加入新項目**對話方塊中，或當他們按一下滑鼠右鍵中的項目**方案總管 中**。  
  
 在精靈中，您可以提供當地語系化的新專案或輕鬆，名稱的選項，您可以決定當他們選取精靈時，使用者會看到的圖示。 您也可以控制相對於其他可用的項目; 新的項目出現的順序項目沒有依照字母順序排列。  
  
 您也可以提供根據開啟時，會傳遞給精靈的自訂參數會以不同的方式，啟動精靈。  
  
 本節中的主題將討論您實作會造成檔案[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**加入新的專案**和**加入新項目**列出可用的精靈與範本精靈對話方塊和程式精靈在 IDE 中正常運作所必須符合的需求。  
  
## <a name="in-this-section"></a>本節內容  
 [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 提供的哪一個範本概觀目錄描述檔案，並說明其顯示在對話方塊中的專案相關聯的範本檔案、 精靈.vsz 檔案和資料夾在 IDE 中的運作方式。  
  
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 說明如何在 IDE 中啟動精靈，並列出.vsz 檔案中的三個部分。  
  
 [精靈介面 (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 描述`IDTWizard`精靈必須能夠在 IDE 中實作的介面。  
  
 [內容參數](../../extensibility/internals/context-parameters.md)  
 說明如何實作精靈，以及當 IDE 會將內容參數傳遞到實作。  
  
 [自訂參數](../../extensibility/internals/custom-parameters.md)  
 說明如何使用自訂參數來控制精靈作業後啟動精靈。  
  
## <a name="related-sections"></a>相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 提供額外的主題提供有關如何設計新的專案類型的資訊連結。  
  
 [逐步解說： 建立精靈](http://msdn.microsoft.com/Library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 說明如何建立精靈。  
  
 [擴充專案](../../extensibility/extending-projects.md)  
 描述如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案和解決方案組織程式碼檔案和資源檔，以及如何實作原始檔控制。