---
title: 專案持續性 |Microsoft Docs
description: 瞭解專案設計中的持續性，包括使用 IPersistFileFormat 來保存檔案和非檔案型專案物件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 17b9fc40a93a926fde5edc28e93f7751b919611c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903641"
---
# <a name="project-persistence"></a>專案持續性
持續性是您專案的重要設計考慮。 大部分的專案都會使用代表檔案的專案專案; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 也支援以非檔案為基礎之資料的專案。 專案和專案檔案所擁有的兩個檔案都必須保存。 IDE 會指示專案儲存本身或專案專案。

 專案的範本會傳遞至專案 factory。 範本應該根據特定專案類型的需求，支援所有專案專案的初始化。 這些範本之後可以儲存為專案檔，然後由 IDE 透過解決方案來管理。 如需詳細資訊，請參閱[使用專案工廠和方案建立專案實例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。 [](../../extensibility/internals/solutions-overview.md)

 專案專案可以是以檔案為基礎或非檔案型的：

- 以檔案為基礎的專案可以是本機或遠端。 例如，在 c # 中的 Web 專案中，連接至遠端系統上的檔案會保存在本機，而檔案本身會保存在遠端系統上。

- 非檔案型專案可以將專案儲存至資料庫或存放庫。

## <a name="commit-models"></a>認可模型
 決定專案專案的所在位置之後，您必須選擇適當的認可模型。 例如，在具有本機檔案的檔案型模型中，每個專案都可以自主儲存。 在儲存機制模型中，您可以將數個專案儲存在一個交易中。 如需詳細資訊，請參閱 [專案類型設計決策](../../extensibility/internals/project-type-design-decisions.md)。

 為了判斷副檔名，專案會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 介面，此介面會提供資訊讓物件的用戶端執行 [ **另存** 新檔] 對話方塊，也就是填入 [ **另存** 新檔] 下拉式清單，並管理初始副檔名。

 IDE `IPersistFileFormat` 會呼叫專案上的介面，以指出專案應適當保存專案專案。 因此，物件擁有其檔案和格式的所有層面。 這包括物件的格式名稱。

 如果專案不是檔案， `IPersistFileFormat` 則仍然會保存非檔案型專案。 專案檔（例如專案的 vbp 檔案 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 或專案的 vcproj 檔案 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ）也必須保存。

 針對儲存動作，IDE 會檢查執行中的檔資料表 (RDT) ，而且階層會將命令傳遞給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> 介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>方法會實作為判斷專案是否已修改。 如果專案具有，則 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> 會執行方法以儲存修改過的專案。

 介面上的方法 `IVsPersistHierarchyItem2` 是用來判斷專案是否可以重載，而且如果專案可以的話，也可以重載。 此外，您 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> 可以執行方法來使變更的專案在不儲存的情況下捨棄。

## <a name="see-also"></a>另請參閱
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [使用專案 Factory 建立專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
