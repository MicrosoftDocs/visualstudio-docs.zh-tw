---
title: 其他檔案專案 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bdcbe1901deb472969c993b826660d03d12b2cf3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488758"
---
# <a name="miscellaneous-files-project"></a>其他檔案專案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[其他檔案專案](https://docs.microsoft.com/visualstudio/extensibility/internals/miscellaneous-files-project)。  
  
當使用者開啟專案項目時，IDE 會指派給其他檔案專案不是成員的方案中的任何專案的任何項目。  
  
 專案會扮演重要的角色，在決定當使用者開啟的專案項目，使用哪一個編輯器。 在設計專案時，可能使用的專案特定的編輯器或標準編輯器開啟特定檔案。  
  
 專案特定編輯器通常會需要使用者具有專業知識，或使用特殊的介面，從專案。 如需詳細資訊，請參閱 <<c0> [ 如何： 開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)。  
  
 標準編輯器可以開啟任何專案中的特定延伸模組的任何檔案。 使用者可以自訂某些標準的編輯器，例如[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]文字編輯器 中的，針對專案，但仍會保留其公用的字元。 標準編輯器藉由使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法。  
  
 如果方案中的沒有專案回應，它可以開啟專案項目，則 IDE 會提供名為其他檔案專案開啟任何檔案的特殊專案。  
  
 這個特殊的專案提供的內容以外的專案檔案的開頭。 在處理期間<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>方法，其他檔案專案一律會回應以非常低優先順序。 因此，其他檔案專案一律會產生任何可以開啟檔案的較高優先順序專案。  
  
 其他檔案專案不需要明確地建立它與使用者**新的專案** 對話方塊。 此外，其他檔案專案不會永久管理專案成員的清單。 它會使用的選擇性功能，記錄的每一位使用者最近使用過的檔案清單。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [如何： 開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)   
 [如何： 開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)   
 [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)

