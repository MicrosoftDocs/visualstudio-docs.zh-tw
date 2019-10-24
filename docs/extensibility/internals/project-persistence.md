---
title: 專案持續性 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a95c919de9b87ed1782cbdcb029efbf191958f5a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725456"
---
# <a name="project-persistence"></a>專案持續性
持續性是您專案的重要設計考慮。 大部分專案都會使用代表檔案的專案專案; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 也支援不以檔案為基礎之資料的專案。 專案和專案檔所擁有的兩個檔案都必須保存。 IDE 會指示專案儲存自己或專案專案。

 專案的範本會傳遞至專案 factory。 範本應該支援根據特定專案類型的需求，來初始化所有專案專案。 這些範本稍後可以儲存為專案檔，並透過方案由 IDE 管理。 如需詳細資訊，請參閱使用專案處理站和[方案](../../extensibility/internals/solutions-overview.md)[建立專案實例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。

 專案專案可以是以檔案為基礎或非檔案型：

- 以檔案為基礎的專案可以是本機或遠端。 例如，在的C#Web 專案中，遠端系統上的檔案連接會保存在本機，而檔案本身會保存在遠端系統上。

- 不以檔案為基礎的專案可以將專案儲存至資料庫或存放庫。

## <a name="commit-models"></a>認可模型
 決定專案專案的所在位置之後，您必須選擇適當的認可模型。 例如，在具有本機檔案的檔案型模型中，每個專案都可以獨立儲存。 在存放庫模型中，您可以將數個專案儲存在一個交易中。 如需詳細資訊，請參閱[專案類型設計決策](../../extensibility/internals/project-type-design-decisions.md)。

 為了決定副檔名，專案會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 介面，這會提供資訊讓物件的用戶端執行 [**另存**新檔] 對話方塊，也就是填入 [**存檔類型**] 下拉式清單，然後管理初始副檔名。

 IDE 會呼叫專案上的 `IPersistFileFormat` 介面，以指示專案應適當保存其專案專案。 因此，物件擁有其檔案和格式的所有層面。 這包括物件格式的名稱。

 如果專案不是檔案，`IPersistFileFormat` 仍會保存非檔案型專案的方式。 專案檔（例如 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 專案的 .vbp 檔或 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 專案的 vcproj 檔案）也必須保存。

 針對儲存動作，IDE 會檢查執行中的檔資料表（RDT），而階層會將命令傳遞給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> 介面。 會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> 方法，以判斷專案是否已修改。 如果專案具有，則會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> 方法以儲存修改過的專案。

 @No__t_0 介面上的方法是用來判斷是否可以重載專案，如果專案可以，則會重載。 此外，也可以執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> 方法，使變更的專案在未儲存的情況下捨棄。

## <a name="see-also"></a>請參閱
- [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [使用 Project Factory 建立專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)