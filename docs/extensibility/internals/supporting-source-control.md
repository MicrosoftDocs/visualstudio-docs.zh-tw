---
title: "支援原始檔控制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f5dd2a98ec84b656dc70a00236775710266c54ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-source-control"></a>支援的原始檔控制
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援的檔案簽出、 簽入和其他原始檔控制作業，您的專案或編輯器。 做為原始檔控制用戶端，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]設計來與原始檔控制封裝中，例如互動[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]，可保存、 版本控制和一組動態定義檔案的存取控制等機能。  
  
## <a name="in-this-section"></a>本節內容  
 [原始檔控制套件的模型](../../extensibility/internals/model-for-source-control-packages.md)  
 描述專案型別必須實作的介面來支援原始檔控制。  
  
 [設計決策](../../extensibility/internals/source-control-design-decisions.md)  
 提供的問題的答案可讓您變更專案類型的實作方式。  
  
 [設定詳細資料](../../extensibility/internals/source-control-configuration-details.md)  
 描述如何變更支援原始檔控制專案類型的實作。  
  
 [專案和編輯器的其他指導方針](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 討論針對專案類型和編輯器的最佳做法。  
  
 [執行階段詳細資料](../../extensibility/internals/source-control-runtime-details.md)  
 說明如何註冊專案，當使用者將它加入至原始檔控制系統。  
  
## <a name="reference"></a>參考資料  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 表示檔案是在記憶體中變更或儲存的原始檔控制封裝的環境。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 可讓專案和階層會與原始檔控制自行註冊並取得原始檔控制狀態的相關資訊。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 在專案檔和專案項目提供原始檔控制專案系統中實作。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 使用專案來查詢加入、 移除或重新命名檔案或目錄在方案中的權限的環境。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 通知用戶端的專案檔案或目錄所做的變更。  
  
## <a name="related-sections"></a>相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 提供的專案概觀，做為基本建置組塊的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 說明如何專案控制建立和編譯程式碼的其他主題會提供連結。