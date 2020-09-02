---
title: 狀態持續性的支援 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434315"
---
# <a name="support-for-state-persistence"></a>狀態持續性支援
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 可以維持一般物件的狀態。 例如，方案和專案屬性會儲存至方案和專案檔，以及從方案和專案檔案還原。 您可以將使用者設定匯出至設定檔，並從設定檔匯入。  
  
 Vspackage 通常依賴本機儲存體（在系統登錄中），或在目前使用者或電腦的應用程式資料夾中。 需要少量空間來儲存的值（例如整數和字串）通常會儲存在系統登錄中。 需要大量儲存空間（例如點陣圖）的值會儲存在檔案中。 檔案的路徑本身可以儲存在系統登錄中。 持續性機制必須具有存取本機儲存體的許可權。  
  
## <a name="support-for-locating-local-storage"></a>支援尋找本機儲存體  
 <xref:Microsoft.VisualStudio.Shell.Package>類別可支援在 system registry 或 application data 資料夾中尋找目前使用者或電腦的狀態資訊。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 傳回本機電腦的登錄根目錄路徑 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，例如 HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp。  
  
 本機登錄根目錄是從 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> 服務取得。 如果無法使用，則會從 <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> VSPackage 的屬性取得。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 傳回每一電腦的目前使用者 (路徑) 的登錄根目錄，例如 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp。  
  
 本機登錄根目錄是從 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> 服務取得。 如果無法使用，則會從 VSPackage 的 DefaultLocalRegistryRoot 屬性取得。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 傳回目錄的路徑，做為 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 目前漫遊使用者資料的通用儲存機制，例如 c:\documents and And Settings \\ *YourAccountName*\Application Data\Microsoft\VisualStudio\8.0Exp。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 傳回目錄的路徑，做為 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 目前非漫遊使用者資料的通用儲存機制，例如 c:\documents and And Settings \\ *YourAccountName*\Local Settings\Application Data\Microsoft\VisualStudio\8.0Exp。  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage 狀態](../misc/vspackage-state.md)