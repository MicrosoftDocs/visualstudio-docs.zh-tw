---
title: 專案持久性 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10a9cde91c0181fbfefbaa353c7c3702f4b36819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706465"
---
# <a name="project-persistence"></a>專案持續性
持久性是專案的關鍵設計考慮因素。 大多數專案使用表示檔的專案項;[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]還支援數據非基於檔的專案。 必須保留項目擁有的檔和專案檔。 IDE 指示專案保存自身或專案項。

 專案的範本將傳遞到項目工廠。 範本應支援根據特定項目類型的要求對所有專案項進行初始化。 這些範本以後可以保存為專案檔,並由IDE透過解決方案進行管理。 有關詳細資訊,請參閱[使用專案工廠和解決方案建立專案實例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。 [Solutions](../../extensibility/internals/solutions-overview.md)

 專案項目可以基於檔案,也可以是非式式檔的:

- 基於檔的項可以是本地的,也可以是遠端的。 例如,在 C# 中的 Web 專案中,與遠端系統上檔案的連接在本地保留,而檔本身則保留在遠端系統上。

- 非基於檔的項可以將項保存到資料庫或儲存庫。

## <a name="commit-models"></a>提交模型
 確定專案項的位置后,必須選擇適當的提交模型。 例如,在具有本地檔的基於檔的模型中,可以自動儲存每個專案。 在存儲庫模型中,可以在一個事務中保存多個項。 有關詳細資訊,請參閱[項目類型設計決策](../../extensibility/internals/project-type-design-decisions.md)。

 要確定檔案名副檔名,專案<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>實現 該介面,該介面提供的資訊使物件的用戶端能夠實現 **「儲存為」** 對話框,即填寫 **「儲存為類型」** 下拉清單並管理初始檔案名副檔名。

 IDE 調用專案`IPersistFileFormat`上 的介面以指示專案應保留其專案項。 因此,對象擁有其檔和格式的所有方面。 這包括物件的格式的名稱。

 在項不是檔案的情況下,`IPersistFileFormat`仍如何保留非基於檔的項。 還必須保留專案檔,如[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案的 .vbp[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]檔或 專案的 .vcproj 檔。

 對於保存操作,IDE 檢查正在運行的文檔表 (RDT),層次結構將命令<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem><xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>傳遞給 和介面。 實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>該方法以確定專案是否已修改。 如果項有,<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A>則實現該方法以保存修改後的項。

 介面上`IVsPersistHierarchyItem2`的方法用於確定是否可以重新載入項,如果可以重新載入項,則重新載入該項。 此外,還可以<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>實現該方法,以便在不保存的情況下丟棄已更改的專案。

## <a name="see-also"></a>另請參閱
- [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [使用專案 Factory 建立專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
