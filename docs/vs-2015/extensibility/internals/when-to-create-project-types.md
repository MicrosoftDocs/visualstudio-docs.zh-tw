---
title: 建立專案類型的時機 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1744801b7efe591c449e74796c3c7d297dc3f982
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061706"
---
# <a name="when-to-create-project-types"></a>建立專案類型的時機
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

建立新的專案類型提供基礎自訂[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]為您的使用者。 不過，建立新的專案類型不需要所有[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]自訂項目。 下列指導方針可協助您判斷新的專案類型是否需要針對您的案例。  
  
## <a name="create-a-new-project-type"></a>建立新的專案類型  
 您必須先建立專案類型，如果您想要自訂[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]以扮演一或多個下列的方式：  
  
- 參與建置、 部署、 設定和原始檔控制。  
  
- 偵錯支援的供應項目。  
  
- 顯示專案中的項目**方案總管 中**。  
  
- 使用**開啟專案**或是**新的專案** 對話方塊。  
  
- 支援專案巢狀結構。  
  
## <a name="extend-an-existing-project-type"></a>擴充現有的專案類型  
 您可能想要建立新的專案類型可供[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]下列方式來修改或擴充現有的專案類型的行為，例如，修改的建置程序[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]專案：  
  
- 使用多個檔案當做單一單位。  
  
- 顯示單一檔案的子項目階層。  
  
- 顯示編輯器命令內容。  
  
- 編輯器中顯示的服務內容。  
  
## <a name="use-an-existing-project-type"></a>使用現有的專案類型  
 建立新的專案則有時候不需要。 下表顯示您沒有建立的專案類型的工作。  
  
|工作|描述|  
|----------|-----------------|  
|處理命令|任何的 VSPackage 可以處理命令。|  
|建置編輯器|您可以註冊自訂編輯器。 如需詳細資訊，請參閱 <<c0> [ 文件的 Windows 和編輯器](http://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc)。|  
|擁有 windows|您可以建立工具和文件視窗，而不會增加新的專案類型。|  
|在 [屬性] 視窗中公開的屬性|所有物件都可以都公開屬性。|  
  
## <a name="create-a-project-subtype"></a>建立專案子類型  
 您可以使用專案子類型，來擴充受管理的專案類型，而不需要建立新的專案類型。 專案子類型來擴充 Microsoft 以撰寫的 managed 的專案中使用 COM 彙總[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]或[!INCLUDE[csprcs](../../includes/csprcs-md.md)]。 COM 彙總，您可以重複使用大部分的 managed 的專案系統實作，並仍然透過彙總，以及使用支援的介面的特定案例自訂。 如需有關專案子類型的詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
## <a name="see-also"></a>另請參閱  
 [文件的 Windows 和編輯器](http://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc)   
 [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)
