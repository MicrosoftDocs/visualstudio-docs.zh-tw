---
title: 專案持續性 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff836f56601adeba7b3df675207701f6e2d6e7fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729569"
---
# <a name="project-persistence"></a>專案持續性
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

持續性是重要的設計考量，為您的專案。 大部分的專案使用的專案項目代表檔案;[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]也支援其中的資料為非檔案型的專案。 這兩個專案和專案檔案所擁有的檔案必須被 persisted。 IDE 會指示專案，以儲存本身或專案項目。  
  
 專案範本會傳遞至 project factory。 範本應該支援所有的專案項目，根據特定專案類型的需求的初始化。 這些範本稍後會儲存為專案檔，IDE 中透過此解決方案所管理。 如需詳細資訊，請參閱 <<c0> [ 建立專案執行個體所使用 Project Factory](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)並[解決方案](../../extensibility/internals/solutions.md)。  
  
 專案項目可以是檔案為基礎，或非檔案型：  
  
-   檔案為基礎的項目可以是本機或遠端。 在 C# 中的 Web 專案，比方說，連線到遠端系統上的檔案保存在本機，而檔案本身會保存在遠端系統上。  
  
-   非檔案型的項目可以將項目儲存到資料庫或儲存機制。  
  
## <a name="commit-models"></a>認可模型  
 決定專案項目位於何處之後, 您必須選擇適當的認可模型。 例如，在具有本機檔案的檔案為基礎的模型，每個專案可以儲存自主。 在儲存機制模型中，您可以儲存在單一交易中的數個項目。 如需詳細資訊，請參閱 <<c0> [ 專案類型的設計決策](../../extensibility/internals/project-type-design-decisions.md)。  
  
 若要判斷副檔名的檔案，請實作專案<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>介面，可提供資訊讓用戶端的物件，實作**另存新檔** 對話方塊中，也就是以填滿**檔案類型**下拉式清單列出並管理的初始檔案名稱副檔名。  
  
 IDE 呼叫`IPersistFileFormat`介面來表示專案應該保存其專案的專案項目適當地。 因此，物件會擁有其檔案和格式的所有層面。 這包括物件的格式的名稱。  
  
 其中的項目不是檔案，萬一`IPersistFileFormat`仍然是如何非檔案型的項目會保存。 專案檔，例如.vbp 檔案[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]專案或.vcproj 檔案[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]專案，也必須 persisted。  
  
 針對儲存動作，IDE 會檢查執行的文件資料表 (RDT) 和階層會傳遞到命令<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>而<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>實作方法，以判斷是否已修改的項目。 如果此項目，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A>實作方法，以儲存修改過的項目。  
  
 上的方法`IVsPersistHierarchyItem2`介面用來判斷是否可以重新載入項目，如果項目可以是的將它重新載入。 此外，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>可以實作方法，以造成變更的項目，而不會儲存遭到捨棄。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [使用 Project Factory 建立專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

