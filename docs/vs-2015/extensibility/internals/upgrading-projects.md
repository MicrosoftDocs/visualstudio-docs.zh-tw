---
title: 升級專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838827"
---
# <a name="upgrading-projects"></a>升級專案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

從某個版本到下一個版本的專案模型變更， [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 可能需要升級專案和方案，才能在較新的版本上執行。 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]提供介面，可用來在您自己的專案中執行升級支援。  
  
## <a name="upgrade-strategies"></a>升級策略  
 若要支援升級，您的專案系統實行必須定義和實行升級策略。 在決定您的策略時，您可以選擇支援並存 (SxS) 備份、複本備份或兩者。  
  
- SxS 備份表示專案只會複製需要就地升級的檔案，並新增適當的檔案名尾碼，例如「.old」。  
  
- 複本備份表示專案會將所有專案專案複製到使用者提供的備份位置。 然後會升級原始專案位置的相關檔案。  
  
## <a name="how-upgrade-works"></a>升級的運作方式  
 當在舊版中建立的方案 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 是在較新版本中開啟時，IDE 會檢查方案檔，以判斷是否需要升級方案檔。 如果需要升級，則會自動啟動 **升級嚮導** ，以引導使用者進行升級程式。  
  
 當解決方案需要升級時，它會查詢每個專案 factory 的升級策略。 此策略會決定專案 factory 是否支援複本備份或 SxS 備份。 這項資訊會傳送至 [ **升級嚮導]**，以收集備份所需的資訊，並向使用者呈現適用的選項。  
  
### <a name="multi-project-solutions"></a>多專案方案  
 如果解決方案包含多個專案，而且升級策略不同，例如，當僅支援 SxS 備份的 c + + 專案，以及僅支援複本備份的 Web 專案時，專案處理站必須協調升級策略。  
  
 方案會查詢的每個專案 factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 。 然後，它會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> 以查看全域專案檔是否需要升級，以及判斷支援的升級策略。 接著會叫用 **Upgrade Wizard** 。  
  
 當使用者完成嚮導之後， <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 會在每個專案 factory 上呼叫，以執行實際的升級。 為了加速備份，IVsProjectUpgradeViaFactory 方法會提供 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> 服務來記錄升級程式的詳細資料。 這是無法快取的服務。  
  
 更新所有相關的全域檔案之後，每個專案 factory 都可以選擇具現化專案。 專案執行必須支援 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>接著會呼叫方法來升級所有相關的專案專案。  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法不提供 SVsUpgradeLogger 服務。 這項服務可以藉由呼叫來取得 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 。  
  
## <a name="best-practices"></a>最佳做法  
 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 服務來檢查是否可以編輯檔案，然後儲存檔案。 這可協助您的備份和升級程式處理原始檔控制下的專案檔案、許可權不足的檔案等等。  
  
 在 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> 備份和升級的所有階段中使用服務，以提供升級程式成功或失敗的相關資訊。  
  
 如需有關備份和升級專案的詳細資訊，請參閱 vsshell2 中的 IVsProjectUpgrade 批註。  
  
## <a name="see-also"></a>另請參閱  
 [專案](../../extensibility/internals/projects.md)   
 [升級自訂專案](../../misc/upgrading-custom-projects.md)   
 [升級專案項目](../../misc/upgrading-project-items.md)
