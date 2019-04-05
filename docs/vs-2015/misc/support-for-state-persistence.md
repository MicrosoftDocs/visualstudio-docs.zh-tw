---
title: 狀態持續性支援 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945711"
---
# <a name="support-for-state-persistence"></a>狀態持續性支援
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 可以維護狀態的通用物件。 比方說，方案和專案屬性會儲存到與方案和專案檔從還原的。 可以匯出為使用者設定，而且從設定檔匯入。  
  
 Vspackage 通常依賴本機儲存體，在系統登錄或目前的使用者或電腦的應用程式資料資料夾中。 儲存體，例如整數和字串，所需的少量空間的值通常會儲存在系統登錄中。 儲存體，例如點陣圖、 需要大量空間的值會儲存在檔案中。 檔案的路徑可以本身儲存在系統登錄中。 持續性機制都必須擁有存取本機儲存體的權限。  
  
## <a name="support-for-locating-local-storage"></a>尋找本機儲存體的支援  
 <xref:Microsoft.VisualStudio.Shell.Package>類別尋找目前的使用者或電腦系統登錄或應用程式資料資料夾中的狀態資訊提供支援。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 傳回本機電腦的登錄根目錄的路徑[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，例如 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0Exp。  
  
 本機登錄根目錄取自<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>服務。 如果這是無法使用，它取自<xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute>VSPackage 的屬性。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 傳回目前的使用者 （每部電腦） 的路徑的登錄根目錄[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，例如 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp。  
  
 本機登錄根目錄取自<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>服務。 如果這是無法使用，則會從 VSPackage 的 DefaultLocalRegistryRoot 屬性中取得。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 傳回做為通用儲存機制的目錄路徑[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]目前漫遊使用者資料，例如 C:\Documents and Settings\\*YourAccountName*\applicationVisualStudio\8.0Exp。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 傳回做為通用儲存機制的目錄路徑[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]目前非漫遊使用者資料，例如 C:\Documents and Settings\\*YourAccountName*settings\applicationData\Microsoft\VisualStudio\8.0Exp。  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage 狀態](../misc/vspackage-state.md)