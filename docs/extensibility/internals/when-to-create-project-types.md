---
title: "當建立專案類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b532ad4e72fb15cd9409c362259347f6f3833d2e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="when-to-create-project-types"></a>建立專案類型的時機
建立新的專案類型提供基礎自訂[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]為您的使用者。 不過，建立新的專案類型不需要所有[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]自訂項目。 下列指導方針有助於您判斷是否為您的案例需要新的專案類型。  
  
## <a name="create-a-new-project-type"></a>建立新的專案類型  
 您必須建立的專案類型，如果您想要自訂[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以扮演一或多個下列方法：  
  
-   參與建置、 部署組態和原始檔控制。  
  
-   提供偵錯支援。  
  
-   顯示專案中的項目**方案總管 中**。  
  
-   使用**開啟專案**或**新專案** 對話方塊。  
  
-   支援專案巢狀結構。  
  
## <a name="extend-an-existing-project-type"></a>擴充現有的專案類型  
 您可能想要建立新的專案類型，可以用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]下列方式來修改或擴充現有的專案類型的行為，例如，修改的建置程序[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案：  
  
-   使用多個檔案當做單一單位。  
  
-   顯示單一檔案的子項目階層。  
  
-   顯示編輯器周圍的命令內容。  
  
-   編輯器會顯示服務內容。  
  
## <a name="use-an-existing-project-type"></a>使用現有的專案類型  
 建立新的專案不有時需要。 下表顯示您沒有建立的專案類型的工作。  
  
|工作|說明|  
|----------|-----------------|  
|處理命令|任何 VSPackage 可以處理命令。|  
|建置編輯器|您可以註冊自訂編輯器。 如需詳細資訊，請參閱[文件視窗和編輯器](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)。|  
|擁有 windows|您可以建立工具和文件視窗，而不需要加入新的專案類型。|  
|[屬性] 視窗中的屬性|所有物件都可以都公開的屬性。|  
  
## <a name="create-a-project-subtype"></a>建立專案子類型  
 您可以使用專案子類型，而不需要建立新的專案類型擴充的 managed 的專案類型。 專案子類型使用 COM 彙總，來擴充 Microsoft 以撰寫的 managed 的專案[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]或[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]。 COM 彙總，您可以重複使用的 managed 的專案的系統實作，並仍然自訂透過彙總，以及使用支援介面的特定案例。 如需專案子類型的詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
## <a name="see-also"></a>另請參閱  
 [文件視窗和編輯器](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [檢查清單： 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)