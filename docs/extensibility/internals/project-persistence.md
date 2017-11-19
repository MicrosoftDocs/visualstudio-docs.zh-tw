---
title: "專案持續性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bb782b79c00576a431c8f4453ddf020606aaf5a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="project-persistence"></a>專案持續性
持續性是您的專案的重要設計考量。 大部分的專案使用專案項目代表檔案。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]也支援其資料為非檔案型的專案。 這兩個檔案的擁有者專案和專案檔必須保存。 IDE 會指示專案以儲存本身或專案項目。  
  
 專案範本會傳遞至 project factory。 範本應該支援根據需求的特定專案類型的所有專案項目的初始設定。 這些範本可在之後儲存為專案檔及受解決方案透過 IDE。 如需詳細資訊，請參閱[建立專案執行個體所使用的專案 Factory](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)和[解決方案](../../extensibility/internals/solutions.md)。  
  
 專案項目可以是以檔案為基礎或非檔案為基礎：  
  
-   以檔案為基礎的項目可以是本機或遠端。 在 C# 中的 Web 專案，例如，連線到遠端系統上的檔案保留在本機，而遠端系統上保存檔案本身。  
  
-   以檔案為基礎的項目可以將項目儲存至資料庫或儲存機制。  
  
## <a name="commit-models"></a>認可模型  
 決定專案項目位於何處，您必須選擇適當的認可模式。 例如，在具有本機檔案的檔案為基礎的模型，每個專案可以儲存自主。 在儲存機制模型中，您可以儲存在單一交易中的數個項目。 如需詳細資訊，請參閱[專案類型的設計決策](../../extensibility/internals/project-type-design-decisions.md)。  
  
 若要判斷檔案名稱副檔名，請實作專案<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>介面，可提供資訊讓物件的用戶端實作**存**對話方塊 — 也就是以填滿**檔案類型**下拉式清單列出並管理初始檔案名稱的副檔名。  
  
 IDE 呼叫`IPersistFileFormat`介面上，表示專案應保存其專案的專案項目依適當情況。 因此，物件會擁有其檔案和格式的所有層面。 這包括物件的格式名稱。  
  
 在其中的項目不是檔案的情況下`IPersistFileFormat`仍然是如何非以檔案為基礎的項目會保存。 專案檔，例如.vbp 檔案[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案或.vcproj 檔案[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案，也必須 persisted。  
  
 用於儲存動作，IDE 會檢查執行中文件資料表 (RDT) 和階層會傳遞至命令<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>實作方法來判斷是否已修改的項目。 如果此項目，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A>方法實作以儲存修改過的項目。  
  
 上的方法`IVsPersistHierarchyItem2`介面用來判斷是否可以重新載入項目，如果項目可以是，將它重新載入。 此外，<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>方法可以實作以造成變更的項目而不會儲存被捨棄。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [使用 Project Factory 建立專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)