---
title: "其他檔案專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0d3fa64b06504d8982594945f5b0c38956676b4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="miscellaneous-files-project"></a>其他檔案專案
當使用者開啟專案項目時，IDE 會指派給其他檔案專案不是成員的方案中的任何專案的任何項目。  
  
 專案扮演著重要的角色，決定當使用者開啟的專案項目使用的編輯器。 專案可以設計成使用特定專案編輯器或標準編輯器開啟特定檔案。  
  
 在專案特定編輯器通常會需要使用者具有特殊的知識，或使用 從專案的特殊介面。 如需詳細資訊，請參閱[如何： 開啟專案的特定編輯器](../../extensibility/how-to-open-project-specific-editors.md)。  
  
 標準編輯器可以開啟任何專案中的任何特定副檔名的檔案。 使用者可以自訂某些標準的編輯器，例如[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]文字編輯器 中的，專案，但仍會保留其公用的字元。 使用標準編輯器所建立<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法。  
  
 如果方案中的沒有專案回應，它可以開啟專案項目，IDE 會提供特殊的專案呼叫其他檔案專案開啟的任何檔案。  
  
 這個特殊的專案提供的檔案出現在專案內容之外開啟的。 在處理期間<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>方法時，其他檔案專案一律會回應以非常低優先順序。 因此，其他檔案專案一律會產生任何可以開啟檔案的較高優先權專案。  
  
 其他檔案專案不需要使用者明確建立其與**新專案** 對話方塊。 此外，其他檔案專案不會永久管理專案成員的清單。 它會使用的選擇性功能，記錄的每個使用者最近使用過的檔案清單。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [如何： 開啟專案的特定編輯器](../../extensibility/how-to-open-project-specific-editors.md)   
 [如何： 開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)   
 [加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)