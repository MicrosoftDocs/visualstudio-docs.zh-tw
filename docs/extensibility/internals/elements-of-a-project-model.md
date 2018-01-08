---
title: "專案模型的項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c5f230da41efa8dd2fa522a5f86ae1402991b2cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="elements-of-a-project-model"></a>專案模型的項目
介面與實作中的所有專案[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]共用基本結構： 您的專案類型的專案模型。 在您專案的模型，也就是您開發的 VSPackage，您可以建立符合您的設計決策及 IDE 所提供的通用功能搭配運作的物件。 雖然您控制的專案項目會保存方式，例如，您無法控制通知檔案必須 persisted。 當使用者將焦點放在開啟的專案項目，並選擇**儲存**上**檔案**功能表[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能表列，您的專案類型程式碼必須攔截從 IDE 命令、 保留檔案，並傳送通知回 IDE 不會再變更的檔案時。  
  
 VSPackage 會提供給 IDE 介面的存取權的服務透過 IDE 與互動。 例如，透過特定的服務，您監視和路由命令，並提供選取之項目的專案中的內容資訊。 由服務提供的所有全域 IDE 功能所需的 VSPackage。 如需服務的詳細資訊，請參閱[How to： 取得服務](../../extensibility/how-to-get-a-service.md)。  
  
 其他實作的考量：  
  
-   在單一專案模型可以包含多個專案類型。  
  
-   專案類型以及伴隨專案處理站會向獨立 Guid。  
  
-   每個專案都必須有範本檔案或精靈，以初始化新的專案檔，當使用者建立新的專案，透過[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]UI。 例如，[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]範本初始化功能最後會變成.vcproj 檔案。  
  
 下圖顯示主要的介面、 服務及撰寫一般專案實作的物件。 您可以使用應用程式協助程式，HierUtil7，若要建立的基礎物件和其他程式設計的重複使用。 如需 HierUtil7 應用程式協助程式的詳細資訊，請參閱[不在組建中： 使用 HierUtil7 專案類別以實作專案類型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)。  
  
 ![Visual Studio 專案模型圖形](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
專案模型  
  
 如需的介面和列在上圖中，服務和其他選擇性介面不包含在圖表中的詳細資訊，請參閱[專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)。  
  
 專案可以支援的命令，因此必須實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面來參與命令路由透過命令內容的 Guid。  
  
## <a name="see-also"></a>請參閱  
 [檢查清單： 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [不在組建中： 使用 HierUtil7 專案類別來實作的專案型別 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)   
 [使用 Project Factory 建立的專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [如何： 取得服務](../../extensibility/how-to-get-a-service.md)   
 [建立專案類型](../../extensibility/internals/creating-project-types.md)