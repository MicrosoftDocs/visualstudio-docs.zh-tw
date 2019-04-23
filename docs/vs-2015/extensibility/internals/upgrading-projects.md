---
title: 將專案升級 |Microsoft Docs
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
ms.openlocfilehash: 7e97e21b2d08d7398a4372ac31cda63b5cfb9fe9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100595"
---
# <a name="upgrading-projects"></a>升級專案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

從舊版變更專案模型[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]到下一個可能需要專案和方案，會升級，使它們可以較新版本上執行。 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]提供可用來實作您自己的專案中的升級支援的介面。  
  
## <a name="upgrade-strategies"></a>升級策略  
 若要支援升級，您的專案系統實作必須定義和實作的升級策略。 在決定您的策略時，您可以選擇支援的並存 (SxS) 備份、 複製備份，或兩者。  
  
- SxS 備份表示專案會複製那些需要升級的位置，新增適當的檔案名稱尾碼，例如，".old"的檔案。  
  
- 複製專案將所有的專案項目複製到使用者所提供的備份位置的備份方式。 然後會升級原始專案位置的相關檔案。  
  
## <a name="how-upgrade-works"></a>如何升級的運作方式  
 當舊的版本中建立的方案[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]開啟在較新版本中，方案檔案來判斷它是否需要升級的 IDE 檢查。 如果升級為必要項，**升級精靈**引導使用者完成升級程序時，就會自動啟動。  
  
 當升級需求的解決方案時，它會查詢每個專案處理站，其升級策略。 策略會決定 project factory 支援複製備份 」 或 「 SxS 備份。 將資訊傳送至**升級精靈**，其可收集備份所需的資訊，並向使用者呈現的適用選項。  
  
### <a name="multi-project-solutions"></a>多專案的方案  
 如果方案包含多個專案，而且不同的升級策略，例如當C++專案，只支援 SxS 備份和 Web 專案，只支援複製備份，project factory 必須交涉的升級策略。  
  
 解決方案會查詢每個專案 factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>。 然後它會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A>看看通用專案檔是否需要升級，並判斷支援的升級策略。 **升級精靈**接著叫用。  
  
 使用者完成精靈之後<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>執行實際升級每個專案 factory 上呼叫。 若要簡化備份，提供 IVsProjectUpgradeViaFactory 方法<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>服務記錄檔的升級程序的詳細資料。 此服務無法快取。  
  
 更新所有相關的通用檔案之後, 每個專案的處理站可以具現化專案。 專案的實作必須支援<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>然後呼叫方法來升級所有相關的專案項目。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法不提供 SVsUpgradeLogger 服務。 這項服務，可由呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>。  
  
## <a name="best-practices"></a>最佳作法  
 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>來檢查是否可以編輯檔案，再加以編輯，以及可以將它儲存在儲存它之前的服務。 這可協助您的備份和升級的實作會處理原始檔控制下的專案檔案、 檔案為權限不足，依此類推。  
  
 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>服務備份的所有階段期間，並升級成功或失敗的升級程序提供相關資訊。  
  
 如需有關備份和升級專案的詳細資訊，請參閱註解 IVsProjectUpgrade vsshell2.idl 中。  
  
## <a name="see-also"></a>另請參閱  
 [專案](../../extensibility/internals/projects.md)   
 [升級自訂專案](../../misc/upgrading-custom-projects.md)   
 [升級專案項目](../../misc/upgrading-project-items.md)
