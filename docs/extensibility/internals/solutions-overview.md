---
title: "方案概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 539ceb45cce6c317ed3723c5006e6d2a77029335
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="solutions-overview"></a>方案概觀
方案是建立應用程式一起運作的一或多個專案的群組。 屬於方案的專案和狀態資訊會儲存在兩個不同的方案檔。 方案 (.sln) 檔案是以文字為基礎和可以是放在原始檔控制之下，而且使用者之間共用。 方案使用者選項 (.suo) 檔案是二進位檔案。 如此一來，.suo 檔案不能放在原始檔控制之下，並包含使用者特定資訊。  
  
 任何 VSPackage 可以寫入任一類型的方案檔。 因為檔案的本質，有兩個不同的介面實作，以寫入。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>介面.sln 檔案中寫入文字資訊和<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>介面.suo 檔案中寫入二進位資料流。  
  
> [!NOTE]
>  專案並沒有明確寫入項目本身的方案檔。環境會處理該專案。 因此，除非您想要新增其他內容為方案檔，您不需要以這種方式註冊您的 VSPackage。  
  
 支援方案持續性的每個 VSPackage 使用三種介面，<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>介面，它是由環境實作，以及呼叫 VSPackage，以及`IVsPersistSolutionProps`和`IVsPersistSolutionOpts`，兩者實作哪一個是由 VSPackage。 `IVsPersistSolutionOpts`介面只需要由 VSPackage 的.suo 檔案寫入個人資訊是否實作。  
  
 開啟方案時，下列程序就會發生。  
  
1.  環境會讀取方案。  
  
2.  如果環境找到`CLSID`，它會載入對應的 VSPackage。  
  
3.  如果 VSPackage 載入時，環境呼叫`QueryInterface`如<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>介面，VSPackage 所需要的介面。  
  
    1.  當讀取.sln 檔案，環境會呼叫`QueryInterface`如`IVsPersistSolutionProps`。  
  
    2.  當讀取.suo 檔案，環境會呼叫`QueryInterface`如`IVsPersistSolutionOpts`。  
  
 可讓您使用這些檔案與相關的特定資訊位於[方案 (。Sln) 檔案](../../extensibility/internals/solution-dot-sln-file.md)和[方案使用者選項 (。Suo) 檔案](../../extensibility/internals/solution-user-options-dot-suo-file.md)。  
  
> [!NOTE]
>  如果您想要建立組成兩個專案組態，並從組建排除第三個新方案組態時，您需要使用屬性頁 UI 或 automation。 您無法直接變更方案建置 manager 組態和其屬性，但您可以使用操作使用的方案組建管理員`SolutionBuild`從 DTE automation 模型中的類別。 如需有關設定解決方案的詳細資訊，請參閱[方案組態](../../extensibility/internals/solution-configuration.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>