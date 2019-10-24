---
title: 其他檔案專案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c46126507ef9bb293bd0fa6771f53343ad6206f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726684"
---
# <a name="miscellaneous-files-project"></a>其他檔案專案
當使用者開啟專案專案時，IDE 會將任何不是方案中任何專案成員的專案指派給其他檔案專案。

 當使用者開啟專案專案時，專案會扮演重要的角色來決定要使用哪一個編輯器。 專案可以設計成使用專案特定編輯器或標準編輯器來開啟特定檔案。

 專案特定的編輯器通常會要求使用者必須具備特殊知識，或使用專案的特殊介面。 如需詳細資訊，請參閱[如何：開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)。

 標準編輯器可以在任何專案中開啟特定副檔名的任何檔案。 使用者可以為專案自訂一些標準編輯器（例如 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 文字編輯器），但仍保留其公用字元。 標準編輯器是使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法建立的。

 如果方案中沒有任何專案回應可以開啟專案專案，IDE 會提供一個稱為 [其他檔案] 專案的特殊專案，以開啟任何檔案。

 這個特殊專案提供在專案內容之外開啟檔案的程式。 在處理 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> 方法期間，其他檔案專案一律會以非常低的優先順序回應。 因此，[其他檔案] 專案一律會對可開啟檔案的任何較高優先順序專案產生。

 [其他檔案] 專案不需要使用者使用 [**新增專案**] 對話方塊來明確建立。 此外，[其他檔案] 專案也不會永久管理專案成員清單。 它會使用選擇性功能來記錄每個使用者最近使用過的檔案清單。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [如何︰開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)
- [如何︰開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)
- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)