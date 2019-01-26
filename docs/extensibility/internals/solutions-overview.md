---
title: 方案概觀 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 090f70776ab3323be55d13888f29d4855386a511
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020889"
---
# <a name="solutions-overview"></a>方案概觀
解決方案是建立應用程式一起運作的一或多個專案的群組。 屬於方案的專案和狀態資訊會儲存在兩個不同的方案檔。 方案 (.sln) 檔案是以文字為基礎和可放置在原始程式碼控制之下，並讓使用者彼此共用。 方案使用者選項 (.suo) 檔案是二進位。 如此一來，.suo 檔案不能放在原始檔控制之下，並包含使用者特定資訊。  
  
 任何的 VSPackage 可以寫入任一類型的方案檔。 由於檔案的情況，有兩個不同的介面實作進行寫入。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>介面會將文字資訊寫入而非.sln 檔案和<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>介面.suo 檔案中寫入二進位資料流。  
  
> [!NOTE]
>  不需要明確寫入項目本身的方案檔; 專案環境將會為專案處理。 因此，除非您想要為方案檔中加入其他內容，您不需要以這種方式註冊 VSPackage。  
  
 每個支援解決方案的持續性的 VSPackage 會使用三個介面，<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>介面，它是由環境實作，而且呼叫 vspackage，以及`IVsPersistSolutionProps`和`IVsPersistSolutionOpts`，兩者實作，這是 vspackage。 `IVsPersistSolutionOpts`介面只需要實作私用資訊是否要寫入 vspackage.suo 檔案。  
  
 開啟方案時，下列程序進行。  
  
1. 環境讀取方案。  
  
2. 如果環境找到`CLSID`，它會載入對應的 VSPackage。  
  
3. 如果載入 VSPackage 時，此環境會呼叫`QueryInterface`針對<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>介面，VSPackage 所需要的介面。  
  
   1.  從.sln 檔案讀取時，環境會呼叫`QueryInterface`針對`IVsPersistSolutionProps`。  
  
   2.  從.suo 檔案讀取時，環境會呼叫`QueryInterface`針對`IVsPersistSolutionOpts`。  
  
   使用這些檔案的相關的特定資訊可在[解決方案 (。Sln) 檔案](../../extensibility/internals/solution-dot-sln-file.md)和[方案使用者選項 (。Suo) 檔案](../../extensibility/internals/solution-user-options-dot-suo-file.md)。  
  
> [!NOTE]
>  如果您想要建立新的方案組態包含兩個專案組態，並從組建排除第三，您要使用的屬性頁面 UI 或自動化。 您無法直接變更方案的組建管理員設定和其屬性，但您可以使用操作使用的解決方案組建管理員`SolutionBuild`從 DTE automation 模型中的類別。 如需有關如何設定解決方案的詳細資訊，請參閱 <<c0> [ 方案組態](../../extensibility/internals/solution-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>