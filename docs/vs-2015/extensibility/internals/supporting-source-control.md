---
title: 支援原始檔控制 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1166197a5c79dcb0d1ddf4018227914346a6172
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156071"
---
# <a name="supporting-source-control"></a>支援原始檔控制
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 支援專案或編輯器的檔案簽出、簽入和其他原始檔控制作業。 作為原始檔控制用戶端， [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 是設計來與原始檔控制套件互動，例如 [!INCLUDE[vsvss](../../includes/vsvss-md.md)] ，可為動態定義的檔案集提供封存、版本控制及控制功能。  
  
## <a name="in-this-section"></a>本節內容  
 [原始檔控制套件的模型](../../extensibility/internals/model-for-source-control-packages.md)  
 描述專案類型必須執行以支援原始檔控制的介面。  
  
 [設計決策](../../extensibility/internals/source-control-design-decisions.md)  
 提供問題，這些問題的答案會變更您如何執行專案類型。  
  
 [組態詳細資料](../../extensibility/internals/source-control-configuration-details.md)  
 描述支援的原始檔控制如何變更專案類型的執行。  
  
 [專案和編輯器適用的其他方針](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 討論專案類型和編輯器的最佳作法。  
  
 [執行階段詳細資料](../../extensibility/internals/source-control-runtime-details.md)  
 描述如何在使用者將專案新增至原始檔控制系統時註冊專案。  
  
## <a name="reference"></a>參考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 向環境或原始檔控制封裝指出檔案即將在記憶體中變更或儲存。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 允許專案和階層向原始檔控制註冊自己，並取得原始檔控制狀態的相關資訊。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 在專案系統中執行，以提供專案檔和專案專案的原始檔控制。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 專案用來查詢環境，以取得在方案中新增、移除或重新命名檔案或目錄的許可權。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 通知用戶端對專案檔或目錄所做的變更。  
  
## <a name="related-sections"></a>相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 提供專案的總覽，作為 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 整合式開發環境 (IDE) 的基本組建區塊。 連結會提供給其他主題，以說明專案如何控制組建和編譯器代碼。
