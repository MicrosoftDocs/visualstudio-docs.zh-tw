---
title: 精靈 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e58ebd736f7bb9f35df6e41d5235f36f7037259
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687621"
---
# <a name="wizards"></a>精靈
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

建立精靈之後，您通常想要將它新增至[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]整合式開發環境 (IDE)，以便其他人可以使用它。 已新增的精靈接著會出現在**加入新的專案**或是**加入新項目**對話方塊。 若要查看**加入新的專案**或**加入新項目**對話方塊方塊中，以滑鼠右鍵按一下中開啟的方案**方案總管 中**，指向**新增**，及然後按一下**新的專案**或是**新項目**。  
  
 精靈可實作於[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，讓使用者從可用的值何時開啟的樹狀檢視中選取**加入新的專案** 對話方塊或**加入新項目** 對話方塊中，或當他們以滑鼠右鍵按一下中的項目**方案總管 中**。  
  
 在精靈中，您可以提供當地語系化的新增專案] 或 [輕鬆，名稱的選項，您可以決定當他們選取精靈時，使用者會看到的圖示。 您也可以控制新的項目相對於其他可用的項目; 出現的順序項目沒有依照字母順序排列。  
  
 您也可以提供一個精靈，根據自訂參數傳遞至精靈開啟時以不同的方式啟動。  
  
 在本節中的主題將討論，讓您實作的檔案[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]**加入新的專案**並**加入新項目**列出您可以使用精靈與範本之間的精靈對話方塊與您的精靈必須符合才能正確運作，在 IDE 中的需求。  
  
## <a name="in-this-section"></a>本節內容  
 [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 提供概略的範本目錄描述檔案，並說明其運作在 IDE 中顯示資料夾、 精靈.vsz 檔案和相關聯的專案 對話方塊中的範本檔案的方式。  
  
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 說明如何在 IDE 啟動精靈，並列出.vsz 檔案的三個部分。  
  
 [精靈介面 (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 描述`IDTWizard`精靈必須實作以在 IDE 中工作的介面。  
  
 [內容參數](../../extensibility/internals/context-parameters.md)  
 說明如何實作精靈以及 IDE 會將內容參數傳遞至實作時，可能發生的狀況。  
  
 [自訂參數](../../extensibility/internals/custom-parameters.md)  
 說明如何使用自訂參數來控制精靈 的作業之後會啟動精靈。  
  
## <a name="related-sections"></a>相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 提供額外的主題提供有關如何設計新的專案類型的資訊連結。  
  
 [逐步解說：建立精靈](https://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 說明如何建立精靈。  
  
 [擴充專案](../../extensibility/extending-projects.md)  
 描述如何使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 專案和解決方案組織程式碼檔案和資源檔，以及如何實作原始檔控制。
